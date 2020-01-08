---
title: Jak pobrać wartość atrybutu (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: d5b8bb3b5857b82a61367953b8e1cd63bea90beb
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347433"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Jak pobrać wartość atrybutu (LINQ to XML) (C#)
W tym temacie pokazano, jak uzyskać wartość atrybutów. Istnieją dwa podstawowe sposoby: można rzutować <xref:System.Xml.Linq.XAttribute> na żądany typ; operator jawnej konwersji konwertuje zawartość elementu lub atrybutu do określonego typu. Alternatywnie możesz użyć właściwości <xref:System.Xml.Linq.XAttribute.Value%2A>. Jednak Rzutowanie jest ogólnie lepszym rozwiązaniem. Jeśli rzutowany atrybut na typ dopuszczający wartość null, kod jest łatwiejszy do zapisu podczas pobierania wartości atrybutu, który może lub nie istnieje. Aby zapoznać się z przykładami tej techniki, zobacz [jak pobrać wartość elementu (LINQ to XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Przykład  
 Aby pobrać wartość atrybutu, należy po prostu rzutować obiekt <xref:System.Xml.Linq.XAttribute> na żądany typ.  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```output  
<Root Attr="abcde" />  
abcde  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak pobrać wartość atrybutu, gdzie atrybut znajduje się w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw —C#omówienie (LINQ to XML) ()](namespaces-overview-linq-to-xml.md).  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XElement root = new XElement(aw + "Root",  
                    new XAttribute(aw + "Attr", "abcde")  
                );  
string str = (string)root.Attribute(aw + "Attr");  
Console.WriteLine(str);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```output  
abcde  
```  
  
## <a name="see-also"></a>Zobacz także

- [Osie LINQ to XML (C#)](./linq-to-xml-axes-overview.md)
