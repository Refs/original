# original



## Copying Arrays (deep and shallow)

```js
/* Copying Arrays */ 

var original = [true, true, undifined, false, null];

// slice
var copy1 = original.slice(0);

// spread operator
var copy2 = [...original];

// Deep copying
// if you have an array or an object within you array the above copy method won't work; 
// whenever you have an array or an object in your array , you need to do deep copying 
var deepArray = [['freeCodeCamp']];

// anytime you have an array within an array in javascript or if you have an object within an array in javascript , in the original array is just a poninter to an array or or a pointer to an object inside that original array. So when we are doing a copy of the array we're just copying the pointers to the ['freeCodeCamp']
var shallowCopy = deepArray.slice(0);

// So when we push 'is greate' , we're not pushing 'is great' to the shallow copy directly , we're pushing 'is great' to the pointer to the other array . Since both them are pointing the same array . it's going to add the 'is great ' to basically both copies. 

shallowCopy[0].push("is great");

console.log(deepArray[0], shallowCopy[0])
// ["freeCodeCamp"， "is great"] ["freeCodeCamp"， "is great"]

// If you have an array that has other arrays or other objects within the array you really need to a deep copy if you want to make sure everything is copied as you would expect 

// JSON.stringify(deepArray) to create a string of the whole array including the array within the array and objects within the array ;
// JSON.parse() which is going to convert this string back into a javascript object or a javascript array 

var deepCopy = JSON.parse(JSON.stringify(deepArray));
deepCopy[0].push('is great');

console.log(deepArray[0], deepCopy[0])
// ["freeCodeCamp"] ["freeCodeCamp"， "is great"]

```

## deep copy (clone) object

```js
/* clone.js v1.0.1
 * https://github.com/AngelAngelov/deepCopy
 * Small function to deep copy an object in pure javascript
 */

  var clone = function(obj){
    var clonedObject;

    //Handle null, undefined or primitive types
    if (obj === null || typeof obj !== 'object') {
        return obj;
    }

    //Handle Array
    if(obj instanceof Array){
        clonedObject = [];

        for(var i = 0; i < obj.length; i++){
            //clone every element in the array
            clonedObject[i] = clone(obj[i]);
        }

        return clonedObject;
    }

    //Handle Date
    if(obj instanceof Date) {
        clonedObject = new Date(obj.valueOf());
        return clonedObject;
    }

    //Handle RegExp
    if(obj instanceof RegExp) {
        clonedObject=RegExp(obj.source,obj.flags);
        return clonedObject;
    }

    //Handle Object
    if(obj instanceof Object) {
        clonedObject = new obj.constructor();

        //iterate object properties
        for(var attr in obj){
            if(obj.hasOwnProperty(attr)){
                //clone every propery to the new object
                clonedObject[attr] = clone(obj[attr]);
            }
        }

        return clonedObject;
    }

    //If you hit this code something in VERY Wrong :)
    throw new Error('Object not cloned');
  }

  

```