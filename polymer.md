---
layout: default
title: Polymer core
---

The {{site.project_title}} _core_ provides a thin layer of code that expresses
its opinion and provides the extra sugaring that all {{site.project_title}} elements use. It is provided in the file `polymer.js`.

**Note:** You can find working examples of the concepts on this page in [/toolkit-ui](https://github.com/polymer/toolkit-ui), [/polymer-elements](https://github.com/Polymer/polymer-elements), and [/polymer-ui-elements](https://github.com/Polymer/polymer-ui-elements).
{: .alert .alert-success }

## Element declaration

At the heart of {{site.project_title}} are Custom Elements. Thus, it should be no surprise that defining a {{site.project_title}} element is similar to the way you define a standard Custom Element. The major difference is that {{site.project_title}} elements are created using `<polymer-element>`, not `<element>`.

To register and supercharge `<tag-name>` as a {{site.project_title}} element, use `<polymer-element>` to create its definition:

    <polymer-element name="tag-name">
      <template>
        <!-- shadow DOM here -->
      </template>
    </polymer-element>

If you need to set methods or properties on the element's `prototype`, use `{{site.project_title}}()`.
Its first argument is the name of the element you're creating. The second argument (optional) is an object that defines your element's `prototype`. In the following example the registration call defines a property `message` and the `ready` callback: 

    <polymer-element name="tag-name">
      <template>
        <!-- shadow DOM here -->
      </template>
      <script>
        {{site.project_title}}('tag-name', {
          message: "Hello!",
          ready: function() {
            // Component is ready. Use it.
          }
        });
      </script>
    </polymer-element>

### Element lifecycle methods {#lifecyclemethods}

{{site.project_title}} has first class support for the Custom Element lifecycle
callbacks, though implements them with shorter names for convenience.

Allow the lifecycle callbacks are optional: 

    {{site.project_title}}('tag-name', {
      ready: function() { ... },
      inserted: function () { ... },
      removed: function() { ... },
      attributeChanged: function(attrName, oldVal, newVal) {
        //var newVal = this.getAttribute(attrName);
        console.log(attrName, 'old: ' + oldVal, 'new:', newVal);
      },
    });

Below is a table with the names of lifecycle method according to the Custom Elements
[specificationn](https://dvcs.w3.org/hg/webcomponents/raw-file/tip/spec/custom/index.html#custom-element-lifecycle) vs. the names {{site.project_title}} uses.

Spec | {{site.project_title}} | Called when
|-
readyCallback | ready | an instance of the element is created
insertedCallback | inserted | an instance was inserted into the document
removedCallback | removed | an instance was removed from the document
attributeChangedCallback | attributeChanged | an attribute was added, removed, or updated
{: .table }

### The WebComponentsReady event {#WebComponentsReady}

The polyfill(s) parse element definitions and handle their upgrade _asynchronously_. If you try to fetch the element from the DOM before things have settled, you'll get a big fat `null`. In these situations, an including page should wait for the `WebComponentsReady` event
before working with the node.

Example:

    <head>
      <link rel="import" href="path/to/x-foo.html">
    </head>
    <body style="opacity:0">
      <x-foo></x-foo>
      <script>
        window.addEventListener('WebComponentsReady', function() {
          document.body.style.opacity = 1; // show body now that registration is done.

          var xFoo = document.querySelector('x-foo');
          // Do something with x-foo.
        });
      </script>
    </body>

**Tip:** Use the `WebComponentsReady` event to mitigate FOUC in browsers that don't
support the CSS `:unknown` pseudo class.
{: .alert .alert-success }

## {{site.project_title}} Features {#features}

### Published properties

When you _publish_ a property name, you're making that property two-way data-bound and part
of the element's "public API". Published properties can be initialized by an HTML attribute
of the same name. 

There are two ways to publish properties:

1. **Preferred** - Include its name in the `<polymer-element>`'s `attributes` attribute.
1. Include the name in a `publish` object on your prototype.

As an example, here's an element that publishes three public properties, `foo`, `bar`, and `baz`:

    <polymer-element name="x-foo" attributes="foo bar baz">
      <script> 
        Polymer('x-foo');
      </script>
    </polymer-element>

#### Default property values

By default, properties defined in `attributes` are `null`:

    <polymer-element name="x-foo" attributes="foo">
      <script> 
        Polymer('x-foo'); // x-foo has a foo property with null value.
      </script>
    </polymer-element>

As such, you can provide default values using the `prototype`:

    <polymer-element name="x-foo" attributes="foo">
      <script> 
        Polymer('x-foo', { // x-foo has a foo property with default value false.
          foo: false
        });
      </script>
    </polymer-element>

    <!-- Same, but using the alternate "publish" object. -->
    <polymer-element name="x-foo">
      <script> 
        Polymer('x-foo', {
          publish: {
            foo: false 
          }
        });
      </script>
    </polymer-element>

#### Configuring an element via attributes

Attributes are a great way for users of your element to configure it, declaratively.
They can customize a published property by passing an initial value on the attribute
with the same name:

    <x-foo foo="true"></x-foo>

**Note:** As of today, property values are not reflected back into markup. Also, setting
an attribute using `.setAttribute()`) has no effect.
{: .alert }

##### Hinting an attribute's type

When attribute values are converted to property values, {{site.project_title}} attempts to convert the value to the correct type, depending on the default value of the property.

    <polymer-element name="x-foo" attributes="foo">
      <script> 
        Polymer('x-foo', {
          foo: false // hint that foo is Boolean
        });
      </script>
    </polymer-element>

### Data binding and custom attributes

Published properties are data-bound inside of {{site.project_title}} elements and accessible
via MDV's `{%raw%}{{}}{%endraw%}`. These bindings are by reference and are two-way.

For example, we can define a `name-tag` element that publishes two properties,
`name` and `nameColor`.

    <polymer-element name="name-tag" attributes="name nameColor">
      <template>
        Hello! My name is <span style="color:{{"{{nameColor"}}}}">{{"{{name"}}}}</span>
      </template>
      <script>
        {{site.project_title}}('name-tag', {
          nameColor: "orange"
        });
      </script>
    </polymer-element>

In this example, `name` has initial value of `null` and `nameColor` has a value of "orange".
Thus, the `<span>`'s color will be orange.

#### Binding objects to attribute values

Generally, attributes are string values, but {{site.project_title}} makes it possible to bind references between elements using attributes. The binding engine interprets reference bindings
by interrogating the [attribute's type](#hinting-an-attributes-type). This means you 
can bind an an object to an HTML attribute!

Let's modify the `name-tag` example to take an object instead of individual properties.

    <polymer-element name="name-tag" attributes="person">
      <template>
        Hello! My name is <span style="color:{{"{{person.nameColor"}}}}">{{"{{person.name"}}}}</span>
      </template>
      <script>
        {{site.project_title}}('name-tag', {
          ready: function() {
            this.person = {
              name: "Scott",
              nameColor: "orange"
            }
          }
        });
      </script>
    </polymer-element>

Now, imagine we make a new component called `<visitor-creds>` that uses `name-tag`:

    <polymer-element name="visitor-creds">
      <template>
        <name-tag person="{{"{{person"}}}}"></name-tag>
      </template>
      <script>
        {{site.project_title}}('visitor-creds', {
          ready: function() {
            this.person = {
              name: "Scott2",
              nameColor: "red"
            }
          }
        });
      </script>
    </polymer-element>

When an instance of `<visitor-creds>` is created, its `person` property (an object)
is also bound to `<name-tag>`'s `person` property. Now both components are using
the same `person` object.

**Important:** Be careful when your properties are objects or arrays. Element registration
is evaluated once. This means only one instance of an object used in property initialization is ever created. Because of the nature of `prototype`, you may run into unexpected "shared state" across different instances of the same element if you're setting an initial value for a property which is an object or array. Do this type of initialization in `ready()` rather than directly on the `prototype`. 
{: .alert .alert-error }

### Declarative event mapping

{{site.project_title}} supports declarative binding of events to methods in the component.
It uses special <code>on-<em>event</em></code> syntax to trigger this binding behavior.

    <polymer-element name="g-cool" on-keypress="keypress">
      <template>
        <button on-click="buttonClick"></button>
      </template>
      <script>
        {{site.project_title}}('g-cool', {
          keypress: function(event) { ...},
          buttonClick: function(event) { ... }
        });
      </script>
    </polymer-element>

In this example, the `on-keypress` declaration maps the standard DOM `"keypress"` event to the `keypress` method in the component. Within the component template, the `on-click` declaration maps a custom `buttonClick` event to the `buttonClick` method in the component. This is achieved again without the need for any glue code. 

Some things to notice:

* The value of an event handler attribute is the string name of a method on the component. Unlike traditional syntax, you cannot put executable code in the attribute.
* The event handler is passed the following arguments:
  * `inEvent` is the [standard event object](http://www.w3.org/TR/DOM-Level-3-Events/#interface-Event).
  * `inDetail`: A convenience form of `inEvent.detail`.
  * `inSender`: A reference to the node that declared the handler. This is often different from `inEvent.target` (the lowest node that received the event) and `inEvent.currentTarget` (the component processing the event), so  {{site.project_title}} provides it directly.

## Advanced sugaring

In addition to the above features, which are focused around making the core functionality of components simple and easy to use, {{site.project_title}} provides syntactical sugar that makes more advanced component features easy to create.

### Change watchers {#change-watchers}

All properties on {{site.project_title}} elements can be watched for changes by implementing a <code><em>propertyName</em>Changed</code> handler. When the value of a watched property changes, the appropriate change handler is automatically invoked. 

    <polymer-element name="g-cool" attributes="better best">
      <script>
        {{site.project_title}}('g-cool', {
          plain: '',
          best: '',
          betterChanged: function(inOldValue) {
          },
          bestChanged: function(inOldValue) {
          }
        });
      </script>
    </polymer-element>

In this example, there are two watched properties, `better` and `best`. The `betterChanged` and `bestChanged` function will be called whenever `better` or `best` are modified, respectively. 

### Automatic node finding

Another useful feature of {{site.project_title}} is node reference marshalling. Every node in a component's shadow DOM that is tagged with an `id` attribute is automatically referenced in the component's `this.$` hash. 

For example, the following defines a component whose template contains an `<input>` element whose `id` attribute is `nameInput`. The component can refer to that element with the expression `this.$.nameInput`.

    <polymer-element name="x-form">
      <template>
        <input type="text" id="nameInput">
      </template>
      <script>
        {{site.project_title}}('x-form', {
          logNameValue: function() {
            console.log(this.$.nameInput.value);
          }
        });
      </script>
    </polymer-element>

### Extending other elements

A {{site.project_title}} element can extend another element by using the `extends`
attribute. The parent's properties and methods are inherited by the child element,
data-bound, and accessible via MDV.

    <polymer-element name="polymer-cool">
      <!-- UI-less element -->
      <script>
        {{site.project_title}}('polymer-cool', {
          praise: 'cool'
        });
      </script>
    </polymer-element>

    <polymer-element name="polymer-cooler" extends="polymer-cool">
      <template>
        {%raw%}{{praise}}{%endraw%} <!-- "cool" -->
      </template>
      <script>
        {{site.project_title}}('polymer-cooler');
      </script>
    </polymer-element>

#### Overriding a parent's methods

When you override an inherited method, you can call the parent's method with `this.super()`.

    <polymer-element name="polymer-cool">
      <script>
        {{site.project_title}}('polymer-cool', {
          praise: 'cool',
          makeCoolest: function() {
            this.praise = 'coolest';
          }
        });
      </script>
    </polymer-element>

    <polymer-element name="polymer-cooler" extends="polymer-cool" on-click="makeCoolest">
      <template>polymer-cooler is {%raw%}{{praise}}{%endraw%}</template>
      <script>
        {{site.project_title}}('polymer-cooler', {
          praise: 'cooler',
          makeCoolest: function() {
            this.super(); // calls polymer-cool's makeCoolest()
          }
        });
      </script>
    </polymer-element>

    <polymer-cooler></polymer-cooler>

In this example, when the user clicks on a `<polymer-cooler>` element, its
`makeCoolest()` method is called, which in turn calls the parent's version
using `this.super()`. The `praise` property (inherited from `<polymer-cool>`) is set
to "coolest".

## Additional utilities

Source: [base.js](https://github.com/Polymer/polymer/blob/stable/src/base.js)

- [`asyncMethod()`](#asyncmethod)
- [`fire()` / `asyncFire()`](#fire)

### Dealing with asynchronous tasks {#asyncmethod}

Many things in {{site.project_title}} happen asynchronously. Changes are gathered up
and executed all at once, instead of executing right away. Batching
changes creates an optimization that (a) prevents duplicated work and (b) reduces unwanted [FOUC](http://en.wikipedia.org/wiki/Flash_of_unstyled_content).

[Change watchers](#change-watchers) and situations that rely on MDV data-bindings
are examples that fit under this async behavior. For example, [conditional templates](/platform/mdv.html#where-to-go-from-here) may not immediately render after setting properties because changes to those renderings are saved up and performed all at once after you return from JavaScript.

To do work after changes have been processed, {{site.project_title}} provides `asyncMethod()`.
It's similar to `window.setTimeout()`, but automatically binds `this` to the correct value:

    // asyncMethod(inMethod, inArgs, inTimeout)
    this.asyncMethod(function() {
      this.foo = 3;
    }, null, 1000);

    // Roughly equivalent to:
    //setTimeout(function() {
    //  this.foo = 3;
    //}.bind(this), 1000);

The second argument to `asyncMethod()`, `inArgs`, is an optional object or array of arguments to
pass to the callback.

In the case of property changes that result in DOM modifications, follow this pattern:

    Polymer('my-element', {
      propChanged: function() {
        // If "prop" changing results in our DOM changing, schedule an update after
        // the new microtask.
        this.asyncMethod(this.updateValues);
      },
      updateValues: function() {...}
    });

### Firing custom events {#fire}

{{site.project_title}} core provides a convenient `fire()` method for
sending custom events. Essentially, it's a wrapper around your standard `node.dispatchEvent(new CustomEvent(...))`. In cases where you need to fire an event after microtasks have completed,
use the asynchronous version: `asyncFire()`.

Example:

    <polymer-element name="ouch-button">
      <template>
        <button on-click="onClick">Send hurt</button> 
      </template>
      <script>
        Polymer('ouch-button', {
          onClick: function() {
            this.fire('ouch', {msg: 'That hurt!'}); // fire(inType, inDetail, inToNode)
          }
        });
      </script>
    </polymer-element>

    <ouch-button></ouch-button>

    <script>
      document.querySelector('ouch-button').addEventListener('ouch', function(e) {
        console.log(e.type, e.detail.msg); // "ouch" "That hurt!"
      });
    </script>

**Tip:** If your element is within another {{site.project_title}} element, you can
use the special [`on-* handlers`](declarative-event-mapping) to deal with the event: `<ouch-button on-ouch="myMethod"></ouch-button>`
{: .alert .alert-success }
