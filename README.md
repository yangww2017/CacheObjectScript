English description

1.Application scenarios：

The hospital needs to summarize the data of each department to the hospital headquarters, but after the summary, it is found that the dictionaries used by each department are not unified, and the existing dictionaries in the table need to be replaced by the dictionaries formulated by the hospital. For example, the gender Dictionary of a department uses 0 / 1 / 2 to represent all kinds of genders, and the gender Dictionary of B department uses f / M / O to represent all kinds of genders, but now the hospital requires all gender dictionaries to save the gender information of female / male / other, so it is necessary to replace the original gender dictionary with a new one. This is just a use scenario. In the future, we can consider the design and implementation idea of this project when we need to compare dictionaries.

2.basic environment:
IRIS for Windows (x86-64) 2020.1 (Build 215U)

3.Deployment steps：

1)、Create a specified mapping table. The table name is the same as the data table name (in this example, the table name is patinfo). The key field holds the name of the field in the table that needs to be compared, and the value field holds the name of the dictionary mapping table。


2)、Create a dictionary mapping table. The key value in this table is the original dictionary value, and the value is the corresponding value of the new dictionary. In this example, the gender comparison relationship table "sextable" and the occupation comparison relationship table "professional table" are listed. At present, the comparison between the original dictionary and the new dictionary needs to be carried out manually. Later, we can try to improve it to program execution。


Note: the lookuptable data in the example can be imported directly using the attached file(PatInfo.xml/ProfessionTable.xml/SexTable.xml)

3)、Prepare the test data, execute the following SQL statement, create the table patinfo and insert the test data 
create table PatInfo(
name varchar(20),
sex varchar(20),
age varchar(20),
profession varchar(20))

insert into PatInfo(name,sex,age,profession) values('zhangsan','1','16','002');
insert into PatInfo(name,sex,age,profession) values('lisi','1','36','001');
insert into PatInfo(name,sex,age,profession) values('wangwu','2','26','003');
insert into PatInfo(name,sex,age,profession) values('zhaoming','F','23','01002');
insert into PatInfo(name,sex,age,profession) values('zhangliu','M','45','01003');
insert into PatInfo(name,sex,age,profession) values('cailun','O','45','001')

4)、Import run code(DEMO.xml) and execute method
Note: Make sure that lookuptable and this code are in the same namespace
Do ##class(DEMO.DictNormalize).Normalize("PatInfo")

5)、Verify whether the data are compared successfully

More details please refer to README.docx






















中文描述说明：

应用场景：

现场需要将各个科室部门内的数据统一汇总到医院总部，但是汇总后发现各个科室使用的字典并不统一，需要将表中的现存的字典统一更换为医院制定字典。例如：A科室中人员的性别字典使用0/1/2表示各种性别，B科室中性别字典使用F/M/O表示各种性别，但是现在医院要求所有性别字典保存Female/Male/Other性别信息，此时就需要替换原有的性别字典为新用字典。当初，此处只是列举了一个使用场景，未来有多个需要对照字典的工作都可以考虑此项目的设计和实现思想。

基本环境：
IRIS for Windows (x86-64) 2020.1 (Build 215U)

部署步骤：

1)、建立数据对照表，表名与数据表名相同（此样例中表名为：PatInfo），其中Key字段保存该表中需要进行对照的字段名称，Value字段保存字典对照表名。


2)、建立字典对照表，此表中的Key值为原字典值，Value为新字典对应值，此样例中列举性别对照关系SexTable和职业对照关系ProfessionTable，在初始版本中此工作目前需要人工对照映射关系，后期可以改进为程序对照。


注：样例中的LookupTable数据可以使用附属文件直接导入(PatInfo.xml/ProfessionTable.xml/SexTable.xml)

3)、准备测试数据，执行以下SQL语句，建立表PatInfo并插入测试数据
create table PatInfo(
name varchar(20),
sex varchar(20),
age varchar(20),
profession varchar(20))

insert into PatInfo(name,sex,age,profession) values('zhangsan','1','16','002');
insert into PatInfo(name,sex,age,profession) values('lisi','1','36','001');
insert into PatInfo(name,sex,age,profession) values('wangwu','2','26','003');
insert into PatInfo(name,sex,age,profession) values('zhaoming','F','23','01002');
insert into PatInfo(name,sex,age,profession) values('zhangliu','M','45','01003');
insert into PatInfo(name,sex,age,profession) values('cailun','O','45','001')

4)、导入运行代码并执行方法
注：请保证lookupTable和此代码放在同一个命名空间
Do ##class(DEMO.DictNormalize).Normalize("PatInfo")

5)、验证数据是否对照成功

更多详情信息请参考：README.docx

