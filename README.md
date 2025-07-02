<!DOCTYPE html>
<head><meta charset="UTF-8">
<title>COLLABORATIVE TASK MANAGER⚙️.</title>
<script src="C:\Users\dell\Desktop\WEB\react.js"></script>
<index class="C:\Users\dell\Desktop\WEB"></index> 
</head>
<body style="background-color: bisque;">
    <center>
        <style>
            h1{
                color:aqua;
                font-weight: bold;
            }
        </style>
        <h1>COLLABORATIVE TASK MANAGER</h1>
        <img src="https://www.shutterstock.com/image-vector/welcome-colorful-letters-banner-can-260nw-1313361116.jpg">
                
        <div id="dashboard" class="hidden">
            <h2>Your tasks</h2>
            <button>Open</button>
            <button onclick="location.href='file:///C:/Users/dell/Desktop/WEB/login.html/login.html'"class="bg-blue">Login</button>
            <u1 id="userTasks"class="list"></u1>
            <h2>Created Tasks</h2>
            <button>Open</button>
            <h2>Deleted Tasks</h2>
            <button>Open</button>
            <ul id="createdTasks"class="list-disc"></ul></form>
            
        </div>
        <div id="taskFormContainer"class="hidden mt">
            <h2>Create a New Task</h2>
            <form id="taskForm"class="flex flex-col gap-2">
                <input type="text"id="taskName"placeholder="Task Name">
                <button type="submit"class="bg-green">Add Task</button>
            </form>
        </div>
    </center>
    </body>

