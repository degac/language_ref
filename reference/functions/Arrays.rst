======
Arrays
======
Arrays are used to store sequences of variables, or %elements. An element within an array is accessed by %indexing the array with an integer offset.
The general syntax for indexing an array is:
{
%ArrayExpression **[** %index1 **,** %index2 etc... @]
**
 
Creating Arrays
===============
The most common way to create an array is when declaring a variable:
 
.. code-block:: blitzmax
	 
	Local int_array[10]
 
This will initialize the int_array variable with a 10 element array. You can declare an 'empty' array by using []:
 
.. code-block:: blitzmax
	 
	Local int_array[]
 
An empty array is identical to an array with 0 elements.
Arrays may also be created 'on the fly' using the syntax:
{
**New** **[** %Dimension1 **,** %Dimension2 etc... @]
**
This returns an array of the specified dimension(s) with each element initialized to #Null. For example:
 
.. code-block:: blitzmax
	 
	Local int_array:Int[]
	int_array=New Int[10]
 
'Auto arrays' may be created using the syntax:
{
**[** %Element1 **,** %Element2 etc... @]
**
This returns a 1 dimensional array containing the specified elements, for example:
 
.. code-block:: blitzmax
	 
	Local int_array[]=[1,2,3,4,5]
 
Each element of an auto array must have exactly the same type. If necessary, you can use type conversions to enforce this.
Arrays also provide the following methods:
[ **Method** | @Description
* Sort( ascending=True ) | Sort the array.
* Dimensions:Int[]() | Get array dimensions.
]
Arrays also provide a read-only **length** field that returns the total number of elements in the array.
Here are some examples of using array methods:
 
.. code-block:: blitzmax
	 
	Strict
	Local arr:String[]=["some","random","strings","in","a","string","array"]
	arr.Sort        'sort ascending
	Print "Array in ascending order..."
	For Local t:String=EachIn arr
	        Print t
	Next
	arr.Sort False  'sort descending
	Print "Array in descending order..."
	For Local t:String=EachIn arr
	        Print t
	Next
	Local arr2[10,20,30,40]
	'Dump array dimensions
	For Local i=EachIn arr2.Dimensions()
		Print i
	Next
 
