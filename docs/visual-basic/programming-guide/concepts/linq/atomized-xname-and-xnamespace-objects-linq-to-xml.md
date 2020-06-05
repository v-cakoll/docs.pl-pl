---
title: Rozproszone obiekty XName i XNamespace (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: 6a94bc0f2fd8013997e233b300fa19c12671bf29
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84383692"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>Atomed XName and XNamespace Objects (LINQ to XML) (Visual Basic)

<xref:System.Xml.Linq.XName>i <xref:System.Xml.Linq.XNamespace> obiekty są *atomowe*; oznacza to, że jeśli zawierają one taką samą kwalifikowaną nazwę, odwołują się do tego samego obiektu. Zapewnia to korzyści z wydajności dla zapytań: w przypadku porównania dwóch nazw atomowych dla równości, podstawowy język pośredni musi określić, czy te dwa odwołania wskazują na ten sam obiekt. Kod źródłowy nie musi wykonywać porównań ciągów, co byłoby czasochłonne.

## <a name="atomization-semantics"></a>Semantyka rozproszenie

Rozproszenie oznacza, że jeśli dwa <xref:System.Xml.Linq.XName> obiekty mają tę samą nazwę lokalną i znajdują się w tej samej przestrzeni nazw, współużytkują to samo wystąpienie. W taki sam sposób, jeśli dwa <xref:System.Xml.Linq.XNamespace> obiekty mają ten sam identyfikator URI przestrzeni nazw, współużytkują to samo wystąpienie.

Aby można było włączyć obiekt Atoms, Konstruktor dla klasy musi być prywatny, a nie publiczny. Wynika to z faktu, że jeśli Konstruktor był publiczny, można utworzyć obiekt niebędący atomem. <xref:System.Xml.Linq.XName>Klasy i <xref:System.Xml.Linq.XNamespace> implementują Operator niejawnej konwersji w celu przekonwertowania ciągu na <xref:System.Xml.Linq.XName> lub <xref:System.Xml.Linq.XNamespace> . W ten sposób można uzyskać wystąpienie tych obiektów. Nie można uzyskać wystąpienia przy użyciu konstruktora, ponieważ Konstruktor jest niedostępny.

<xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> także zaimplementować operatory równości i nierówności, aby określić, czy dwa porównywane obiekty są odwołaniami do tego samego wystąpienia.

## <a name="example"></a>Przykład

Poniższy kod tworzy niektóre <xref:System.Xml.Linq.XElement> obiekty i pokazuje, że identyczne nazwy współużytkują to samo wystąpienie.

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

```console
r1 and r2 have names that refer to the same instance.
The name of r1 and the name in 'n' refer to the same instance.
```

Jak wspomniano wcześniej, zaletą obiektów atomowych jest użycie jednej z metod osi, która przyjmuje <xref:System.Xml.Linq.XName> jako parametr, metoda osi ma tylko określić, że dwie nazwy odwołują się do tego samego wystąpienia w celu wybrania żądanych elementów.

Poniższy przykład przekazuje <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XContainer.Descendants%2A> wywołanie metody, które następnie ma lepszą wydajność ze względu na wzorzec rozproszenie.

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

## <a name="see-also"></a>Zobacz też

- [Wydajność (LINQ to XML) (Visual Basic)](performance-linq-to-xml.md)
