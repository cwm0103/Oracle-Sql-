# Oracle-Sql-
Oracle 语句命令

-------------------------------查询锁表---------------------------

SELECT  lpad(' ',decode(l.xidusn ,0,3,0))||l.oracle_username User_name,
o.owner,o.object_name,o.object_type,s.sid,s.serial#
FROM v$locked_object l,dba_objects o,v$session s
WHERE l.object_id=o.object_id
AND l.session_id=s.sid
ORDER BY o.object_id,xidusn DESC;

-----------------------当其他人在使用时就锁住了---------------------

---------------------------------解锁--------------------------------
--alter system kill session 'sid, serial#'
--alter system kill session '18, 1033';
---------------------------------------------------------------------
