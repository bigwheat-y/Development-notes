## SQL语言

- 多表联查用户对应的

```sql
select tu.ID ID,
       tu.USER_NAME USER_NAME,
       tr.NAME ROLE,
       tm.TITLE MENU,
       tm.PERMISSION PERMISSION from TB_USER tu
                left join TB_USER_ROLE tur
                           on tu.ID = tur.USER_ID
                left join TB_ROLE tr
                           on tur.ROLE_ID = tr.ID
                left join TB_ROLE_MENU trm
                           on tr.ID = trm.ROLE_ID
                left join TB_MENU tm
                           on trm.MENU_ID = tm.ID
         where tu.USER_NAME = #{username}
```

