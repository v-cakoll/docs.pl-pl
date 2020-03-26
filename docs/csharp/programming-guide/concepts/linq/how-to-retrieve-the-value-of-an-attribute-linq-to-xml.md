---
title: Jak pobrać wartość atrybutu (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 212ad3bb3097e7e2c76da8f165011b181f329d4c
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249197"
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Jak pobrać wartość atrybutu (LINQ do XML) (C#)
W tym temacie pokazano, jak uzyskać wartość atrybutów. Istnieją dwa główne sposoby: <xref:System.Xml.Linq.XAttribute> można rzucić do żądanego typu; operator konwersji jawne następnie konwertuje zawartość elementu lub atrybutu do określonego typu. Goście mogą również skorzystać <xref:System.Xml.Linq.XAttribute.Value%2A> z obiektu. Jednak odlewanie jest na ogół lepszym podejściem. Jeśli rzutujesz atrybut na typ wartości możliwej do wartości null, kod jest prostszy do zapisania podczas pobierania wartości atrybutu, który może lub nie może istnieć. Aby zapoznać się z przykładami tej techniki, zobacz [Jak pobrać wartość elementu (LINQ do XML) (C#)](./how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Przykład  
 Aby pobrać wartość atrybutu, wystarczy rzutować <xref:System.Xml.Linq.XAttribute> obiekt do żądanego typu.  
  
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
 W poniższym przykładzie pokazano, jak pobrać wartość atrybutu, w którym atrybut znajduje się w obszarze nazw. Aby uzyskać więcej informacji, zobacz [Omówienie obszarów nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
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

- [Osie LINQ do XML (C#)](./linq-to-xml-axes-overview.md)
