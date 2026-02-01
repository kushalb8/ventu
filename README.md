CREATE DATABASE recycling_system;
USE recycling_system;

CREATE TABLE candidates (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100),
    experience INT,
    skills TEXT
);

CREATE TABLE evaluations (
    id INT AUTO_INCREMENT PRIMARY KEY,
    candidate_id INT,
    crisis_score FLOAT,
    sustainability_score FLOAT,
    team_score FLOAT,
    FOREIGN KEY (candidate_id) REFERENCES candidates(id)
);

CREATE TABLE rankings (
    candidate_id INT PRIMARY KEY,
    total_score FLOAT,
    rank_position INT
);
