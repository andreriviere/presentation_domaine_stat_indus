# Divers

----

## Accéder aux données dans un autre schéma et dans une autre base
- pour récupérer les données d’une table dans un autre schéma situé dans la même base, il suffit d’indiquer le nom du schéma suivi du nom de la table : `nomSchéma.nomTable`
```sql
select * from ful4_rev2.tlb_orig;
```
- pour récupérer les données d’une table dans une autre base, il faut utiliser un DBLink (database link) : `nomSchéma.nomTable@nomDBLink`
```sql
select * from ful4_rev2.tlb_orig@dbl_rifus01.insee.fr;
```

----

## Récupérer les premières d'une table trié sur une variable donnée
à compléter
