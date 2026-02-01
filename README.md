const db = require("./db");
const { faker } = require("@faker-js/faker");

for(let i=0;i<40;i++){
  const name = faker.person.fullName();
  const exp = faker.number.int({min:1,max:15});
  const skills = faker.helpers.arrayElements(
    ["Leadership","Safety","AI","Operations","Lean","Sustainability"],
    3
  ).join(",");

  db.query(
    "INSERT INTO candidates (name,experience,skills) VALUES (?,?,?)",
    [name,exp,skills]
  );

  const crisis = faker.number.float({min:5,max:10});
  const sustain = faker.number.float({min:5,max:10});
  const team = faker.number.float({min:5,max:10});

  db.query(
    "INSERT INTO evaluations (candidate_id,crisis_score,sustainability_score,team_score) VALUES (LAST_INSERT_ID(),?,?,?)",
    [crisis,sustain,team]
  );
}

console.log("40 candidates added");
