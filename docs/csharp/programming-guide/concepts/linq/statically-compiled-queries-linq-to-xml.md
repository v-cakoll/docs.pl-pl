---
title: Skompilowane statycznie zapytania (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: 842f8c1c2fa07e1658992e94e5163222f38f80ba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514793"
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a>Skompilowane statycznie zapytania (LINQ to XML) (C#)
Jedną z najważniejszych wydajności korzyści programu LINQ to XML, w przeciwieństwie do <xref:System.Xml.XmlDocument>, jest statycznie są zapytania w LINQ to XML kompilowane, dlatego należy interpretować zapytania XPath w czasie wykonywania. Ta funkcja jest wbudowana w LINQ to XML, dzięki czemu nie trzeba wykonać dodatkowe kroki, aby z niej korzystać, ale warto zrozumieć różnicę, wybierając między te dwie technologie. W tym temacie opisano różnicę.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Statycznie zapytania skompilowane vs. XPath  
 Poniższy przykład pokazuje, jak można pobrać elementów podrzędnych o określonej nazwie i z atrybutem z określoną wartością.  
  
 Równoważne wyrażenie XPath jest następująca:  
  
```  
//Address[@Type='Shipping']  
```  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    from el in po.Descendants("Address")  
    where (string)el.Attribute("Type") == "Shipping"  
    select el;  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Wyrażenia zapytania w tym przykładzie jest ponownie zapisywany przez kompilator, aby składni zapytania oparte na metodzie. Poniższy przykład, który został napisany w składni zapytania oparte na metodzie, jest taki sam jak poprzedni:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <xref:System.Linq.Enumerable.Where%2A> Metoda jest metodą rozszerzenia. Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Ponieważ <xref:System.Linq.Enumerable.Where%2A> jest metodą rozszerzenia, powyższe zapytania jest kompilowany tak, jakby zostały napisane w następujący sposób:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 Ten przykład generuje dokładnie te same wyniki poprzednich dwóch przykładach. Obrazuje to fakt, że zapytania skutecznie są kompilowane do wywołania metody statycznie połączone. W połączeniu z semantyką odroczonego wykonania iteratorów, zwiększa wydajność. Aby uzyskać więcej informacji dotyczących semantyki odroczonego wykonania iteratorów, zobacz [wykonanie odroczone i obliczanie z opóźnieniem w LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
>  Te przykłady są reprezentatywne kodu, który może zapisać kompilator. Rzeczywiste wdrożenie może różnić się nieco od tych przykładach, ale wydajność będą takie same lub podobne do tych przykładów.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>Wykonywanie wyrażeń XPath z parametrem XmlDocument  
 W poniższym przykładzie użyto <xref:System.Xml.XmlDocument> wykonywać te same wyniki poprzednich przykładach:  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 Ta kwerenda zwraca ten sam wynik jako przykłady, które używają programu LINQ to XML; Jedyna różnica polega na czy LINQ to XML wcięcia XML drukowane, podczas gdy <xref:System.Xml.XmlDocument> nie.  
  
 Jednak <xref:System.Xml.XmlDocument> podejście zazwyczaj nie wykonuje oraz LINQ to XML, ponieważ <xref:System.Xml.XmlNode.SelectNodes%2A> metody należy wykonać następujące czynności wewnętrznie za każdym razem, gdy jest to:  
  
-   Analizuje ciąg, który zawiera wyrażenie XPath podzielenie ciągu na tokeny.  
  
-   Sprawdza poprawność tokenów, aby upewnić się, że wyrażenie XPath jest nieprawidłowy.  
  
-   Tłumaczy je wyrażenia do drzewa wyrażenie wewnętrznego.  
  
-   Iterację węzłów, odpowiednio Wybieranie węzłów do zestawu wyników na podstawie oceny wyrażenia.  
  
 Jest to znacznie więcej niż pracy wykonanej przez odpowiednie zapytaniu składnika LINQ to XML. Różnica dotyczącego wydajności różni się dla różnych typów kwerend, ale w ogólne LINQ to XML zapytania są mniej pracy i w związku z tym mają lepszą wydajność, niż oceny wyrażeń XPath przy użyciu <xref:System.Xml.XmlDocument>.  
  
## <a name="see-also"></a>Zobacz także

- [Wydajność (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
