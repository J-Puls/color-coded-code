# color-coded-code
## What is it?
A script that parses a string containing pre-formatted code, returning a syntactically highlighted HTML string.

## What's its purpose?
Adding lightweight, dynamic syntax highlighting capabilities to any Node based JavaScript project, without relying on external style sheets. This allows on-the-fly customization of styles (when switching between light/dark modes for instance) without hacky HTML link tag toggling.

## What languages does it support?
Currenly, the parser only understands HTML/JSX.

## Usage
The module exports a single function, `colorCode`, which accepts 4 arguments.
  * `str` - the pre-formatted string of code to be parsed
  * `theme` - An object defining colors for different parts of the syntax. This can be any valid CSS color string (hex, rgb, hsl, etc...)
    - tag: the opening and closng tags (ex. <code><b><div</b>><<b>div</b>></code>)
    - attr: attribute keywords (ex <code><div <b>myAttribute</b>></code>)
    - vrbl: JSX variable attribute values (ex <code><div someProp=<b>{myVariable}</b>></div></code>)
    - str: string based attribute values (ex <code><div myAttribute=<b>"some value"</b>></div></code>)
  * `lang` - the language to be parsed _(currently only "html" is supported)_
  * `asReactElement` - boolean value; if `true`, the parsed code will be returned as a set of React elements ready to inject into a component
  
  ## Example
  ```javascript
  import {colorCode} from "color-coded-code";
  
  const myCode = `<button style="color: red;">Click Me!</button>`;
  const myTheme = {
    tag: "hsl(0, 100%, 50%)",
    attr: "hsl(100, 100%, 50%)",
    vrbl: "hsl(200, 100%, 50%)",
    str: "hsl(300, 100%, 50%)",
  }
  const myParsedCode = colorCode(myCode, myTheme, "html", false);
  console.log(myParsedCode);
  
  
  /* RETURNS:
  
"< <span style="color: hsl(0, 100%, 50%)">button</span> <span style="color: hsl(100, 100%, 50%)">style=<span style="color: hsl(300, 100%, 50%)">"color: red;"</span></span>>Click Me!<<span style="color: hsl(0, 100%, 50%)">/button</span>>"
  
  */
  ```
 ```

 ```
