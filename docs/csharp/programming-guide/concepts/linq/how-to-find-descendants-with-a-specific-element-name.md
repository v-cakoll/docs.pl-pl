---
title: "Porady: znajdowanie elementów podrzędnych o nazwie określonego elementu (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b1cc45f07accd7ae6dcc530f0fd5a9078bce949d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a>Porady: znajdowanie elementów podrzędnych o nazwie określonego elementu (C#)
Czasami chcesz znaleźć wszystkich elementów podrzędnych o określonej nazwie. Można napisać kod, aby wykonać iterację wszystkich elementów podrzędnych, ale jest łatwiejsze w <xref:System.Xml.Linq.XContainer.Descendants%2A> osi.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można znaleźć elementów podrzędnych na podstawie nazwy elementu.  
  
```csharp  
XElement root = XElement.Parse(@"<root>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
IEnumerable<string> textSegs =  
    from seg in root.Descendants("t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
```csharp  
XElement root = XElement.Parse(@"<root xmlns='http://www.adatum.com'>  
  <para>  
    <r>  
      <t>Some text </t>  
    </r>  
    <n>  
      <r>  
        <t>that is broken up into </t>  
      </r>  
    </n>  
    <n>  
      <r>  
        <t>multiple segments.</t>  
      </r>  
    </n>  
  </para>  
</root>");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<string> textSegs =  
    from seg in root.Descendants(ad + "t")  
    select (string)seg;  
  
string str = textSegs.Aggregate(new StringBuilder(),  
    (sb, i) => sb.Append(i),  
    sp => sp.ToString()  
);  
  
Console.WriteLine(str);  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XContainer.Descendants%2A>  
 [Podstawowe zapytania (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/basic-queries-linq-to-xml.md)
