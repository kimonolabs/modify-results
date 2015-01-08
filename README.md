A collection of filter functions.

#Default filters
  - sort
  - replace
  - custom
  - split
  - filter
  - merge
  - remove
  - removeProp
  - toInt 
  - toFloat
  - renameCollection
  - renameProperty 
  - currencyConvert

--------------------------------------------------------------
#Documentation

####.**split**(*option*)

Split one string property into multiple properties according to the separator.

#####Argument
  - option (Object): The configuration of this transform. It should contain following properties:

    - *collection* (String):        The collection being modified. Optional if current collection has been set previously via setCurrentCollection()
    - *property*   (String):        The property whose value is being splited. The value being splited must be a string.
    - *separator*  (String|RegExp): The character, or regular expression, to use for splitting the string.
    - *names*:     (Array[String]): Optional. An array of strings that specifies the names of new properties generated by the split. If not provided, they will be generated automatically by appending 0, 1, 2, ... to the end of *property* specified above.
    
#####Returns
  - The *this* binding of the KimFilter object being applied.
  
#####Example
    
```javascript
var data = {
  "name": "sample_input",
  "results": {
    "collection1": [
      { "ID": "1.", "Karma": "329 points" },
      { "ID": "2.", "Karma": "171 points" },
      { "ID": "3.", "Karma": "145 points" }
    ]
  }
};

new kimFilter(data)
.setCurrentCollection("collection1")
.split({
  property: "Karma",
  separator: " ",
  names: ["Num", "Unit"]
})
.output(function(data) {
  console.log(data);
 });

// will print
// {
//   "name": "function_filters",
//   "results": {
//     "collection1": [
//       { "ID": "1.", "Num": "329", "Unit": "points" },
//       { "ID": "2.", "Num": "171", "Unit": "points" },
//       { "ID": "3.", "Num": "145", "Unit": "points" }
//     ]
//   }
// };
```
