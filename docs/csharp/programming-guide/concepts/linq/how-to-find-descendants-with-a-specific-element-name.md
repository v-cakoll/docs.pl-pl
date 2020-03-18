---
title: Jak znaleźć elementy podrzędne o nazwie określonego elementu (C#)
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: b3200a2fdf75dbf52079a2b3d27aa1a88d313406
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141083"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a>Jak znaleźć elementy podrzędne o nazwie określonego elementu (C#)
Czasami chcesz znaleźć wszystkie elementy podrzędne o określonej nazwie. Można napisać kod do iterate przez wszystkie elementy podrzędne, <xref:System.Xml.Linq.XContainer.Descendants%2A> ale łatwiej jest użyć osi.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak znaleźć elementy podrzędne na podstawie nazwy elementu.  
  
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
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono tę samą kwerendę dla języka XML, która znajduje się w obszarze nazw. Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
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
  
```output  
Some text that is broken up into multiple segments.  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
