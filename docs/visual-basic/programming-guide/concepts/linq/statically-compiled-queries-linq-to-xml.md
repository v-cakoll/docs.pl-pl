---
title: Skompilowane statycznie zapytania (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: ff708dd14d27b34be797f1630dabe27a56c5a219
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834910"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a>Skompilowane statycznie zapytania (LINQ to XML) (Visual Basic)
Jedną z najważniejszych wydajności korzyści programu LINQ to XML, w przeciwieństwie do <xref:System.Xml.XmlDocument>, jest statycznie są zapytania w LINQ to XML kompilowane, dlatego należy interpretować zapytania XPath w czasie wykonywania. Ta funkcja jest wbudowana w LINQ to XML, dzięki czemu nie trzeba wykonać dodatkowe kroki, aby z niej korzystać, ale warto zrozumieć różnicę, wybierając między te dwie technologie. W tym temacie opisano różnicę.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Statycznie zapytania skompilowane vs. XPath  
 Poniższy przykład pokazuje, jak można pobrać elementów podrzędnych o określonej nazwie i z atrybutem z określoną wartością.  
  
 Równoważne wyrażenie XPath jest następująca:  
  
```  
//Address[@Type='Shipping']  
```  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = From el In po.Descendants("Address")  
            Where el.@Type = "Shipping"  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Wyrażenia zapytania w tym przykładzie jest ponownie zapisywany przez kompilator, aby składni zapytania oparte na metodzie. Poniższy przykład, który został napisany w składni zapytania oparte na metodzie, jest taki sam jak poprzedni:  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next   
```  
  
 <xref:System.Linq.Enumerable.Where%2A> Metoda jest metodą rozszerzenia. Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Ponieważ <xref:System.Linq.Enumerable.Where%2A> jest metodą rozszerzenia, powyższe zapytania jest kompilowany tak, jakby zostały napisane w następujący sposób:  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 Ten przykład generuje dokładnie te same wyniki poprzednich dwóch przykładach. Obrazuje to fakt, że zapytania skutecznie są kompilowane do wywołania metody statycznie połączone. W połączeniu z semantyką odroczonego wykonania iteratorów, zwiększa wydajność. Aby uzyskać więcej informacji dotyczących semantyki odroczonego wykonania iteratorów, zobacz [wykonanie odroczone i obliczanie z opóźnieniem w LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
>  Te przykłady są reprezentatywne kodu, który może zapisać kompilator. Rzeczywiste wdrożenie może różnić się nieco od tych przykładach, ale wydajność będą takie same lub podobne do tych przykładów.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>Wykonywanie wyrażeń XPath z parametrem XmlDocument  
 W poniższym przykładzie użyto <xref:System.Xml.XmlDocument> wykonywać te same wyniki poprzednich przykładach:  
  
```vb  
Dim reader = Xml.XmlReader.Create("PurchaseOrders.xml")  
Dim doc As New Xml.XmlDocument()  
doc.Load(reader)  
Dim nl As Xml.XmlNodeList = doc.SelectNodes(".//Address[@Type='Shipping']")  
For Each n As Xml.XmlNode In nl  
    Console.WriteLine(n.OuterXml)  
Next  
reader.Close()  
```  
  
 Ta kwerenda zwraca ten sam wynik jako przykłady, które używają programu LINQ to XML; Jedyna różnica polega na czy LINQ to XML wcięcia XML drukowane, podczas gdy <xref:System.Xml.XmlDocument> nie.  
  
 Jednak <xref:System.Xml.XmlDocument> podejście zazwyczaj nie wykonuje oraz LINQ to XML, ponieważ <xref:System.Xml.XmlNode.SelectNodes%2A> metody należy wykonać następujące czynności wewnętrznie za każdym razem, gdy jest to:  
  
-   Analizuje ciąg, który zawiera wyrażenie XPath podzielenie ciągu na tokeny.  
  
-   Sprawdza poprawność tokenów, aby upewnić się, że wyrażenie XPath jest nieprawidłowy.  
  
-   Tłumaczy je wyrażenia do drzewa wyrażenie wewnętrznego.  
  
-   Iterację węzłów, odpowiednio Wybieranie węzłów do zestawu wyników na podstawie oceny wyrażenia.  
  
 Jest to znacznie więcej niż pracy wykonanej przez odpowiednie zapytaniu składnika LINQ to XML. Różnica dotyczącego wydajności różni się dla różnych typów kwerend, ale w ogólne LINQ to XML zapytania są mniej pracy i w związku z tym mają lepszą wydajność, niż oceny wyrażeń XPath przy użyciu <xref:System.Xml.XmlDocument>.  
  
## <a name="see-also"></a>Zobacz także

- [Wydajność (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
