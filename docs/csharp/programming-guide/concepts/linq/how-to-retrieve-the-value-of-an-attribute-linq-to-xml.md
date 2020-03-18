---
title: Jak pobrać wartość atrybutu (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: d5b8bb3b5857b82a61367953b8e1cd63bea90beb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347433"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Jak pobrać wartość atrybutu (LINQ do XML) (C#)
W tym temacie pokazano, jak uzyskać wartość atrybutów. Istnieją dwa główne sposoby: Można <xref:System.Xml.Linq.XAttribute> rzucić do żądanego typu; operator konwersji jawnej następnie konwertuje zawartość elementu lub atrybutu na określony typ. Alternatywnie można użyć <xref:System.Xml.Linq.XAttribute.Value%2A> tej właściwości. Jednak casting jest na ogół lepszym podejściem. Jeśli rzutowane atrybut udopuszczający typ, kod jest prostszy do zapisu podczas pobierania wartości atrybutu, który może lub nie może istnieć. Przykłady tej techniki można znaleźć w [części Jak pobrać wartość elementu (LINQ do XML) (C#).](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md)  
  
## <a name="example"></a>Przykład  
 Aby pobrać wartość atrybutu, wystarczy <xref:System.Xml.Linq.XAttribute> rzutować obiekt do żądanego typu.  
  
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
 W poniższym przykładzie pokazano, jak pobrać wartość atrybutu, w którym atrybut znajduje się w obszarze nazw. Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
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
  
## <a name="see-also"></a>Zobacz też

- [LINQ do osi XML (C#)](./linq-to-xml-axes-overview.md)
