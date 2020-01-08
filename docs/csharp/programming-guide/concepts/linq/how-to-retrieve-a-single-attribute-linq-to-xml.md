---
title: Jak pobrać pojedynczy atrybut (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 31b34bddc9e748b473641235402847991d444c39
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347494"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a>Jak pobrać pojedynczy atrybut (LINQ to XML) (C#)
W tym temacie wyjaśniono, jak pobrać pojedynczy atrybut elementu, pod nazwą atrybutu. Jest to przydatne w przypadku pisania wyrażeń zapytania, gdzie chcesz znaleźć element, który ma określony atrybut.  
  
 Metoda <xref:System.Xml.Linq.XElement.Attribute%2A> klasy <xref:System.Xml.Linq.XElement> zwraca <xref:System.Xml.Linq.XAttribute> o określonej nazwie.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano metodę <xref:System.Xml.Linq.XElement.Attribute%2A>.  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 Ten przykład umożliwia znalezienie wszystkich elementów podrzędnych w drzewie o nazwie `Phone`, a następnie znalezienie atrybutu o nazwie `type`.  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```output  
home  
work  
```  
  
## <a name="example"></a>Przykład  
 Jeśli chcesz pobrać wartość atrybutu, możesz go rzutować w taki sam sposób, jak w przypadku obiektów <xref:System.Xml.Linq.XElement>. Poniższy przykład ilustruje to.  
  
```csharp  
XElement cust = new XElement("PhoneNumbers",  
    new XElement("Phone",  
        new XAttribute("type", "home"),  
        "555-555-5555"),  
    new XElement("Phone",  
        new XAttribute("type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =   
    from el in cust.Descendants("Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute("type"));  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```output  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zawiera jawne Operatory rzutowania dla klasy <xref:System.Xml.Linq.XAttribute> do `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, `GUID?`.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje ten sam kod dla atrybutu, który znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement cust = new XElement(aw + "PhoneNumbers",  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "home"),  
        "555-555-5555"),  
    new XElement(aw + "Phone",  
        new XAttribute(aw + "type", "work"),  
        "555-555-6666")  
);  
IEnumerable<XElement> elList =  
    from el in cust.Descendants(aw + "Phone")  
    select el;  
foreach (XElement el in elList)  
    Console.WriteLine((string)el.Attribute(aw + "type"));  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```output  
home  
work  
```  
  
## <a name="see-also"></a>Zobacz także

- [Osie LINQ to XML (C#)](./linq-to-xml-axes-overview.md)
