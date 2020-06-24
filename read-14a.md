#### CSS Transformation
* a new way to position and alter elements.
* *transform property* has two different settings, two-dimensional and three-dimensional. Each of these come with their own individual properties and values.

##### transform syntax:

* transformation property is quite simple, including the transform property followed by the value. The value specifies the transform type followed by a specific amount inside parentheses.

```
div {
  -webkit-transform: scale(1.5);
     -moz-transform: scale(1.5);
       -o-transform: scale(1.5);
          transform: scale(1.5);
}

```
##### 2D transformation:
* Two-dimensional transforms work on the x and y axes, known as horizontal and vertical axes.
###### 2d rotate
* The rotate value provides the ability to rotate an element from 0 to 360 degrees
* The rotate value provides the ability to rotate an element from 0 to 360 degrees
* The default point of rotation is the center of the element, 50% 50%, both horizontally and vertically
```
.box-1 {
  transform: rotate(20deg);
}
.box-2 {
  transform: rotate(-55deg);
}

```
###### 2d scale:
* Using the scale value within the transform property allows you to change the appeared size of an element. 
* The default scale value is 1
* any value between .99 and .01 makes an element appear smaller
* any value greater than or equal to 1.01 makes an element appear larger.
```
.box-1 {
  transform: scale(.75);
}
.box-2 {
  transform: scale(1.25);
}

```
* It is possible to scale only the height or width of an element using the scaleX and scaleY values.
* The scaleX value will scale the width of an element while the scaleY value will scale the height of an element.
* To scale both the height and width of an element but at different sizes, the x and y axis values may be set simultaneously
*  To do so, use the scale transform declaring the x axis value first, followed by a comma, and then the y axis value.
```
.box-1 {
  transform: scaleX(.5);
}
.box-2 {
  transform: scaleY(1.15);
}
.box-3 {
  transform: scale(.5, 1.15);
}

```
###### 2D traslate:
* The translate value works a bit like that of relative positioning, pushing and pulling an element in different directions without interrupting the normal flow of the document.
* Using the translateX value will change the position of an element on the horizontal axis
* using the translateY value will change the position of an element on the vertical axis.
* As with the scale value, to set both the x and y axis values at once.
* se the translate value and declare the x axis value first, followed by a comma, and then the y axis value.
* the distance values used within the translate value may be any general length measurement
* Positive values will push an element down and to the right of its default position
* negative values will pull an element up and to the left of its default position.
```
.box-1 {
  transform: translateX(-10px);
}
.box-2 {
  transform: translateY(25%);
}
.box-3 {
  transform: translate(-10px, 25%);
}

```
###### 2D skew:
* skew is used to distort elements on the horizontal axis, vertical axis, or both. 
* Using the skewX value distorts an element on the horizontal axis while the skewY value distorts an element on the vertical axis.
* To distort an element on both axes the skew value is used, declaring the x axis value first, followed by a comma, and then the y axis value.%p
* The distance calculation of the skew value is measured in units of degrees
* Length measurements, such as pixels or percentages, do not apply here.
```
.box-1 {
  transform: skewX(5deg);
}
.box-2 {
  transform: skewY(-20deg);
}
.box-3 {
  transform: skew(5deg, -20deg);
}

```
##### combining transforms:
* To combine transforms, list the transform values within the transform property one after the other without the use of commas.
* Using multiple transform declarations will not work, as each declaration will overwrite the one above it.
```
.box-1 {
  transform: rotate(25deg) scale(.75);
}
.box-2 {
  transform: skew(10deg, 20deg) translateX(20px);
}

```
##### transform origin:
* the default transform origin is the dead center of an element, both 50% horizontally and 50% vertically
* To change this default origin position the transform-origin property may be used.
* The transform-origin property can accept one or two values
*  When only one value is specified, that value is used for both the horizontal and vertical axes.
* If two values are specified, the first is used for the horizontal axis and the second is used for the vertical axis.
* Individually the values are treated like that of a background image position, using either a length or keyword value.
* That said, 0 0 is the same value as top left, and 100% 100% is the same value as bottom right.
* More specific values can also be set, for example 20px 50px would set the origin to 20 pixels across and 50 pixels down the element.
```
.box-1 {
  transform: rotate(15deg);
  transform-origin: 0 0;
}
.box-2 {
  transform: scale(.5);
  transform-origin: 100% 100%;
}
.box-3 {
  transform: skewX(20deg);
  transform-origin: top left;
}
.box-4 {
  transform: scale(.75) translate(-10px, -10px);
  transform-origin: 20px 50px;
```
##### perpective:
* In order for three-dimensional transforms to work the elements need a perspective from which to transform.
* The perspective for each element can be thought of as a vanishing point
way of setting:
** One way includes using the perspective value within the transform property on individual elements
** another includes using the perspective property on the parent element residing over child elements being transformed.
* Using the perspective value within the transform property works great for transforming one element from a single, unique perspective
* . When you want to transform a group of elements all with the same perspective, or vanishing point, apply the perspective property to their parent element.
```
.box {
  transform: perspective(200px) rotateX(45deg);
}

```
###### perspective depth value
* The perspective value can be set as none or a length measurement.
* The none value turns off any perspective, while the length value will set the depth of the perspective.
* The higher the value, the further away the perspective appears, thus creating a fairly low intensity perspective and a small three-dimensional change.
* The lower the value the closer the perspective appears, thus creating a high intensity perspective and a large three-dimensional change.
```
ox-1 {
  transform: perspective(100px) rotateX(45deg);
}
.box-2 {
  transform: perspective(1000px) rotateX(45deg);
}

```
##### perpective origin:
* The same values used for the transform-origin property may also be used with the perspective-origin property, and maintain the same relationship to the element.
* the origin of a transform determines the coordinates used to calculate the change of a transform, while the origin of a perspective identifies the coordinates of the vanishing point of a transform.
```
.original {
  perspective: 200px;
}
.box {
  transform: rotateX(45deg);
}
.original-1 {
  perspective-origin: 0 0;
}
.original-2 {
  perspective-origin: 75% 75%;
}
.original-3 {
  perspective-origin: 20px 40px;
}

```







































