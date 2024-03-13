修改说明: 这个库的修改目的是解决dbf数据和类型匹配不上造成的错误.以及使用jdk1.8编译的问题.
(Modification Description: The purpose of modifying this library is to address errors caused by mismatched data and types in dbf files, as well as issues related to using JDK 1.8 for compilation.)\

使用说明: 用jdk1.8编译即可.在dbeaver中直接删除已有的jar,配置这个jar.就可以避免-->因为dbf数据和类型匹配不上造成的错误,造成后续数据无法读取的问题.
(Usage Instructions: Compile using JDK 1.8. In DBeaver, directly delete the existing jar file and configure this modified jar file. This will prevent errors caused by mismatched data and types in dbf files, which can lead to subsequent data being unreadable.)



dans-dbf-lib
============

DANS DBF Library - Java classes to read, write and update DBF database files.

DESCRIPTION
===========

DANS DBF is a Java library for reading, writing and updating
the contents of old [DBF] \(dBase) databases.
It was produced for the [MIXED] project.
It is no longer maintained. You are however free to fork it, if you wish. 

DANS DBF requires Java 1.5, or later, and has no dependencies.

The following program demonstrates how the library is used.

```java
import nl.knaw.dans.common.dbflib.*;

import java.io.File;
import java.util.Iterator;
import java.util.List;

public class DansDbfDemo
{
  public static void main(String []args) throws Exception
  {
    File dbfFile = new File("src/test/resources/dbase3plus/cars/cars.dbf");
    Table table = new Table(dbfFile);
    table.open(IfNonExistent.ERROR);
    List<Field> fields = table.getFields();
    Iterator<Record> it = table.recordIterator();
    while (it.hasNext())
    {
      Record record = it.next();
      for (Field field: fields)
      {
        System.out.print(field.getName());
        System.out.print(": ");
        System.out.print(field.getType());
        System.out.print(": ");
        System.out.println(record.getTypedValue(field.getName()));
      }
    }
    table.close();
  }
}
```

The project does contain configuration for building a Maven site. However, it is currently broken. At sourceforge
there [may still be a version of this site](http://dans-dbf-lib.sourceforge.net/).


[DBF]: https://en.wikipedia.org/wiki/DBase
[MIXED]: http://www.dans.knaw.nl/en/projects/mixed
