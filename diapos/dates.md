# Les agents

----

## Convertion format date <--> format caractère

### Format caractère --> Format date
Utiliser la fonction `to_date()` qui convertit une variable caractère au format date en utilisant le format spécifié
```sql
select to_date('2015/12/11', 'yyyy/mm/dd') as date_convertie from dual;
select to_date(date_anniversaire, 'yyyy/mm/dd') as date_convertie from maTable;
```
### Format date --> Format caractère et numérique
Utiliser la fonction `to_char()` qui convertit une variable date au format caractère en utilisant le format spécifié. On peut ensuite utiliser la fonction `to_number()` pour convertir la chaîne de caractères au format numérique
```sql
select to_char(d_traitement, 'yyyymmdd hh24:mi:ss') from eap.questionnaire;
select to_number(to_char(date_vente, 'yyyy')) as annee from maTable;
```

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
