---
title: 'Instrukcje: Pobierz wartość atrybutu (LINQ to XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 54ea4b532669ed2c615fcde02011fdd1228705a3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69592470"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Instrukcje: Pobierz wartość atrybutu (LINQ to XML) (C#)
W tym temacie pokazano, jak uzyskać wartość atrybutów. Istnieją dwa główne sposoby: Można rzutować <xref:System.Xml.Linq.XAttribute> na żądany typ; operator jawnej konwersji następnie konwertuje zawartość elementu lub atrybutu do określonego typu. Alternatywnie można użyć <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości. Jednak Rzutowanie jest ogólnie lepszym rozwiązaniem. Jeśli rzutowany atrybut na typ dopuszczający wartość null, kod jest łatwiejszy do zapisu podczas pobierania wartości atrybutu, który może lub nie istnieje. Przykłady tej techniki można znaleźć w temacie [How to: Pobierz wartość elementu (LINQ to XML) (C#).](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md)  
  
## <a name="example"></a>Przykład  
 Aby pobrać wartość atrybutu, wystarczy przerzutować <xref:System.Xml.Linq.XAttribute> obiekt na żądany typ.  
  
```csharp  
XElement root = new XElement("Root",  
                    new XAttribute("Attr", "abcde")  
                );  
Console.WriteLine(root);  
string str = (string)root.Attribute("Attr");  
Console.WriteLine(str);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
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
  
```  
abcde  
```  
  
## <a name="see-also"></a>Zobacz także

- [Osie LINQ to XML (C#)](./linq-to-xml-axes-overview.md)
