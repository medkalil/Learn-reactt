# Learn-reactt
setState Exemple:
//class App

import React from "react"
import TodoItem from "./TodoItem"
import todosData from "./todosData"

class App extends React.Component {
    constructor() {
        super()
        this.state = {
            todos: todosData
        }
        this.handleChange = this.handleChange.bind(this)
    }
    
    handleChange(id) {
       this.setState(prevState=>{
           const updatedList= prevState.todos.map(item =>{
               if(item.id == id){
                   item.completed = !item.completed
               }
               return item
           } )
           return{
               todos: updatedList
           }
       })
    }
    
    render() {
        const todoItems = this.state.todos.map(item => <TodoItem 
        key={item.id}
        item={item}
        handleChange={this.handleChange} />)
        
        return (
            <div className="todo-list">
                {todoItems}
            </div>
        )    
    }
}

export default App

class TodoItem
import React from "react"

function TodoItem(props) {
    return (
        <div className="todo-item">
            <input 
                type="checkbox" 
                checked={props.item.completed} 
                onChange={() => props.handleChange(props.item.id) }
            />
            <p>{props.item.text}</p>
        </div>
    )
}

export default TodoItem
