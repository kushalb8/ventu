import { useEffect, useState } from "react";
import Leaderboard from "./Leaderboard";
import CandidateCard from "./CandidateCard";

function App(){
  const [candidates,setCandidates]=useState([]);

  useEffect(()=>{
    fetch("http://localhost:5000/candidates")
      .then(r=>r.json())
      .then(setCandidates);
  },[]);

  return (
    <div style={{padding:20}}>
      <h1>Recycling Manager Dashboard</h1>
      <Leaderboard/>
      <div style={{display:"grid",gridTemplateColumns:"repeat(3,1fr)",gap:15}}>
        {candidates.map(c=><CandidateCard key={c.id} data={c}/>)}
      </div>
    </div>
  )
}

export default App;
