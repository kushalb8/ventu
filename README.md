export default function CandidateCard({data}){
  return (
    <div style={{border:"1px solid #ccc",padding:10}}>
      <h3>{data.name}</h3>
      <p>Experience: {data.experience} yrs</p>
      <p>Skills: {data.skills}</p>
      <p>Crisis: {data.crisis_score}</p>
      <p>Sustainability: {data.sustainability_score}</p>
      <p>Team: {data.team_score}</p>
    </div>
  )
}
