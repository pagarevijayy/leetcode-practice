**Category**: String Manipulation

**Prob definition**: HTML Elements


Have the function HTMLElements(str) read the str parameter being passed which will be a string of HTML DOM elements and plain text. The elements that will be used are: `b, i, em, div, p`. 

For example: if str is `"<div><b><p>hello world</p></b></div>"` then this string of DOM elements is nested correctly so your program should return the string true.

If a string is not nested correctly, return the first element encountered where, if changed into a different element, would result in a properly formatted string. If the string is not formatted properly, then it will only be one element that needs to be changed. 

For example: if str is `"<div><i>hello</i>world</b>"` then your program should return the string div because if the first `<div>` element were changed into a `<b>`, the string would be properly formatted.

Examples
```
Input: "<div><div><b></b></div></p>"
Output: div
Input: "<div>abc</div><p><em><i>test test test</b></em></p>"
Output: i
```

**Solution**

```
function HTMLElements(str) {
  
  let parsedStack = []; // parsed element's stack
  let currentElm = '';  // current element being traversed

  /* logic: 
  traverse through the string and note down parsed tags i.e.
  push to stack on tag opening and when the tag ends pop it 
  from the stack if it is valid... if it tag is invalid return 
  stack top (i.e the tag that needs a fix.)
  */
  
  for(let i = 0; i < str.length; i++){

    let elm = str[i]; // letter being parsed

    if(elm == '>'){
      if(currentElm[1] == '/'){
        let stackTop = parsedStack[parsedStack.length - 1];

        if(currentElm.slice(2) == stackTop){
          parsedStack.pop();
        } else {
          return stackTop;
        }
      } else {
        parsedStack.push(currentElm.slice(1));
      }

      currentElm = "";
      continue;
    }

    if(elm == '<' || currentElm ){
      currentElm+= elm;
    }

  }

  return true; // properly nested

}
```

**Learnings**

- `null + 'string' = 'nullstring'` null and undefined with string undergo type coercion (converts them to string)
- in such cases use "" (empty strings) for assignment instead of null/undefined
 