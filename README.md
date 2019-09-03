# ng4-click-outside

[![NPM](https://nodei.co/npm/@jmcrommen/ng4-click-outside.png?compact=true)](https://nodei.co/npm/ng4-click-outside/)

*forked from chippdnyc/ng-click-outside*

*add include and includeBeforeClick property* 

Angular 2+ directive for handling click events outside an element. Useful for things like reacting to clicking
outside of a dropdown menu or modal dialog.

**NOW WORKS WITH ANGULAR UNIVERSAL**

Like binding to a regular `click` event in a template, you can do something like this:

```HTML
<div (clickOutside)="onClickedOutside($event)">My element</div>
```


## Installation

```shell
npm install --save @jmcrommen/ng4-click-outside
```


## Usage

Add `ClickOutsideModule` to your list of module imports:

```typescript
import { ClickOutsideModule } from 'ng4-click-outside';

@NgModule({
  declarations: [AppComponent],
  imports: [BrowserModule, ClickOutsideModule],
  bootstrap: [AppComponent]
})
class AppModule {}
```

You can then use the directive in your templates:

```typescript
@Component({
  selector: 'app',
  template: `
    <div (clickOutside)="onClickedOutside($event)">Click outside this</div>
  `
})
export class AppComponent {
  onClickedOutside(e: Event) {
    console.log('Clicked outside:', e);
  }
}
```

### Options

| Property name | Type | Default | Description |
| ------------- | ---- | ------- | ----------- |
| `attachOutsideOnClick` | boolean | `false` | By default, the outside click event handler is automatically attached. Explicitely setting this to `true` sets the handler after the element is clicked. The outside click event handler will then be removed after a click outside has occurred. |
| `delayClickOutsideInit` | boolean | `false` | Delays the initialization of the click outside handler. This may help for items that are conditionally shown ([see issue #13](https://github.com/arkon/ng-click-outside/issues/13)). |
| `clickOutsideEvents` | string | `'click'` | Allows for a space-separated list of events to cause the trigger. For example, for additional mobile support: `[clickOutsideEvents]="'click touchstart'"`. |
| `exclude` | string | | A comma-separated string of DOM element queries to exclude when clicking outside of the element. For example: `[exclude]="'button,.btn-primary'"`. |
| `excludeBeforeClick` | boolean | `false` | By default, `clickOutside` registers excluded DOM elements on init. This property refreshes the list before the `clickOutside` event is triggered. This is useful for ensuring that excluded elements added to the DOM after init are excluded (e.g. ng2-bootstrap popover: this allows for clicking inside the `.popover-content` area if specified in `exclude`). |
| `include` | string | | A comma-separated string of DOM element queries to include when clicking outside of the element. For example: `[include]="'button,.overlayPanel'"`. |
| `includeBeforeClick` | boolean | `false` | By default, `clickOutside` registers included DOM elements on init. This property refreshes the list before the `clickOutside` event is triggered. This is useful for ensuring that included elements added to the DOM after init are included (e.g. ng2-bootstrap popover: this allows for clicking inside the `.popover-content` area if specified in `include`). |
