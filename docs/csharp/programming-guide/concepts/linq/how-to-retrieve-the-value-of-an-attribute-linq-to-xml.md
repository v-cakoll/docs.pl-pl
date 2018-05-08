---
title: 'Porady: pobieranie wartości atrybutu (LINQ do XML) (C#)'
ms.date: 07/20/2015
ms.assetid: 817bbe89-5979-4234-bf0c-46f63692ac8c
ms.openlocfilehash: 224ba9ba47d68afd7c29d0f33fe20d290d0b5ef5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-the-value-of-an-attribute-linq-to-xml-c"></a>Porady: pobieranie wartości atrybutu (LINQ do XML) (C#)
W tym temacie przedstawiono sposób uzyskiwania wartości atrybutów. Istnieją dwa sposoby: można rzutować <xref:System.Xml.Linq.XAttribute> na żądany typ.; operator jawnej konwersji następnie konwertuje zawartość elementu lub atrybutu do określonego typu. Alternatywnie można użyć <xref:System.Xml.Linq.XAttribute.Value%2A> właściwości. Rzutowanie jest jednak ogólnie lepszym rozwiązaniem. Jeśli rzutowania atrybut do typu dopuszczającego wartość null, kod jest łatwiejsze do zapisania podczas pobierania wartości atrybutu, który może lub nie istnieje. Przykłady tej metody, zobacz [porady: pobieranie wartości elementu (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md).  
  
## <a name="example"></a>Przykład  
 Można pobrać wartości atrybutu, możesz po prostu rzutowania <xref:System.Xml.Linq.XAttribute> obiektu do żądanego typu.  
  
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
 Poniższy przykład pokazuje, jak można pobrać wartości atrybutu którym atrybut jest w przestrzeni nazw. Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do osi XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
