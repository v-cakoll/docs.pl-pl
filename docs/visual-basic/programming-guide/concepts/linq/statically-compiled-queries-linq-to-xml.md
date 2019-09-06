---
title: Zapytania skompilowane statycznie (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3f4825c7-c3b0-48da-ba4e-8e97fb2a2f34
ms.openlocfilehash: ed701f57821c18f4cfa75a3bb7cd5a652ab384d8
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373736"
---
# <a name="statically-compiled-queries-linq-to-xml-visual-basic"></a>Zapytania skompilowane statycznie (LINQ to XML) (Visual Basic)

Jedną z najważniejszych korzyści związanych z wydajnością LINQ to XML, w przeciwieństwie do <xref:System.Xml.XmlDocument>programu, jest to, że zapytania w LINQ to XML są kompilowane statycznie, podczas gdy zapytania XPath muszą być interpretowane w czasie wykonywania. Ta funkcja jest wbudowana w LINQ to XML, więc nie trzeba wykonywać dodatkowych czynności, aby korzystać z nich, ale warto zrozumieć rozróżnienie podczas wybierania dwóch technologii. W tym temacie opisano różnicę.

## <a name="statically-compiled-queries-vs-xpath"></a>Zapytania skompilowane statycznie a XPath

Poniższy przykład pokazuje, jak uzyskać elementy podrzędne o określonej nazwie i z atrybutem o określonej wartości.

Poniżej znajduje się równoważne wyrażenie XPath:

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

Wyrażenie zapytania w tym przykładzie jest ponownie zapisywane przez kompilator do składni zapytania opartej na metodzie. Poniższy przykład, który został zapisany w składni zapytania opartej na metodzie, daje takie same wyniki jak poprzedni:

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 As IEnumerable(Of XElement) = po.Descendants("Address").Where(Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

<xref:System.Linq.Enumerable.Where%2A> Metoda jest metodą rozszerzenia. Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md). Ponieważ <xref:System.Linq.Enumerable.Where%2A> jest to metoda rozszerzająca, zapytanie powyżej zostało skompilowane tak, jakby było zapisywane w następujący sposób:

```vb
Dim po = XDocument.Load("PurchaseOrders.xml")

Dim list1 = Enumerable.Where(po.Descendants("Address"), Function(el) el.@Type = "Shipping")

For Each el In list1
    Console.WriteLine(el)
Next
```

Ten przykład daje dokładnie te same wyniki co dwa poprzednie przykłady. Ilustruje to fakt, że zapytania są efektywnie kompilowane na wywołania metod połączonych statycznie. W połączeniu z odroczoną semantyką wykonywania iteratorów, zwiększa wydajność. Aby uzyskać więcej informacji o odroczonej semantyki wykonywania iteratorów, zobacz [odroczone wykonywanie i obliczanie z opóźnieniem w LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

> [!NOTE]
> Te przykłady są reprezentatywne dla kodu, który kompilator może napisać. Rzeczywista implementacja może się nieco różnić od tych przykładów, ale wydajność będzie taka sama lub podobna do tych przykładów.

## <a name="executing-xpath-expressions-with-xmldocument"></a>Wykonywanie wyrażeń XPath przy użyciu elementu XmlDocument

Poniższy przykład używa <xref:System.Xml.XmlDocument> , aby wykonać te same wyniki co w poprzednich przykładach:

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

To zapytanie zwraca te same dane wyjściowe jak przykłady, które używają LINQ to XML; Jedyną różnicą jest to, że LINQ to XML wcięcia drukowanego kodu XML <xref:System.Xml.XmlDocument> , a nie.

Jednakże podejście zwykle nie wykonuje ani LINQ to XML, <xref:System.Xml.XmlNode.SelectNodes%2A> ponieważ metoda musi wykonać wewnętrznie przy każdym wywołaniu: <xref:System.Xml.XmlDocument>

- Analizuje ciąg zawierający wyrażenie XPath, dzieląc ciąg na tokeny.

- Sprawdza tokeny, aby upewnić się, że wyrażenie XPath jest prawidłowe.

- Tłumaczy wyrażenie na wewnętrzne drzewo wyrażeń.

- Wykonuje iterację w węzłach, odpowiednio wybierając węzły dla zestawu wyników na podstawie oceny wyrażenia.

Jest to znacznie więcej niż pracy wykonanej przez odpowiednie LINQ to XML zapytanie. Określona różnica wydajności różni się w zależności od różnych typów zapytań, ale w ogólnych zapytaniach LINQ to XML wykonuje mniej pracy i w związku z tym wykonuje lepsze, niż ocenianie wyrażeń XPath przy użyciu <xref:System.Xml.XmlDocument>.

## <a name="see-also"></a>Zobacz także

- [Wydajność (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
