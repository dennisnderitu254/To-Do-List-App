# This is a TO-DO-LIST Application in React JS

- ADD IMAGE

## Steps to create the Application:

- `NPX`: It is a package runner tool that comes with npm 5.2+, npx is easy to use CLI tools. The npx is used for executing Node packages.

```
npx create-react-app todo-react
```

- Go to the Directory

```
cd todo-react
```

- Install the bootstrap and react-bootstrap module

```
npm install bootstrap
npm install react-bootstrap
```

- Folder Structure

- ADD IMAGE

- The dependencies in package.json file

```
"dependencies": {
    "@testing-library/jest-dom": "^5.16.5",
    "@testing-library/react": "^13.4.0",
    "@testing-library/user-event": "^13.5.0",
    "react": "^18.2.0",
    "bootstrap": "^5.3.0",
    "react-bootstrap": "^2.7.4",
    "react-dom": "^18.2.0",
    "react-scripts": "5.0.1",
    "web-vitals": "^2.1.4"
}
```

[App.js File](https://github.com/dennisnderitu254/To-Do-List-App/blob/main/todo-react/src/App.js)

- Steps to run the Application:

```
class App extends Component { 
	constructor(props) { 
		super(props); 

		// Setting up state 
		this.state = { 
			userInput: "", 
			list: [], 
		}; 
	} 

	// Set a user input value 
	updateInput(value) { 
		this.setState({ 
			userInput: value, 
		}); 
	} 
```

- The code defines a class named `App`that extends the `Component` class from React. This means `App` inherits functionalities from the base `Component` class.

## Component State

- Inside the `constructor`, the `state` object is initialized. This object holds data specific to the component and can be updated to reflect changes in the UI.
- Here, the state object has two properties:
    - userInput: Stores the user's input value (initially empty).
    - list: An empty array to store the list items.

## Component Methods


- `updateInput(value)`: This function updates the `userInput` state property with the provided `value`. It's likely triggered by an onChange event from an input field.

```
// Add item if user input in not empty 
	addItem() { 
		if (this.state.userInput !== "") { 
			const userInput = { 
				// Add a random id which is used to delete 
				id: Math.random(), 

				// Add a user value to list 
				value: this.state.userInput, 
			}; 

			// Update list 
			const list = [...this.state.list]; 
			list.push(userInput); 

			// reset state 
			this.setState({ 
				list, 
				userInput: "", 
			}); 
		} 
	} 
```

- `addItem()`: This function adds a new item to the `list` if the `userInput` is not empty. It does the following:
* Creates a new object with a random `id` (for deletion purposes) and the user input value.
* Creates a copy of the existing `list` using spread syntax (`[...]`).
* Pushes the new item object onto the copied list.
* Updates the state with the new `list` and resets `userInput` to an empty string.

```
// Function to delete item from list use id to delete 
	deleteItem(key) { 
		const list = [...this.state.list]; 

		// Filter values and leave value which we need to delete 
		const updateList = list.filter((item) => item.id !== key); 

		// Update list in state 
		this.setState({ 
			list: updateList, 
		}); 
	} 
```

- `deleteItem(key)`: This function removes an item from the `list` based on its `id` (the `key` parameter). It does the following:
* Creates a copy of the existing `list`.
* Filters the copied list to keep only items where the `id` doesn't match the provided `key`.
* Updates the state with the filtered list.

```
editItem = (index) => { 
	const todos = [...this.state.list]; 
	const editedTodo = prompt('Edit the todo:'); 
	if (editedTodo !== null && editedTodo.trim() !== '') { 
		let updatedTodos = [...todos] 
		updatedTodos[index].value= editedTodo 
		this.setState({ 
		list: updatedTodos, 
	}); 
	} 
	} 
```

- `editItem(index)`: This function edits an existing item in the list based on its index. It does the following:
* Creates a copy of the existing `list`.
Prompts the user to edit the item value using `prompt`.
* Checks if the user entered a valid value (not null or empty after trimming).
* If valid, updates the value of the item at the specified index in the copied list.
* Updates the state with the modified list.

## Component Render:

- The `render` method defines the UI structure of the component. It returns JSX (JavaScript XML) that represents the HTML elements to be displayed. Here's a breakdown of the structure:

* A `Container` component likely defines a layout container.
* A `Row` component displays the title "TODO LIST" with specific styling.
* An `InputGroup` component holds the input field for user input and an "ADD"    button. The button calls the `addItem` function on click.
* A `ListGroup` component displays the list items. It uses the `map` function to iterate over the `list` state and render a `ListGroup.Item` component for each item.
    - Each `ListGroup.Item` displays the item value and two buttons: "Delete" and "Edit".
    - The "Delete" button calls the `deleteItem` function with the item's `id`.
    - The "Edit" button calls the `editItem` function with the item's index.


- Type the following command in the terminal

```
npm start
```

- Type the following URL in the browser:

```
 http://localhost:3000/
```