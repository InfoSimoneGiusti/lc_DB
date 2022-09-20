
// tabella utenti
ID          nome            provincia_id
1           Mario           1
2           Cristina        3


// tabella province
ID              targa
1               PT
2               PO
3               FI


SELECT *
FROM utenti
JOIN province
ON utenti.provincia_id = province.id


ID          nome            provincia_id                ID              targa
1           Mario           1                           1               PT
2           Cristina        3                           3               FI