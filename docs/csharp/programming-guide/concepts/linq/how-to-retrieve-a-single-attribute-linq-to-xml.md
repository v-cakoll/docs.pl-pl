---
title: 'Instrukcje: Pobierz pojedynczy atrybut (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 4a1be51c7f0e89a8f211ae523eb102282bd9747b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592652"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a>Instrukcje: Pobierz pojedynczy atrybut (LINQ to XML) (C#)
W tym temacie wyjaśniono, jak pobrać pojedynczy atrybut elementu, pod nazwą atrybutu. Jest to przydatne w przypadku pisania wyrażeń zapytania, gdzie chcesz znaleźć element, który ma określony atrybut.  
  
 <xref:System.Xml.Linq.XElement.Attribute%2A> Metoda klasy<xref:System.Xml.Linq.XElement> zwraca z<xref:System.Xml.Linq.XAttribute> określoną nazwą.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zastosowano <xref:System.Xml.Linq.XElement.Attribute%2A> metodę.  
  
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
  
```  
home  
work  
```  
  
## <a name="example"></a>Przykład  
 Jeśli chcesz pobrać wartość atrybutu, możesz go rzutować, tak jak w przypadku <xref:System.Xml.Linq.XElement> obiektów. Poniższy przykład ilustruje to.  
  
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
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia jawne Operatory rzutowania dla <xref:System.Xml.Linq.XAttribute> klasy do `string` `int` `bool?` `bool` `int?`,, ,,`long?`,, ,,,`uint?` `uint` `long` `ulong`, `ulong?` ,`float?` ,,`TimeSpan`, ,`decimal?`, ,,`TimeSpan?`,, ,`GUID`i `float` `double` `DateTime` `double?` `decimal` `DateTime?`  `GUID?`.  
  
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
  
```  
home  
work  
```  
  
## <a name="see-also"></a>Zobacz także

- [Osie LINQ to XML (C#)](./linq-to-xml-axes-overview.md)
