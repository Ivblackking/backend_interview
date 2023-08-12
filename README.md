# backend_interview
## sql questions
1) Нормальні форми / нормалізація
2) Денормалізація
3) Кластерний індекс
4) Транзакція
5) ACID
6) views
7) stored procedures
8) Trigers
9) Indexes

code examples:
---------------------------------------------------------------------------------
-- SQL tasks

create view vw_ProductToys as
	select * from where ProducType = 'Toys'
  
select * from vw_ProductToysc

----------------------------------------------------------------------------------
car
id, brand, color

owner
id, sex, firstname, lastname

owner_car
id, owner_id, car_id
1,1, 1
2,2, 1
3,4, 1
4,1, 3

create constraint pkOwnerCar primary key clustered on owner_car (id);

create nonclusterd index in_ownercar_carid on owner_car (car_id);

create nonclusterd index in_ownercar_ownerid on owner_car (owner_id);

select car.brand, car.color, owner.firstname, ower.lastname
from owner_car 
	join owner on owner_car.owner_id = owner.id 
  	join car on owner_car.car_id = car.id;
  
select owner.firstname, ower.lastname, count(car_id)
from owner
	join owner_car on owner.id = owner_car.owner_id
group by owner.firstname, ower.lastname
having count(car_id) > 2;
