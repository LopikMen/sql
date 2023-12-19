# sql
тип
SELECT DISTINCT
Tovars.id,Tovars.name,
CASE 
WHEN Pizza.type_id = 1 THEN 'детский' 
WHEN Pizza.type_id = 2 THEN 'острый' 
WHEN Pizza.type_id = 3 THEN 'веганский' 
END  FROM Tovars 
JOIN Pizza
WHERE Pizza.type_id = 2 and Pizza.tovar_id=Tovars.id;


позиция
SELECT DISTINCT
Tovars.id,Tovars.name,
CASE 
WHEN Pizza.position_id = 1 THEN 'новинка' 
WHEN Pizza.position_id = 2 THEN 'хит' 
WHEN Pizza.position_id = 3 THEN 'без мяса'
WHEN Pizza.position_id = 4 THEN 'выгодно'

END  FROM Tovars 
JOIN Pizza
WHERE Pizza.position_id = 2 and Pizza.tovar_id=Tovars.id;

создание пользователя 
insERT into User (name,phone,street)
VALUES('1','88005553535','Пушкина');
insERT into Log (login,user_id,password)
VALUES('1',1,SHA2('P@ssw0rd',256));

корзина
INSERT INTO Basket(user_id, Pizza_id)
VALUES (
  (SELECT DISTINCT Log.user_id
  FROM Log
  WHERE sha2('P@ssw0rd', 256) = Log.password),
  
  (SELECT DISTINCT id
  FROM Pizza
  WHERE type_id = 2 AND size_id = 2 AND tyype_pizza = 2)
);
