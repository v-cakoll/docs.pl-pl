---
title: Rozproszone obiekty XName i Xnamespace (LINQ to XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: fe0c4429c89e0028b3b012c87684bd14048de27a
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843445"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>Rozproszone obiekty XName i Xnamespace (LINQ to XML) (Visual Basic)

<xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> obiekty są *rozproszone obiekty*; oznacza to, jeśli zawierają one taką samą nazwę kwalifikowaną, odnoszą się do tego samego obiektu. Daje to zalety korzystania z zapytania: Podczas porównywania dwóch nazw rozproszone obiekty pod kątem równości, podstawowy język pośredni ma tylko do określenia, czy dwa odwołania wskazują ten sam obiekt. Podstawowy kod ma ciągów porównań, i może zająć dużo czasu.

## <a name="atomization-semantics"></a>Rozproszenie semantyki

Rozproszenie oznacza, że jeśli dwa <xref:System.Xml.Linq.XName> obiekty mają taką samą nazwę lokalnego i w tej samej przestrzeni nazw, są one współużytkują to samo wystąpienie. W ten sam sposób, jeśli dwa <xref:System.Xml.Linq.XNamespace> obiekty mają ten sam identyfikator URI przestrzeni nazw, mają tego samego wystąpienia.

Klasy umożliwiające rozproszone obiekty obiektów Konstruktor dla klasy musi być prywatna, nie jest publiczny. Jest to spowodowane gdyby publiczny konstruktor można utworzyć obiektu nierozproszonym. <xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> klasy implementuje operator niejawnej konwersji do przekonwertowania ciągu na <xref:System.Xml.Linq.XName> lub <xref:System.Xml.Linq.XNamespace>. Jest to, jak uzyskać wystąpienie tych obiektów. Za pomocą konstruktora, nie można pobrać wystąpienia, ponieważ Konstruktor jest niedostępny.

<xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> także implementować Operatory równości i nierówności, aby ustalić, czy dwa obiekty są porównywane są odwołaniami do tego samego wystąpienia.

## <a name="example"></a>Przykład

Poniższy kod tworzy niektóre <xref:System.Xml.Linq.XElement> obiektów i pokazuje, że identyczne nazwy współużytkują to samo wystąpienie.

```vb
Dim r1 As New XElement("Root", "data1")
Dim r2 As XElement = XElement.Parse("<Root>data2</Root>")

If DirectCast(r1.Name, Object) = DirectCast(r2.Name, Object) Then
    Console.WriteLine("r1 and r2 have names that refer to the same instance.")
Else
    Console.WriteLine("Different")
End If

Dim n As XName = "Root"

If DirectCast(n, Object) = DirectCast(r1.Name, Object) Then
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.")
Else
    Console.WriteLine("Different")
End If
```

Ten przykład generuje następujące wyniki:

```
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

Jak wspomniano wcześniej, zaletą rozproszone obiekty obiektów jest fakt, że możesz użyć jednej z metod osi, które przyjmują <xref:System.Xml.Linq.XName> jako parametru metody osi tylko musi ustalić, to samo wystąpienie, aby wybrać żądaną elementy dwie nazwy odwołania.

Poniższy przykład przekazuje <xref:System.Xml.Linq.XName> do <xref:System.Xml.Linq.XContainer.Descendants%2A> wywołania metody, który następnie ma lepszą wydajność ze względu na wzorcu rozproszenie.

```vb
Dim root As New XElement("Root", New XElement("C1", 1), New XElement("Z1", New XElement("C1", 2), New XElement("C1", 1)))

Dim query = From e In root.Descendants("C1") Where CInt(e) = 1e

For Each z As var In query
    Console.WriteLine(z)
Next
```

Ten przykład generuje następujące wyniki:

```xml
<C1>1</C1>
<C1>1</C1>
```

## <a name="see-also"></a>Zobacz także

- [Wydajność (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
