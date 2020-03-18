---
title: Atomizowane obiekty XName i XNamespace (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
ms.openlocfilehash: bc5066440d87f5485ae9099d7a7f4f5e9e66b4ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70204269"
---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a>Atomizowane obiekty XName i XNamespace (LINQ do XML) (C#)
<xref:System.Xml.Linq.XName>i <xref:System.Xml.Linq.XNamespace> obiekty są *roztamywane;* oznacza to, że jeśli zawierają tę samą kwalifikowaną nazwę, odnoszą się do tego samego obiektu. Daje to korzyści wydajności dla zapytań: Podczas porównywania dwóch atomized nazwy równości, podstawowego języka pośredniego ma tylko określić, czy dwa odwołania wskazują na ten sam obiekt. Podstawowy kod nie musi wykonywać porównań ciągów, co byłoby czasochłonne.  
  
## <a name="atomization-semantics"></a>Semantyka atomizacji  
 Atomizacja oznacza, <xref:System.Xml.Linq.XName> że jeśli dwa obiekty mają taką samą nazwę lokalną i znajdują się w tym samym obszarze nazw, mają to samo wystąpienie. W ten sam sposób, jeśli dwa <xref:System.Xml.Linq.XNamespace> obiekty mają ten sam identyfikator URI obszaru nazw, mają to samo wystąpienie.  
  
 Dla klasy, aby włączyć atomized obiektów konstruktora dla klasy musi być prywatny, a nie publiczny. Dzieje się tak, ponieważ jeśli konstruktor były publiczne, można utworzyć obiekt niezatomizowany. I <xref:System.Xml.Linq.XName> <xref:System.Xml.Linq.XNamespace> klasy implementują niejawnego operatora <xref:System.Xml.Linq.XName> konwersji, aby przekonwertować ciąg na ciąg lub <xref:System.Xml.Linq.XNamespace>. W ten sposób można uzyskać wystąpienie tych obiektów. Nie można uzyskać wystąpienie przy użyciu konstruktora, ponieważ konstruktor jest niedostępny.  
  
 <xref:System.Xml.Linq.XName>a <xref:System.Xml.Linq.XNamespace> także wdrożyć równość i nierówności operatorów, aby ustalić, czy dwa obiekty porównywane są odwołania do tego samego wystąpienia.  
  
## <a name="example"></a>Przykład  
 Poniższy kod tworzy <xref:System.Xml.Linq.XElement> niektóre obiekty i pokazuje, że identyczne nazwy mają to samo wystąpienie.  
  
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
  
```output  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Jak wspomniano wcześniej, zaletą obiektów atomizowanych jest to, że podczas korzystania <xref:System.Xml.Linq.XName> z jednej z metod osi, które przyjmują jako parametr, metoda osi musi tylko określić, że dwie nazwy odwołują się do tego samego wystąpienia, aby wybrać żądane elementy.  
  
 Poniższy przykład przekazuje <xref:System.Xml.Linq.XName> wywołanie <xref:System.Xml.Linq.XContainer.Descendants%2A> metody, która następnie ma lepszą wydajność ze względu na wzorzec atomizacji.  
  
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
