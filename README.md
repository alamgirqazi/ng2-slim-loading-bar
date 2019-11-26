# a fork of [ng2-al-slim-loading-bar](https://www.npmjs.com/package/ng2-slim-loading-bar) that works with Angular 7,8,9+

Angular component that shows slim loading bar at the top of the page of your application.

## Installation

```sh
npm install ng2-al-slim-bar
```
## Demo

[https://angular-wytxgs.stackblitz.io](https://angular-wytxgs.stackblitz.io)
 
## Usage

#### 1. Update the markup

- Import the `style.css` file into your web page
- Add `<ng2-slim-loading-bar></ng2-slim-loading-bar>` tag in template of your application component.

#### 2. Import the `SlimLoadingBarModule`

Import `SlimLoadingBarModule.forRoot()` in the NgModule of your application.
The `forRoot` method is a convention for modules that provide a singleton service.

```ts
import { BrowserModule } from "@angular/platform-browser";
import { NgModule } from "@angular/core";
import { SlimLoadingBarModule } from "ng2-al-slim-bar";

@NgModule({
  imports: [BrowserModule, SlimLoadingBarModule.forRoot()],
  bootstrap: [AppComponent]
})
export class AppModule {}
```

```ts
@NgModule({
  imports: [BrowserModule, SlimLoadingBarModule.forRoot()],
  exports: [BrowserModule, SlimLoadingBarModule]
})
export class SharedModule {}
```

#### 3. Use the `SlimLoadingBarService` for your application

- Import `SlimLoadingBarService` from `ng2-slim-loading-bar` in your application code:

```js
import {Component} from '@angular/core';
import {SlimLoadingBarService} from 'ng2-al-slim-bar';

@Component({
    selector: 'app',
    template: `
        <div>Hello world</div>
        <button (click)="startLoading()">Start Loading</button>
        <button (click)="stopLoading()">Stop Loading</button>
        <button (click)="completeLoading()">Complete Loading</button>
        <ng2-slim-loading-bar></ng2-slim-loading-bar>
    `
})
export class AppComponent {

    constructor(private slimLoadingBarService: SlimLoadingBarService) { }

    startLoading() {
        this.slimLoadingBarService.start(() => {
            console.log('Loading complete');
        });
    }

    stopLoading() {
        this.slimLoadingBarService.stop();
    }

    completeLoading() {
        this.slimLoadingBarService.complete();
    }
}
```

#### 3. Customize the the `ng2-al-slim-bar` for your application

You can use the following properties to customize the `ng2-slim-loading-bar` component in your template:

- `color` - The color of loading bar. Default is `firebrick`. It can be any CSS compatible value.
- `height` - The height of loading bar. Default value is `2px`.
- `show` - The flag helps hide and show the loading bar. Default value is `true`.

Example:
`<ng2-slim-loading-bar color="blue" height="4px"></ng2-slim-loading-bar>`

#### 4. Manage the loading bar

You can use the following properties to customize the SlimLoadingBar via instance of SlimLoadingBarService:

- `color` - The color of loading bar.
- `height` - The height of loading bar.
- `visible` - The flag helps hide and show the loading bar, false for hidden and true for visible.

You can use the following methods to control the SlimLoadingBar via instance of SlimLoadingBarService:

- `start` - Start the loading progress. Use the callback function as an parameter to listed the complete event.
- `stop` - Stop the loading progress. This method pause the current position of loading progress.
- `reset`- Reset the position of loading progress to 0.
- `complete` - Set the progress to 100% and hide the progress bar.

#### 5. Events handling

You can hook up with our different types of events thrown.

- `SlimLoadingBarEventType.PROGRESS`
- `SlimLoadingBarEventType.HEIGHT`
- `SlimLoadingBarEventType.COLOR`
- `SlimLoadingBarEventType.VISIBLE`

you can subscribe to these events types by simplying doing this

```js
 constructor(private _loadingBar: SlimLoadingBarService) {
    this._loadingBar.events.subscribe((item:SlimLoadingBarEvent) => console.log(item));
   }
```

where item returned is of `SlimLoadingBarEvent {type: SlimLoadingBarEventType, value: any}`

# Credits

Inspired by [ngProgress.js](https://github.com/VictorBjelkholm/ngProgress)

fork of [ng2-slim-loading-bar](https://www.npmjs.com/package/ng2-slim-loading-bar)

# License

[MIT](/LICENSE)
