
Tabella utenti
ID              nome                cognome                 provincia_residenza

1               Mario               Rossi                   MI
2               Valentino           Bianchi                 NA
3               Cristina            Verdi                   RO
4               Gianni              Neri                    MI
5               Giorgio             Marroni                 NA


const province = [MI, NA, RO];

//creo una sottotabella per MI
1               Mario               Rossi                   MI
4               Gianni              Neri                    MI

//creo una sottotabella per NA
2               Valentino           Bianchi                 NA
5               Giorgio             Marroni                 NA

//creo una sottotabella per RO
3               Cristina            Verdi                   RO


SELECT COUNT(*), provincia_residenza
FROM tabella_utenti
GROUP BY provincia_residenza

COUNT(*)    provincia_residenza
2           MI
2           NA
1           RO