import { useEffect,useState } from "react";

export default function Leaderboard(){
  const [top,setTop]=useState([]);

  useEffect(()=>{
    fetch("http://localhost:5000/leaderboard")
      .then(r=>r.json())
      .then(setTop);
  },[]);

  return (
    <>
      <h2>Top 10 Candidates</h2>
      <ol>
        {top.map(t=>(
          <li key={t.rank_position}>
            {t.name} - {t.total_score.toFixed(2)}
          </li>
        ))}
      </ol>
    </>
  )
}
