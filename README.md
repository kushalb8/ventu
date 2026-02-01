INSERT INTO rankings (candidate_id, total_score)
SELECT 
  candidate_id,
  (crisis_score + sustainability_score + team_score)/3
FROM evaluations;

SET @r=0;

UPDATE rankings
SET rank_position = (@r:=@r+1)
ORDER BY total_score DESC;
