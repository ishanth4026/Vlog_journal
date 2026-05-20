- We can identify a composable object/component when it has @component before it is created
- We use modifiers to apply things like size, position, font style etc to all components

# Layouts
- Columns - It will display everything vertically one after the other
- Rows - it will display everything horizontally
- Box - It is used to display the components however we want (eg: top middle, centre end etc)

# Lists
- Lazycolumn & Lazyrow - are type of layouts that display the content that is only visible to the user, it helps in saving resources and increases speed.

# State
- It is a value that can change over time
- A state component will recompose every time it is changed but the other components will not be recomposed. 

We can define a state by using

var name - remember mutableStateOf(value : 0)

