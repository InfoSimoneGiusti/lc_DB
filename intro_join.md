
// tabella province

ID              targa
1               PT
2               PO
3               FI
4               LU



// tabella utenti

ID          nome            provincia_id
1           Mario           1
2           Cristina        3
3           Giuseppe        NULL
4           Giacomo         NULL
5           Luisa           4





// risposta da fornire

SELECT utenti.id AS id_utente, utenti.nome, utenti.provincia_id, province.ID as id_provincia, province.targa
FROM utenti
JOIN province
ON utenti.provincia_id = province.id


id_utente           nome            provincia_id        id_provincia            targa
1                   Mario           1                   1                       PT
2                   Cristina        3                   3                       FI
5                   Luisa           4                   4                       LU











// risposta da fornire alternativa


SELECT utenti.id AS id_utente, utenti.nome, utenti.provincia_id, province.ID as id_provincia, province.targa
FROM utenti LEFT JOIN province
ON utenti.provincia_id = province.id


id_utente           nome            provincia_id        id_provincia            targa
1                   Mario           1                   1                       PT
2                   Cristina        3                   3                       FI
3                   Giuseppe        NULL                NULL                    NULL
4                   Giacomo         NULL                NULL                    NULL
5                   Luisa           4                   4                       LU
