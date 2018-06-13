---
title: Atomized XName i XNamespace obiektów (LINQ do XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 21ee7585-7df9-40b4-8c76-a12bb5f29bb3
ms.openlocfilehash: e311de901a9a54bd4fc6ee56d425cc16b4978e8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643276"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-visual-basic"></a>Atomized XName i XNamespace obiektów (LINQ do XML) (Visual Basic)
<xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> obiekty są *atomized*; oznacza to, że jeśli zawierają takiej samej nazwie kwalifikowanej odnoszą się do tego samego obiektu. Daje to zwiększenia wydajności kwerend: podczas porównywania dwóch nazw atomized pod kątem równości ustalić, czy dwa odwołania wskazywać tego samego obiektu ma tylko podstawowy język pośredni. Kod źródłowy ma ciągu porównań, które może być czasochłonne.  
  
## <a name="atomization-semantics"></a>Semantyka Atomizacja  
 Atomizacja oznacza, że jeśli dwie <xref:System.Xml.Linq.XName> obiekty mają taką samą nazwę lokalnego i w tej samej przestrzeni nazw, są one współużytkują to samo wystąpienie. W ten sam sposób, jeśli dwa <xref:System.Xml.Linq.XNamespace> obiekty mają się tym samym identyfikatorem URI przestrzeni nazw, mają tego samego wystąpienia.  
  
 Klasy umożliwiające atomized obiektów konstruktora dla klasy musi być prywatny, nie jest publiczna. Jest to spowodowane gdyby publicznego konstruktora, można utworzyć obiektu nierozproszonym. <xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> klasy implementować operator niejawnej konwersji do przekonwertowania ciągu na <xref:System.Xml.Linq.XName> lub <xref:System.Xml.Linq.XNamespace>. Jest to, jak pobrać wystąpienia tych obiektów. Nie można pobrać wystąpienia przy użyciu konstruktora, ponieważ Konstruktor jest niedostępny.  
  
 <xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> także implementować Operatory równości i nierówności, aby określić, czy dwa obiekty są porównywane są odwołania do tego samego wystąpienia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy niektóre <xref:System.Xml.Linq.XElement> obiekty i pokazuje, że identycznych nazw współużytkują to samo wystąpienie.  
  
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
  
 Jak wspomniano wcześniej, zaletą atomized obiektów jest fakt, że korzystanie z jednej z metod osi, które przyjmują <xref:System.Xml.Linq.XName> jako parametru metody osi tylko musi ustalić to samo wystąpienie, aby wybrać odpowiednie elementy dwie nazwy odwołania.  
  
 W poniższym przykładzie <xref:System.Xml.Linq.XName> do <xref:System.Xml.Linq.XContainer.Descendants%2A> wywołania metody, który następnie ma lepszą wydajność ze względu na wzorcu Atomizacja.  
  
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
 [Wydajność (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
