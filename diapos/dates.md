# présentation Générale

----

## 15 Agents 

### 9 Cadres A - 6 Cadre B
### 1 agent sur le site de Caen jusqu'à Septembre 2018
### 1 départ à la retraite courant 2018
### Format caractère --> Format date

## 9 Aplications et 2 WebService
### DESSIN : 5 applications et 2 WebService
### PAPAYE
### CRPI
### OCTAVIE
### ORIGAMI (passage de la maintenance à Nantes courant 2018)

----

## L'utilisation des dates dans la clause `where`
Pour récupérer toutes les lignes dont la variable date se situe après un moment précis, on peut faire
```sql
select count(*) from t_historique where d_maj>to_date('10/04/2017 15:50:00','dd/mm/yyyy hh24:mi:ss');
```
Pour récupérer les données d’un jour précis voire d'un moment précis dans la journée, il existe différentes façons de faire
```sql
select * from eap.questionnaire where to_char(d_traitement, 'yyyymmdd')='20170320';
select * from eap.questionnaire where d_traitement>='06/12/2017' and d_traitement<'07/12/2017';
select * from eap.questionnaire where d_traitement>=to_date('2017/12/06 09:32:00', 'yyyy/mm/dd hh24:mi:ss')and d_traitement<to_date('2017/12/06 18:00:00', 'yyyy/mm/dd hh24:mi:ss');
select * from eap.questionnaire where d_traitement between to_date('2017/12/06 09:30:00', 'yyyy/mm/dd hh24:mi:ss') and to_date('2017/12/06 18:00:00', 'yyyy/mm/dd hh24:mi:ss');
```
