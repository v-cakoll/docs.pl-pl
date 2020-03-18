---
title: Jak pobrać pojedynczy atrybut (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 1b6b07b9-933f-47e9-874e-e790cab49dc5
ms.openlocfilehash: 830a7be24702b6037ac62471060fbe49d8ded598
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168716"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-c"></a>Jak pobrać pojedynczy atrybut (LINQ do XML) (C#)
W tym temacie wyjaśniono, jak pobrać pojedynczy atrybut elementu, biorąc pod uwagę nazwę atrybutu. Jest to przydatne do pisania wyrażeń kwerendy, gdzie chcesz znaleźć element, który ma określony atrybut.  
  
 Metoda <xref:System.Xml.Linq.XElement.Attribute%2A> <xref:System.Xml.Linq.XElement> klasy zwraca <xref:System.Xml.Linq.XAttribute> o określonej nazwie.  
  
## <a name="example"></a>Przykład  
 W poniższym <xref:System.Xml.Linq.XElement.Attribute%2A> przykładzie użyto metody.  
  
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
  
 W tym przykładzie znajduje wszystkie elementy `Phone`podrzędne w `type`drzewie o nazwie , a następnie znajduje atrybut o nazwie .  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```output  
home  
work  
```  
  
## <a name="example"></a>Przykład  
 Jeśli chcesz pobrać wartość atrybutu, możesz rzutować go, tak <xref:System.Xml.Linq.XElement> jak w przypadku obiektów. Poniższy przykład pokazuje to.  
  
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
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zapewnia wyraźne odlewane operatory <xref:System.Xml.Linq.XAttribute> dla `uint`klasy `uint?` `long`do `long?` `ulong` `ulong?` `float` `float?` `double` `double?` `decimal` `decimal?` `DateTime` `DateTime?` `bool?` `int` `int?` `TimeSpan` `TimeSpan?` `GUID` `GUID?`, `bool`, , , , , , , , , , , , , , , , i . `string`  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono ten sam kod atrybutu, który znajduje się w obszarze nazw. Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
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
  
## <a name="see-also"></a>Zobacz też

- [LINQ do osi XML (C#)](./linq-to-xml-axes-overview.md)
