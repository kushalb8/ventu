const express = require("express");
const cors = require("cors");
const db = require("./db");

const app = express();
app.use(cors());

app.get("/leaderboard",(req,res)=>{
  db.query(`
    SELECT c.name, r.total_score, r.rank_position
    FROM rankings r
    JOIN candidates c ON c.id=r.candidate_id
    ORDER BY r.rank_position
    LIMIT 10
  `,(err,data)=>{
    res.json(data);
  });
});

app.get("/candidates",(req,res)=>{
  db.query(`
    SELECT c.*, e.crisis_score, e.sustainability_score, e.team_score
    FROM candidates c
    JOIN evaluations e ON c.id=e.candidate_id
  `,(err,data)=>{
    res.json(data);
  });
});

app.listen(5000,()=>console.log("Backend running on 5000"));
