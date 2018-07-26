---
title: 'Porady: tworzenie zapytań dotyczących LINQ to XML przy użyciu XPath (C#)'
ms.date: 07/20/2015
ms.assetid: ee5af263-4ab1-45e5-b792-33a3221b426d
ms.openlocfilehash: a02149719afa19350a9baf15c41bd3548daa1344
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37959858"
---
# <a name="how-to-query-linq-to-xml-using-xpath-c"></a>Porady: tworzenie zapytań dotyczących LINQ to XML przy użyciu XPath (C#)
W tym temacie przedstawiono metody rozszerzenia, które pozwalają na wykonywanie zapytań drzewa XML przy użyciu wyrażenie XPath. Aby uzyskać szczegółowe informacje o używaniu tych metod rozszerzenia, zobacz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
 Jeśli nie masz bardzo powód do wykonywania zapytań przy użyciu XPath, takie jak zwiększone użycie starszego kodu, za pomocą LINQ to XML przy użyciu XPath nie jest zalecane. Zapytania XPath nie będzie wykonywać także [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy mały drzewa XML i używa <xref:System.Xml.XPath.Extensions.XPathSelectElements%2A> wybrać zestaw elementów.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", 1),  
    new XElement("Child1", 2),  
    new XElement("Child1", 3),  
    new XElement("Child2", 4),  
    new XElement("Child2", 5),  
    new XElement("Child2", 6)  
);  
IEnumerable<XElement> list = root.XPathSelectElements("./Child2");  
foreach (XElement el in list)  
    Console.WriteLine(el);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Child2>4</Child2>  
<Child2>5</Child2>  
<Child2>6</Child2>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Zaawansowane techniki zapytań (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
