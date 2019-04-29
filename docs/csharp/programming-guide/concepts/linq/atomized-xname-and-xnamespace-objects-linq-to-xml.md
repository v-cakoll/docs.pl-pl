---
title: Rozproszone obiekty XName i Xnamespace (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: ff5677e84d0a4401c9d3ce8c43e7743385cdd432
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61668438"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a>Rozproszone obiekty XName i Xnamespace (LINQ to XML) (C#)
<xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> obiekty są *rozproszone obiekty*; oznacza to, jeśli zawierają one taką samą nazwę kwalifikowaną, odnoszą się do tego samego obiektu. Daje to zalety korzystania z zapytania: Podczas porównywania dwóch nazw rozproszone obiekty pod kątem równości, podstawowy język pośredni ma tylko do określenia, czy dwa odwołania wskazują ten sam obiekt. Podstawowy kod ma ciągów porównań, i może zająć dużo czasu.  
  
## <a name="atomization-semantics"></a>Rozproszenie semantyki  
 Rozproszenie oznacza, że jeśli dwa <xref:System.Xml.Linq.XName> obiekty mają taką samą nazwę lokalnego i w tej samej przestrzeni nazw, są one współużytkują to samo wystąpienie. W ten sam sposób, jeśli dwa <xref:System.Xml.Linq.XNamespace> obiekty mają ten sam identyfikator URI przestrzeni nazw, mają tego samego wystąpienia.  
  
 Klasy umożliwiające rozproszone obiekty obiektów Konstruktor dla klasy musi być prywatna, nie jest publiczny. Jest to spowodowane gdyby publiczny konstruktor można utworzyć obiektu nierozproszonym. <xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> klasy implementuje operator niejawnej konwersji do przekonwertowania ciągu na <xref:System.Xml.Linq.XName> lub <xref:System.Xml.Linq.XNamespace>. Jest to, jak uzyskać wystąpienie tych obiektów. Za pomocą konstruktora, nie można pobrać wystąpienia, ponieważ Konstruktor jest niedostępny.  
  
 <xref:System.Xml.Linq.XName> i <xref:System.Xml.Linq.XNamespace> także implementować Operatory równości i nierówności, aby ustalić, czy dwa obiekty są porównywane są odwołaniami do tego samego wystąpienia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy niektóre <xref:System.Xml.Linq.XElement> obiektów i pokazuje, że identyczne nazwy współużytkują to samo wystąpienie.  
  
```csharp  
XElement r1 = new XElement("Root", "data1");  
XElement r2 = XElement.Parse("<Root>data2</Root>");  
  
if ((object)r1.Name == (object)r2.Name)  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");  
else  
    Console.WriteLine("Different");  
  
XName n = "Root";  
  
if ((object)n == (object)r1.Name)  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");  
else  
    Console.WriteLine("Different");  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Jak wspomniano wcześniej, zaletą rozproszone obiekty obiektów jest fakt, że możesz użyć jednej z metod osi, które przyjmują <xref:System.Xml.Linq.XName> jako parametru metody osi tylko musi ustalić, to samo wystąpienie, aby wybrać żądaną elementy dwie nazwy odwołania.  
  
 Poniższy przykład przekazuje <xref:System.Xml.Linq.XName> do <xref:System.Xml.Linq.XContainer.Descendants%2A> wywołania metody, który następnie ma lepszą wydajność ze względu na wzorcu rozproszenie.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("C1", 1),  
    new XElement("Z1",  
        new XElement("C1", 2),  
        new XElement("C1", 1)  
    )  
);  
  
var query = from e in root.Descendants("C1")  
            where (int)e == 1  
            select e;  
  
foreach (var z in query)  
    Console.WriteLine(z);  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Wydajność (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
