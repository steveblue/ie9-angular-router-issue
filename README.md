# ie9-issue

The project can be built with the `@angular/cli` or `angular-rollup`.

- `npm install`
- `ngr build dev --watch --serve`

- Open IE9 in Windows 7
- Open `http://localhost:4200`
- Observe app loads
- Click the Angular logo or manually route to /lazy in the address bar
- Observe error in console `SCRIPT438: Object doesn't support property or method 'apply' `

If you inspect ZoneTask you will find the `@angular/router` is passing `null` to Zone instead of an Object, throwing the Error.

```
    var ZoneTask = /** @class */ (function () {
        function ZoneTask(type, source, callback, options, scheduleFn, cancelFn) {
            this._zone = null;
            this.runCount = 0;
            this._zoneDelegates = null;
            this._state = 'notScheduled';
            this.type = type;
            this.source = source;
            this.data = options;
            this.scheduleFn = scheduleFn;
            this.cancelFn = cancelFn;
            this.callback = callback;
            var self = this;

```

^^^

`self` is `null` while source is `setTimeout`.




