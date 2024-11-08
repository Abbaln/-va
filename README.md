# -va

<!DOCTYPE html>
<html lang="eng">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Slutuppgift</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>
    <main>
        <header><h1>To do list</h1></header>
        <input type="text" id="taskInput" placeholder="Uppdatera to do listan">
        <button id="addTaskBtn">Lägg till</button>
        <ul id="todoList"></ul>

        <script src="script.js"></script>
    
    </main>
    
    
    
</body>
</html>

body {
    background-color: azure;
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    margin: 0;
    padding: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
}

h1 {
    font-size: 46px;
    box-shadow: 10px 5px rgb(0, 0, 0);
    border: thick double rgb(168, 0, 0);
    border-radius: 25px;
    border-style: dashed;
    box-sizing: content-box;
    width: 100%;
    padding: 20px 5px 10px;
    

}




let toDo = [];

function rendertasks() {
    const todoList = document.getElementById('todoList');
    todoList.innerHTML = '';

    toDo.forEach((task, index) => {
        const li = document.createElement('li');
        li.textContent = task;
        
        const removeBtn = document.createElement('button');
        removeBtn.textContent = 'Ta bort';
        removeBtn.onclick = () => {
            removeTask(index);
        }

        li.appendChild(removeBtn);
        todoList.appendChild(li);
    
});

}

function addTask() {
    const taskInput = document.getElementById('taskInput');
    const newTask = taskInput.value;
     
     if (newTask) {
        toDo.push(newTask);
        taskInput.value = '';
        rendertasks();
     }

}



function removeTask(index) {
    toDo.splice(index, 1);
    rendertasks();
}

document.getElementById('addTaskBtn').onclick = addTask;
