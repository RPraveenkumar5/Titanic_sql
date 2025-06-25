create database titanic;

use titanic;
create table Passenger(PassengerId int primary key,Survived int ,Pclass int ,P_Name varchar(30),Sex varchar(10),Age int);
insert into Passenger values(1,0,3,"Braund, Mr. Owen Harris","male",22),
(2,1,1,"Cumings, Mrs. John Bradley","female",38),
(3,1,3,"Heikkinen, Miss. Laina","female",26),
(4,1,1,"Futrelle, Mrs. Jacques Heath","female",35),
(5,0,3,"Allen, Mr. William Henry","male",35),
(6,0,3,"Moran, Mr. James","male",50),
(7,0,1,"McCarthy, Mr. Timothy J","male",54),
(8,0,3,"Palsson, Master. Gosta Leonard","male",2),
(9,1,3,"Johnson, Mrs. Oscar W","female",27),
(10,1,2,"Nasser, Mrs. Nicholas","female",14),
(11,1,3,"Sandstromt","female",4),
(12,1,1,"Bonnell, Miss. Elizabeth","female",58),
(13,0,3,"Saundercock, Mr. William Henry","male",20),
(14,0,3,"Andersson, Mr. Anders Johan","male",39),
(15,0,3,"Vestrom, Miss. Adolfina","female",14),
(16,1,2,"Hewlett, Mrs.Mary","female",55),
(17,0,3,"Rice, Master. Eugene","male",20),
(18,1,2,"Williams, Mr. Charles Eugene","male",65),
(19,0,3,"Vander Planke, Mrs. Julius","female",31),
(20,1,3,"Masselmani, Mrs. Fatima","female",55),
(21,0,2,"Fynney, Mr. Joseph J","male",35),
(22,1,2,"Beesley, Mr. Lawrence","male",34),
(23,1,3,"McGowan, Miss. Anna","female",15),
(24,1,1,"Sloper, Mr. William Thompson","male",28),
(25,0,3,"Palsson, Miss. Torborg Danira","female",80),
(26,1,3,"Asplund, Mrs. Carl Oscar","female",38),
(27,0,3,"Emir, Mr. Farred Chehab","male",20),
(28,0,1,"Fortune, Mr. Charles Alexander","male",19),
(29,1,3,"O'Dwyer, Miss. Ellen ""Nellie""","female",40),
(30,0,3,"Todoroff, Mr. Lalio","male",45),
(31,0,1,"Uruchurtu, Don. Manuel E","male",40),
(32,1,1,"Spencer, Mrs. William Augustu","female",30),
(33,1,3,"Glynn, Miss. Mary Agatha","female",35),
(34,0,2,"Wheadon, Mr. Edward H","male",66),
(35,0,1,"Meyer, Mr. Edgar Joseph","male",28),
(36,0,1,"Holverson, Mr. Alexander Oskar","male",42),
(37,1,3,"Mamee, Mr. Hanna","male",76),
(38,0,3,"Cann, Mr. Ernest Charles","male",21),
(39,0,3,"Vander Planke","female",18),
(40,1,3,"Nicola-Yarred","female",14),
(41,0,3,"Ahlin, Mrs. Johan","female",40),
(42,0,2,"Turpin, Mrs. William","female",27),
(43,0,3,"Kraeff, Mr. Theodor","male",47),
(44,1,2,"Laroche, Miss. Simonne","female",37),
(45,1,3,"Devaney, Miss. Margaret","female",19),
(46,0,3,"Rogers, Mr. William John","male",10),
(47,0,3,"Lennon, Mr. Denis","male",11),
(48,1,3,"O'Driscoll, Miss. Bridget","female",15),
(49,0,3,"Samaan, Mr. Youssef","male",13),
(50,0,3,"Arnold-Franchi, Mrs. Josef","female",18),
(51,0,3,"Panula, Master. Juha Niilo","male",7),
(53,1,1,"Harper, Mrs. Henry","female",49),
(54,1,2," Mrs. Lizzie","female",29);

select * from Passenger;

Use titanic;
create table P_Fare(PassengerId int primary key, Pclass int, Fare int); 
insert into P_Fare values(1,3,10),(2,1,70),(3,3,9),(4,1,80),(5,3,11),(6,3,12),(7,1,82),(8,3,12),(9,3,11),(10,2,25),
(11,3,15),(12,1,79),(13,3,14),(14,3,13),(15,3,12),(16,2,26),(17,3,14),(18,2,27),(19,3,10),(20,3,9),(21,2,27),(22,2,28),
(23,3,14),(24,1,78),(25,3,15),(26,3,13),(27,3,12),(28,1,79),(29,3,11),(30,3,15),(31,1,76),(32,1,75),(33,3,14),(34,2,28),
(35,1,79),(36,1,80),(37,3,11),(38,3,12),(39,3,14),(40,3,13),(41,3,15),(42,2,25),(43,3,12),(44,2,24),(45,3,10),(46,3,11),
(47,3,12),(48,3,14),(49,3,15),(50,3,12),(51,3,13),(52,3,11),(53,1,80),(54,2,26);

select * from P_Fare;

1)There were 54 passengers on the Titanic in the dataset, and out of them, 24 passengers survived the disaster.
select count(PassengerId) as total_Passenger, sum(Survived) as total_survived from Passenger;

2)There were 26 male and 27 female passengers on the Titanic.Out of these, 4 males survived and 20 females survived.
SELECT gender, COUNT(gender) as total_M_F, sum(Survived) as Survived_M_F
FROM Passenger
GROUP BY gender;

3)1st Class: Total passengers = 11, Survived = 6
2nd Class: Total passengers = 9, Survived = 6
3rd Class: Total passengers = 33, Survived = 12
Select Pclass, count(Pclass) as classcount,sum(Survived) as NO_Survived_class
from Passenger 
Group by Pclass;

4)We have two tables, Passenger and PassengerFare. Use an SELF JOIN to combine these tables based on the common column PassengerId.
select passenger.PassengerId,Survived,P_Name,passenger.Pclass,p_fare.Fare
from passenger inner join P_Fare on passenger.PassengerId=p_fare.PassengerId;

5)1st Class: Average fare = 78.00
2nd Class: Average fare = 26.22
3rd Class: Average fare = 12.42
select passenger.Pclass, avg(p_fare.Fare) as avg_Fare
from Passenger,p_fare where passenger.PassengerId = p_fare.PassengerId
Group by Pclass;



