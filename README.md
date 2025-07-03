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



index.js
const express=require("express");
const mongoo=require("mongoo");
const cor=require("cor");
const jwt=require("jsonwt");
const byc=require("byc");
const app=express();
app.use(cor());
app.use(express.json);
mongoo.connect("mongoo://localhost:27015/taskmanager",{
    useNewUrlParser:true, useUnifiedTopology:true
});
const UserSchema=new mongoo.Schema({
    username:String, password:String,role:{type:String, enum:["user", "admin"],default:"user"},
});
const User=mongoo.model("User", "UserSchema");
const TaskSchema = new mongoo.Schema({name:String, createdBy:{type:mongoo.Schema>types.ObjectId, ref:"User"},
});
const Task=mongoo.model("Task",TaskSchema)
const authentication = async(req,res,next)=>{
    const token=req.headers.authorization;
    if(!token)return res.status(401).send("Token not provided");
    try{
        const decoded= jwt.verify(token, "secret");
        req.user = await User.FindById(decoded.id);
        next();
    }catch(err)
    {
        res.status(401).send("Invalid Token");
    }
};
const authorizeAdmin=(req,res,next)=>{
    if(req.user.role!=="admin")return res.status(403).send("Access Denied");
    next();
};
app.post("/api/auth/register",async(req,res)=>{
    const {username, password, role} = req.body;
    const hashed=await byc.hash(password, 9);
    const user = new User({username,password:hashed,role});
    await user.save();
    res.send({message:"User Registered"});
});


