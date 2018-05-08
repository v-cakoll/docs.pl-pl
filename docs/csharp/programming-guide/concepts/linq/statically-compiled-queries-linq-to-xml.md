---
title: Statycznie skompilowane zapytania (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: 3bf558fe-0705-479d-86d4-00188f5fcf9c
ms.openlocfilehash: b429a5711be942349365019fc71291f78fccc652
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="statically-compiled-queries-linq-to-xml-c"></a>Statycznie skompilowane zapytania (LINQ do XML) (C#)
Jedną z najważniejszych wydajności przynosi korzyści LINQ do XML, w przeciwieństwie do <xref:System.Xml.XmlDocument>, statycznie są kwerendy w składniku LINQ to XML kompilowania, podczas gdy kwerendy XPath muszą być interpretowane w czasie wykonywania. Ta funkcja jest wbudowana w LINQ do XML, więc nie trzeba wykonywać dodatkowe czynności, aby móc korzystać z niego, ale jest przydatne rozróżnienie, gdy Wybieranie między te dwie technologie. W tym temacie objaśniono różnicę.  
  
## <a name="statically-compiled-queries-vs-xpath"></a>Statycznie vs skompilowane zapytania. XPath  
 Poniższy przykład pokazuje, jak można uzyskać elementów podrzędnych o określonej nazwie i z atrybutem o określonej wartości.  
  
 Poniżej przedstawiono równoważne wyrażenie XPath:  
  
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
  
 Wyrażenia zapytania w tym przykładzie są ponownie zapisywane przez kompilator do składni zapytania oparte na metodzie. Poniższy przykład, który został napisany w składni zapytania oparte na metodzie, jest taki sam jak poprzedni:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    po  
    .Descendants("Address")  
    .Where(el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 <xref:System.Linq.Enumerable.Where%2A> Metoda jest metodą rozszerzenia. Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Ponieważ <xref:System.Linq.Enumerable.Where%2A> jest metodą rozszerzenia zapytania powyżej jest kompilowana tak, jakby były zapisywane w następujący sposób:  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
IEnumerable<XElement> list1 =  
    System.Linq.Enumerable.Where(  
        po.Descendants("Address"),  
        el => (string)el.Attribute("Type") == "Shipping");  
  
foreach (XElement el in list1)  
    Console.WriteLine(el);  
```  
  
 W tym przykładzie powoduje dokładnie takie same wyniki jak poprzednich dwóch przykładach. Przedstawiono to fakt skutecznie kompilowane zapytania do wywołania metody statycznie połączone. Tym połączeniu z semantykę wykonanie odroczone Iteratory, poprawia wydajność. Aby uzyskać więcej informacji na temat semantyki wykonanie odroczone Iteratory, zobacz [termin odroczonego wykonania i obliczanie leniwe w składniku LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
> [!NOTE]
>  Te przykłady są reprezentatywne kodu, który może zapisać kompilatora. Rzeczywista implementacja może różnić się nieznacznie w tych przykładach, ale wydajność będą takie same lub podobne do tych przykładów.  
  
## <a name="executing-xpath-expressions-with-xmldocument"></a>Wykonywania wyrażenia XPath z parametrem XmlDocument  
 W poniższym przykładzie użyto <xref:System.Xml.XmlDocument> na takie same wyniki jak w poprzednich przykładach:  
  
```csharp  
XmlReader reader = XmlReader.Create("PurchaseOrders.xml");  
XmlDocument doc = new XmlDocument();  
doc.Load(reader);  
XmlNodeList nl = doc.SelectNodes(".//Address[@Type='Shipping']");  
foreach (XmlNode n in nl)  
    Console.WriteLine(n.OuterXml);  
reader.Close();  
```  
  
 Ta kwerenda zwraca tych samych danych wyjściowych jako przykłady, które używają LINQ do XML; Jedyna różnica polega na czy LINQ do XML wcięcia drukowanymi XML, podczas gdy <xref:System.Xml.XmlDocument> nie.  
  
 Jednak <xref:System.Xml.XmlDocument> podejście zazwyczaj wykonuje oraz LINQ do XML, ponieważ <xref:System.Xml.XmlNode.SelectNodes%2A> metody musi wykonać następujące czynności wewnętrznie za każdym razem, gdy jest to:  
  
-   Analizuje ciąg, który zawiera wyrażenie XPath, dzielenie ciąg na tokeny.  
  
-   Sprawdza poprawność tokenów, aby upewnić się, że wyrażenie XPath jest nieprawidłowa.  
  
-   Tłumaczy go wyrażenia na drzewo wyrażenia wewnętrznego.  
  
-   Iteruje węzłów, odpowiednio zaznaczania węzłów w zestawie wyników na podstawie oceny wyrażenia.  
  
 Jest to znacznie więcej niż pracy wykonanej przez odpowiednie zapytania składnika LINQ to XML. Różnice dotyczące wydajności może być różna dla różnych typów kwerend, ale w ogólne LINQ do XML zapytania mniej pracy i w związku z tym działać lepiej niż obliczenia za pomocą wyrażenia XPath <xref:System.Xml.XmlDocument>.  
  
## <a name="see-also"></a>Zobacz też  
 [Wydajność (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
