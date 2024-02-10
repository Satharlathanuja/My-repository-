
1.To do list app

Certainly! To create a simple to-do list app, we can use HTML, CSS, and JavaScript. Below is a basic example code for a to-do list app:

**index.html:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href="styles.css">
    <title>To-Do List App</title>
</head>
<body>
    <div id="app">
        <h1>To-Do List</h1>
        <input type="text" id="taskInput" placeholder="Add a new task">
        <button onclick="addTask()">Add Task</button>
        <ul id="taskList"></ul>
    </div>

    <script src="app.js"></script>
</body>
</html>
```

**styles.css:**
```css
body {
    font-family: Arial, sans-serif;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

#app {
    text-align: center;
}

ul {
    list-style-type: none;
    padding: 0;
}

li {
    margin: 10px;
    padding: 8px;
    border: 1px solid #ccc;
    border-radius: 5px;
    cursor: pointer;
}

li:hover {
    background-color: #f0f0f0;
}
```

**app.js:**
```javascript
// Array to store tasks
let tasks = [];

// Function to add a new task
function addTask() {
    const taskInput = document.getElementById("taskInput");
    const taskList = document.getElementById("taskList");

    const taskText = taskInput.value.trim();

    if (taskText !== "") {
        // Add task to array
        tasks.push(taskText);

        // Clear input field
        taskInput.value = "";

        // Render tasks
        renderTasks();
    }
}

// Function to render tasks
function renderTasks() {
    const taskList = document.getElementById("taskList");
    taskList.innerHTML = "";

    // Loop through tasks and create list items
    tasks.forEach((task, index) => {
        const li = document.createElement("li");
        li.textContent = task;
        li.setAttribute("onclick", `removeTask(${index})`);
        taskList.appendChild(li);
    });
}

// Function to remove a task
function removeTask(index) {
    // Remove task from array
    tasks.splice(index, 1);

    // Render updated tasks
    renderTasks();
}
```