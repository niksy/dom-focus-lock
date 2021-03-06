# dom-focus-lock
It is a trap! We got your focus and will not let him out!

[![NPM](https://nodei.co/npm/dom-focus-lock.png?downloads=true&stars=true)](https://nodei.co/npm/dom-focus-lock/)

This is a small, but very useful for:
 - Modal dialogs. You can not leave it with "Tab", ie tab-out.
 - Focused tasks. It will aways brings you back.
 
You have to use it in _every_ modal dialog, or you `a11y` will be shitty.
 
# How to use
Just include script
```html
<script src="http://unpkg.com/dom-focus-lock"></script>
```
Or require it from js
```js
 import focusLock from 'dom-focus-lock'
```
Then - activate the lock on desired node
```js
focusLock.on(domNode);
//.....
focusLock.off(domNode);
```

#WHY?
From [MDN Article about accessible dialogs](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_dialog_role):
 - The dialog must be properly labeled
 - Keyboard __focus must be managed__ correctly
 
This one is about managing the focus.

I'v got a good [article about focus management, dialogs and  WAI-ARIA](https://medium.com/@antonkorzunov/its-a-focus-trap-699a04d66fb5).    


# Behavior
 0. It will always keep focus inside Lock.
 1. It will cycle forward then you press Tab.
 2. It will cycle in reverse direction on Shift+Tab.
 3. It will do it using _browser_ tools, not emulation.
 4. It will handle positive tabIndex inside form.
 5. It will prevent any jump outside, returning focus to the last element.

You can use nested Locks or have more than one Lock on the page.
Only `last`, or `deepest` one will work. No fighting.

# API
 FocusLock has only 3 props, 2 of them you will never use(I hope):
  - `disabled`, to disable(enable) behavior without altering the tree.
     
# How it works
 Everything thing is simple - vue-focus-lock just dont left focus left boundaries of component, and
 do something only if escape attempt was succeeded.
 
 It is not altering tabbing behavior at all. We are good citizens.

# Not using a vanilla js?
 try [react-focus-lock](https://github.com/theKashey/react-focus-lock) or [vue-focus-lock](https://github.com/theKashey/vue-focus-lock)

# Licence
 MIT
 
 
