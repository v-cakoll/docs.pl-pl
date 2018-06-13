---
title: Statycznie skompilowane zapytania (LINQ do XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: f6230864eb125d493d38f85adf5806c80a31c910
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655300"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a>Statycznie skompilowane zapytania (LINQ do XML) (Visual Basic)
Jedną z najważniejszych wydajności przynosi korzyści LINQ do XML, w przeciwieństwie do <xref:System.Xml.XmlDocument>, statycznie są kwerendy w składniku LINQ to XML kompilowania, podczas gdy kwerendy XPath muszą być interpretowane w czasie wykonywania. Ta funkcja jest wbudowana w LINQ do XML, więc nie trzeba wykonywać dodatkowe czynności, aby móc korzystać z niego, ale jest przydatne rozróżnienie, gdy Wybieranie między te dwie technologie. W tym temacie objaśniono różnicę.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Statycznie vs skompilowane zapytania. XPath  
 Poniższy przykład pokazuje, jak można uzyskać elementów podrzędnych o określonej nazwie i z atrybutem o określonej wartości.  
  
 Poniżej przedstawiono równoważne wyrażenie XPath:  
  
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
  
 Wyrażenia zapytania w tym przykładzie są ponownie zapisywane przez kompilator do składni zapytania oparte na metodzie. Poniższy przykład, który został napisany w składni zapytania oparte na metodzie, jest taki sam jak poprzedni:  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next   
```  
  
 <xref:System.Linq.Enumerable.Where%2A> Metoda jest metodą rozszerzenia. Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Ponieważ <xref:System.Linq.Enumerable.Where%2A> jest metodą rozszerzenia zapytania powyżej jest kompilowana tak, jakby były zapisywane w następujący sposób:  
  
```vb  
Dim po = XDocument.Load("PurchaseOrders.xml")  
  
Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")  
  
For Each el In list1  
    Console.WriteLine(el)  
Next  
```  
  
 W tym przykładzie powoduje dokładnie takie same wyniki jak poprzednich dwóch przykładach. Przedstawiono to fakt skutecznie kompilowane zapytania do wywołania metody statycznie połączone. Tym połączeniu z semantykę wykonanie odroczone Iteratory, poprawia wydajność. Aby uzyskać więcej informacji na temat semantyki wykonanie odroczone Iteratory, zobacz [termin odroczonego wykonania i obliczanie leniwe w składniku LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
>  Te przykłady są reprezentatywne kodu, który może zapisać kompilatora. Rzeczywista implementacja może różnić się nieznacznie w tych przykładach, ale wydajność będą takie same lub podobne do tych przykładów.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>Wykonywania wyrażenia XPath z parametrem XmlDocument  
 W poniższym przykładzie użyto <xref:System.Xml.XmlDocument> na takie same wyniki jak w poprzednich przykładach:  
  
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
  
 Ta kwerenda zwraca tych samych danych wyjściowych jako przykłady, które używają LINQ do XML; Jedyna różnica polega na czy LINQ do XML wcięcia drukowanymi XML, podczas gdy <xref:System.Xml.XmlDocument> nie.  
  
 Jednak <xref:System.Xml.XmlDocument> podejście zazwyczaj wykonuje oraz LINQ do XML, ponieważ <xref:System.Xml.XmlNode.SelectNodes%2A> metody musi wykonać następujące czynności wewnętrznie za każdym razem, gdy jest to:  
  
-   Analizuje ciąg, który zawiera wyrażenie XPath, dzielenie ciąg na tokeny.  
  
-   Sprawdza poprawność tokenów, aby upewnić się, że wyrażenie XPath jest nieprawidłowa.  
  
-   Tłumaczy go wyrażenia na drzewo wyrażenia wewnętrznego.  
  
-   Iteruje węzłów, odpowiednio zaznaczania węzłów w zestawie wyników na podstawie oceny wyrażenia.  
  
 Jest to znacznie więcej niż pracy wykonanej przez odpowiednie zapytania składnika LINQ to XML. Różnice dotyczące wydajności może być różna dla różnych typów kwerend, ale w ogólne LINQ do XML zapytania mniej pracy i w związku z tym działać lepiej niż obliczenia za pomocą wyrażenia XPath <xref:System.Xml.XmlDocument>.  
  
## <a name="see-also"></a>Zobacz też  
 [Wydajność (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
