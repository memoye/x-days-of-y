# Angular Notes

## Components

Components consists of a few main parts:

1. A `@Component` decorator that contains config used by Angular
2. An **HTML template** that controls what renders into the DOM
3. A **CSS selector** that defines how the component is used in HTML.
4. A **TypeScript** class with behaviors such as handling user input or making server requests (eg api calls).

`@Component` config can contain the following keys amongst others;

- `selector`: a CSS selector that determines how the component is used in HTML eg `selector: 'user-profile'` will be used as `<user-profile />` in other components.
- `template`: (template string) to define the HTML content to render.
- `styles`: (template string) to define the CSS styles.
- `templateUrl`: to use an external HTML file as template eg `templateUrl: 'path/to/user-profile.html'`
- `styleUrl`: to use an external CSS file as template eg `styleUrl: 'path/to/user-profile.css'`
- `imports`: (array) all the imported components that will be used in the current component

### Templates

A **binding** creates a dynamic connection between a component's **tempalte** and its **data**. This ensures that changes to the component's data automatically _updates_ the rendered template.

#### Binding Dynamic Text, Properties and Attributes

- Text Interpolation: Dynamic text can be rendered in templates with double curly braces eg:

  ```js
  template: `<p>Your color preference is {{ theme }}.</p>`;
  ```

  If the value of `theme` changes, the component is updated accordingly

- Dynamic values can bind into object properties and HTML attributes with square brackets. Elements can be bound on an HTML element's DOM instance, a component, or a directive instance.

  ##### Native Element Properties

  Example:

  ```html
  <!-- Bind the `disabled` property on the button element's DOM object -->
  <button [disabled]="isFormValid">Save</button>
  ```

  Whenever 'isFormValid' changes, the disabled property of the HTMLButtonElement instance is set accordingly

  ##### Component and Directive properties

  Example:

  ```html
  <!-- Bind the `value` property on the MyListBox component instance ` -->
  <my-listbox [value]="mySelection" />
  ```

  Everytime mySelection changes, the `value` property of the `MyListbos` instance is set.

  We can also bind to directive properties

  ```html
  <!-- Bind to the `ngSrc` property of the `NgOptimizeImage` directive -->
  ```

  ##### Attributes

  _To be continued..._

### Selectors

Basic CSS selectors can be used to specify how components can be used.
The only supported pseudo-class is `:not()`

Selectors can be _combined_ by concatenating them eg. `button[type="reset"]` for button elements that specify `type="reset"`

We can define multiple selectors with a comma-separated list eg. `drop-zone, [dropzone]`. This way, a component will be created for each element that matches any of the selectors in the list.

#### Choosing a selector`

Use short, consistent selector prefixes for components eg. If building Youtube, we would use something like "yt-" to prefix components

Angular uses the `ng` selector prefix for its own framework APIs. **Never** use `ng` as a selector prefix.

##### When to use an attribute selector

Consider using an attribute selector when creating a component on a standard native element. For example, when creating a custom button component, we can use the standard `<button>` element by using an attribute selector

```ts
@Component({
  selector: "button[yt-upload]",
  // ...
})
export class YoutubeUploadButton {
  /*...*/
}
```
