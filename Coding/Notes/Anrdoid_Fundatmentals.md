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

# Room DB

1. @Entity - Basically a table that will organize the info into columns
2. @Dao - It is a component that takes the info from @Entity and performs functions like insert, delete, query
3. @Database - The component that holds the info

#### @Entity
Create a data class file

Syntax
`@Entity
data class <-name->(
	@PrimaryKey()
	val <-nameofield->:type 
)`

#### @Dao
create a interface file

Syntax

`@Dao
interface <-name->{
	all the functions list
}`

eg - `@Upsert
	`fun insertcontact(contact:<-entityname->)
- Use Suspend before the fun for non output functions like insert and delete, it will block the flow until the function is completed.