# Flexbox
## Flex Container
```css
.flex-container{
	display:flex;
}
```
block level container
inline level container
```css 
.flex-container{
	display: inline-flex;
}
```


## Flex Items
default left-right

## Main Axis
main start beginning of container
main end opposing side
main size length of main
## Cross Axis
perpendicular to main axis
1. cross start
2. cross end
3. cross size

## Flex Direction
```css
.flex-container{
	display: inline-flex;
	flex-direction: row;
}
```
Row is the default direction
Row Reverse will change the defualt direction
```css
.flex-container{
	display: inline-flex;
	flex-direction: row-reverse;
```
Column sets the content in a colum
```css
.flex-container{
	display: inline-flex;
	flex-direction: column;
```
to reverse the direction use colum-reverse
## Flex Wrap
like text-wrap
wrap reverse flow from bottom to top
## Flex Flow

## Order
```css
.flex-item-02{
	order: 1;
}
```
Moves the item to the end
![[Pasted image 20230830164633.png]]
Ordinal groups with order
negative one creates a group before hand
## Flex Grow
![[Pasted image 20230830165743.png]]
## Flex Shrink
![[Pasted image 20230830165850.png]]
## Justify content
main axis
## Align Items
cross axis
## Align self
1. flex-start
2. flex-end
3. stretch
## gap
gutters

## holy grail FLEX
![[Pasted image 20230830171341.png]]
