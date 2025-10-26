# Group 7 MIST4610 Group Project 1
## Team Name:
15058 Group 7
## Team Members:
1. Angela Ren - https://github.com/angelaaa456 
2. Audrey Staples - https://github.com/audreystaples 
3. Sammy Effron - https://github.com/Seffron 
4. Tyler Schildkraut - https://github.com/tylerschildkraut 
5. Tanner Sutherland - https://github.com/tannersutherland 
## Scenario Description:
We wanted to construct a data model that organizes key information used to navigate the NCAA college football landscape. The ultimate goal for our model is to represent the various relationships that exist among Coaches, Teams, Players, Rosters, Games, etc. in a way that mirrors how real NCAA programs operate. Although our data is hypothetical, it represents pertinent information that would meet managerial requirements within the NCAA ecosystem. From surveying game statistics to determining player status on a roster, our database provides insights that would prove highly useful to NCAA stakeholders. Ultimately, we aimed to create a database that would effectively aid managerial decision making within essential business units such as logistics management, decision-making, and reporting within an ever evolving industry.
## Data Model
<img width="621" height="658" alt="Screenshot 2025-10-25 145857" src="https://github.com/user-attachments/assets/bad225f2-d484-4dff-af7a-8bdd38e3ce03" />


Explanation of data model:

Our database is based on the NCAA with hypothetical data included for ease of data insertion. For instance, instead of the University of Georgia the record is the Athens Bulldogs.

Beginning with the Teams entity, we made teamID our identifier and included attributes such as teamName and conference. This entity relates to our Coaches entity with a one-to-many relationship because Teams have many Coaches, but those Coaches are linked to only one Team. Our Coaches attribute is identified by a coachID and contains attributes such as name, role which describes their specific coaching position (Head Coach, Offensive Coordinator, etc.), yearsOfExperience describing the amount of years of coaching experience they have, as well as a foreign key of teamID. Rosters represent the associative entity connecting the many-to-many relationship between Teams and Players as players can be on many teams and teams are composed of many players. Rosters are identified by rosterID, and they have attributes such as a foreign keys playerID and teamID. Additionally, Rosters display the startDate of a player’s commitment to a team as well as the endDate which could be null if the player is still playing. Rosters also display the player’s position on that specific team as well as their jersey number on that specific team. The Players entity is identified by a unique playerID which is the primary key of that entity. In addition to that, the Players entity has attributes such as name, the player’s yearInSchool, their height in inches, their weight in pounds, and the status of their scholarship, if applicable. Additionally, the Players entity has a one-to-many relationship with the entity named Injuries as players have many injuries but a specific instance of an injury can only occur once in one player. Injuries have the primary key injuryID along with attributes such as injuryName, lengthOfRecovery, surgery name if needed, as well as the foreign key playerID which specifies the one-to-many relationship.

Moving on to another key entity, we have Games. Games are identified by their primary key which is called gameID. Our Teams table has two one-to-many relationships with the Games entity meaning that one instance of a Team (the home team) has many games but those games only have the one home team. Additionally, another instance of a Team (the away team) also has many Games but those specific games are only related to one away team. For that reason, our Games entity contains two foreign keys from the Teams table, one being homeTeamID and the other being awayTeamID. Another foreign key in the Games table is the stadiumID. The last attribute in the Games table is the date attribute which specifies the date the game occurred on. Our Stadiums table represents a one-to-many relationship between Stadiums and Games. Stadiums house many games but those games can only be played at one stadium at a time. Stadiums are also identified by attributes such as stadiumName, city, and capacity. Stadiums also have a one-to-many relationship with Seats because a stadium has many seats but a seat can only be in one stadium. Seats have the primary key seatID as well as attributes like section, row, seatNumber, seatType, and the foreign key stadiumID. Seats also have a one-to-many relationship with Tickets as a seat can be sold by many tickets but tickets only are attached to one seat. Tickets are identified by ticketID, and have attributes such as price, ticketHolderName, the foreign key gameID, and the foreign key seatID. This then brings about the relationship between Games and Tickets being one-to-many as games have many tickets but a specific ticket is only attached to one game. The last entity that needs describing is our Statistics entity. Statistics has a many-to-one relationship with Players as Players have many statistics but a specific statistic is only connected to one player. Another relationship that exists with Statistics is a many-to-one relationship with Games. Statistics are present in many games, but a game only has one instance of a specific player statistic. Statistics are identified by a statID, a foreign key of playerID, yards if applicable, touchdowns if applicable, tackles if applicable, interceptions if applicable, receptions if applicable, fieldGoals if applicable, as well as the foreign key gameID.


## Data Dictionary

<img width="822" height="779" alt="Screenshot 2025-10-26 114444" src="https://github.com/user-attachments/assets/f95a8534-08f8-41aa-8daa-93bf66eb6cc4" />
<img width="795" height="353" alt="Screenshot 2025-10-26 114517" src="https://github.com/user-attachments/assets/57fbb625-e864-40da-b8a8-b258baeab7fe" />
<img width="806" height="241" alt="Screenshot 2025-10-26 114455" src="https://github.com/user-attachments/assets/3e4feb30-7a36-470d-bb8f-ac84ca191f3e" />
<img width="808" height="564" alt="Screenshot 2025-10-26 114523" src="https://github.com/user-attachments/assets/504b5730-de30-450d-a26b-3a30e4ba089f" />
<img width="747" height="295" alt="Screenshot 2025-10-26 114427" src="https://github.com/user-attachments/assets/72ab82ef-92b5-49f6-8523-ab836bf57ff6" />
<img width="763" height="611" alt="Screenshot 2025-10-26 114415" src="https://github.com/user-attachments/assets/073f6d28-a6c5-4ec2-ada6-233f7503c02c" />
<img width="765" height="474" alt="Screenshot 2025-10-26 114354" src="https://github.com/user-attachments/assets/ee3bb262-94d4-4816-b8a5-8127274d7abd" />


## Queries:
<img width="778" height="322" alt="Screenshot 2025-10-26 114907" src="https://github.com/user-attachments/assets/35460356-8b5c-4d89-8baf-ba2ddbddc79b" />


Query 1: Number of Players on Each Team

Description:
This query shows every team and counts how many players are currently listed on their roster. It joins the Teams and Rosters tables using the teamID to associate players with their teams, then groups the results by each team name.

Justification:
Roster size directly affects scholarship budgeting, recruiting needs, and practice planning. Athletic departments can use this information to verify roster compliance with NCAA limits (e.g., 85 scholarship players in Division I football) and identify whether certain teams are under- or over-staffed. It also provides insights for coaching staff to balance positional depth across the roster.

<img width="527" height="786" alt="image" src="https://github.com/user-attachments/assets/711bf7c8-7bcf-400f-a8b4-8a07e28d8c2b" />



Query 2: Total Yards per Player

Description:
Calculates the total number of offensive yards gained by each player across all games using the Statistics table. The query groups by player name and sums their yards column, returning players in descending order of total yardage.

Justification:
Tracking cumulative yardage helps offensive coordinators evaluate player impact and consistency. This data is key for determining award nominations, highlighting top performers in media relations, and identifying players who may deserve more playing time or position adjustments based on productivity.

<img width="585" height="825" alt="image" src="https://github.com/user-attachments/assets/1aba97ef-cf74-448d-a142-ce6a9c4ca473" />



Query 3: Players Without Recorded Statistics

Description:
Identifies all players who have not yet recorded any game statistics by checking which player IDs are not present in the Statistics table.


Justification:
This helps coaching staff and analysts find players who have not appeared in any games and make decisions about those players accordingly. Managers can use this information to determine which players may need more opportunities to play or to address what to do with those players in the future.

<img width="611" height="728" alt="image" src="https://github.com/user-attachments/assets/19da2328-a598-474d-9813-9cad3583d615" />




Query 4: Players with Multiple Recorded Injuries

Description:
Displays all players who have sustained more than one recorded injury. It joins Players and Injuries using playerID, groups the results by player, and filters using a HAVING clause.

Justification:
Identifying players with frequent injuries allows medical staff to implement personalized recovery or training programs. Coaches can use this information to manage playing time and avoid re-injury, which reduces long-term risk and protects the team’s investment in scholarship athletes.

<img width="592" height="643" alt="image" src="https://github.com/user-attachments/assets/e412f4f1-de94-4449-b6bc-635ceedd921f" />




Query 5: Average Player Weight by Position

Description:
Finds the average weight of players for each position across all rosters. It joins Rosters and Players and groups the results by position.


Justification:
Weight and conditioning benchmarks are crucial for maintaining competitiveness. This data helps strength and conditioning coaches monitor whether players at each position (e.g., linemen, receivers, linebackers) meet desired physical standards and make training adjustments if a position group is under or over target weight ranges.

<img width="607" height="577" alt="image" src="https://github.com/user-attachments/assets/b316ecec-1ec7-4d75-909d-2751f1ed1f94" />




Query 6: Total Games Played by Each Team

Description:
Shows the number of total games each team has participated in—both home and away. It joins Teams and Games and counts how many times a team appears as either the home or away team.

Justification:
Tracking total games played helps administrators measure team activity levels across the season and can highlight scheduling imbalances. Operations teams can use this data to evaluate travel frequency, ensure scheduling fairness, and make logistical improvements for future seasons.

<img width="613" height="792" alt="image" src="https://github.com/user-attachments/assets/b96eec25-1d1b-4364-b2a6-7c8fa91c2f33" />



Query 7: Current Scholarship Players

Description:
Lists all players who currently receive full athletic scholarships, ordered alphabetically by name.

Justification:
Scholarship allocation is one of the largest financial responsibilities for athletic programs. This query helps compliance officers ensure that scholarship funds are properly assigned and enables administrators to monitor financial obligations and renewal cycles.

<img width="462" height="772" alt="image" src="https://github.com/user-attachments/assets/b5bb9a8b-09ae-40d1-8c63-3d9f2203b3a5" />



Query 8: Longest Recovery Injuries

Description:
Displays the injuries in the database with the longest reported recovery times, ordered from longest to shortest.

Justification:
Provides insight into which types of injuries are most severe and time-consuming to heal. This allows sports medicine staff to plan future prevention programs, identify potential insurance or cost implications, and communicate expected recovery timelines to coaches and media. Although we had not yet learned this feature, we utilized AI to accomplish this query as the VARCHAR() data format is not compatible with the ORDER BY DESC or ASC capabilities. Utilizing CAST and UNSIGNED, our string data values were converted to numbers effectively.

<img width="553" height="772" alt="image" src="https://github.com/user-attachments/assets/415c4214-2e11-44b4-9056-dcf60e72d7df" />




Query 9: Average Ticket Price per Game

Description:
Calculates the average price of tickets sold for each game by joining the Games and Tickets tables and grouping results by gameID.

Justification:
Understanding average ticket prices helps the marketing and sales department assess revenue potential per game. It also reveals which matchups draw higher-paying audiences, allowing pricing strategies to be adjusted for rivalry or high-demand games to maximize profits. Similarly as before, we utilized the CAST function so that we could convert the original VARCHAR value of the price attribute in the Tickets entity to DECIMAL data formats so that we would be able to perform aggregations on the values.

<img width="595" height="722" alt="image" src="https://github.com/user-attachments/assets/21477fa6-d963-4761-8014-6609274db2ae" />



Query 10: Top 5 Players by Touchdowns Scored

Description:
Lists the five players with the highest total touchdowns recorded across all games.

Justification:
This helps highlight standout offensive players for performance evaluations, awards, and media recognition. Teams can also use this information for recruiting promotions and identifying which athletes consistently contribute to scoring.


<img width="582" height="488" alt="image" src="https://github.com/user-attachments/assets/81c42b8c-db79-4270-a1f3-8dba9465cc38" />


## Database information:
Name of database: ns_Group7







