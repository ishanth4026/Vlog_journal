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

- For query use @Quesry("SQL cmd")

#### @Database

create a class file

Syntax
@Database (
	entities = [ entity list ]
		version = 1
)

abstract class <-name->: RoomDatabase() {
	abstract val dao: <-Dao name ->
}

- First we give a list of all our entities and then create the room DB with all the Dao names


# Frontend-Backend communication

#### Events file

- This is a sealed interface file that is used to have the triggers for actions and info that needs to be used for example: It will have the trigger and info needed to save a new contact, it will be triggered with the UI, then it will send the data needed for that action.

- Eg:
	`Sealed interface contactevents {
		object savecontact : contactevents
		data class firstname (val firstname: String)
	}
`
- The object in the above example is the thing that determines the trigger for that specific action
- The data class will contain the info needed for that action which is triggered.
- We use ":" in the object to link the trigger to this event, this allows us to use the same trigger for multiple pages in multiple sealed interface.


#### Enum file
This is used for fixed lists of choices, eg: like options in drop down menu

#### State file (data class file)
- This is similar to the staging are in git, it stores screenshots of the info that needs to be displayed in UI.
- Always provide default values, or else it will not work when there is no info to dsplay
- Eg: `data class contactstate(
	val firstname : String = ""
	)`


#### View Model file (class file)
- View model is the brains that connects with database, collects the info and performs the action and then sends the new info to the state which redraws the UI.
- Eg: `class contactviewmodel(
	private cal dao : ContactDao
	) : ViewModel() {
		private val _sortType = mutablestateflow(contactstate)
		
		fun onEvent(event : contactevents){
			when(event){
				is contactevent.deletecontact -> {
					what it needs to do
				}
			}
		}
	}`

- So in above code the mutablestateflow() is used, so that it keeps on checking for new state snapshot and if there is it redraws the UI.
- The onEvent is a fun used to give instructions on what to do when the object from events is triggered.
- It uses when and is like "if that then do this" analogy, like when event is savecontact do that from dao

# Flow


![[Untitled.png]]
- In a app each page will have it's dedicated:
	1. Event file
	2. State file
	3. Viewmodel file