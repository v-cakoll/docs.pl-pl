---
title: 'Instrukcje: Wyszukiwanie elementów potomnych o określonej nazwie elementu (C#)'
ms.date: 07/20/2015
ms.assetid: f684da20-bee9-47f5-9607-7e3fd7e67470
ms.openlocfilehash: c54b3c6a01459781b8ed9d5495bf9eb8937363fa
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66486756"
---
# <a name="how-to-find-descendants-with-a-specific-element-name-c"></a>Instrukcje: Wyszukiwanie elementów potomnych o określonej nazwie elementu (C#)
Czasami chcesz znaleźć wszystkie elementy podrzędne o określonej nazwie. Można napisać kod, aby wykonać iterację przez wszystkie elementy podrzędne, ale jest łatwiejszy w obsłudze <xref:System.Xml.Linq.XContainer.Descendants%2A> osi.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak można znaleźć elementy podrzędne na podstawie nazwy elementu.  
  
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
 Poniższy przykład pokazuje tego samego zapytania w formacie XML, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XContainer.Descendants%2A>
