<!-- Buscar el informe del caso -->
SELECT * FROM crime_scene_report WHERE city = 'SQL City' 
AND date = 20180115
AND type = 'murder';

<!-- Busco a los testigos -->
SELECT * FROM person WHERE address_street_name = 'Northwestern Dr'
ORDER BY address_number DESC LIMIT 1;

SELECT * FROM person WHERE name LIKE 'Annabel%'
AND address_street_name = 'Franklin Ave';

<!-- Leer las declaraciones de los testigos -->
SELECT * FROM interview WHERE person_id IN (14887, 16371);

<!-- Busco a los miembros del gimnasio con las características dadas por los testigos -->
SELECT * FROM get_fit_now_member WHERE membership_status = 'gold'
AND id LIKE '48Z%';

SELECT * FROM get_fit_now_check_in
WHERE check_in_date = 20180109
AND membership_id LIKE '48Z%';

<!-- Busco coincidencias con la matrícula de coche y los dos sospechosos -->
SELECT * FROM person WHERE id IN (28819, 67318);

SELECT * FROM drivers_license WHERE id IN (173289, 423327);

<!-- Confirmo el nombre con el que coinciden todos los datos -->
INSERT INTO solution VALUES (1, 'Jeremy Bowers');

SELECT value FROM solution;

<!-- Sigo pistas para buscar al culpable -->
SELECT * FROM interview WHERE person_id = 67318;

SELECT * FROM drivers_license WHERE gender = 'female'
AND hair_color = 'red'
AND height BETWEEN 65 AND 67
AND car_make = 'Tesla'
AND car_model = 'Model S';

<!-- Cruzo licencia id con person id-->
SELECT id, name, license_id FROM person 
WHERE license_id IN (202298, 291182, 918773);

<!-- Buscar coincidencias en el evento -->
SELECT person_id, COUNT(*) AS veces
FROM facebook_event_checkin
WHERE person_id IN (78881, 90700, 99716)
AND event_name = 'SQL Symphony Concert'
AND date BETWEEN 20171201 AND 20171231
GROUP BY person_id;

<!-- Resultado -->
INSERT INTO solution VALUES (1, 'Miranda Priestly');
SELECT value FROM solution;
