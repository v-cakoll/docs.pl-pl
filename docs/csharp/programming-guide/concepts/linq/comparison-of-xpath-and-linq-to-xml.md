---
title: Porównanie metody XPath i LINQ to XML
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: afd8701c6a37fd981d9fc23b57904da80eabf86e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583171"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>Porównanie metody XPath i LINQ to XML
Wyrażenie XPath i LINQ to XML oferuje kilka podobne funkcje. Jednocześnie może służyć do kwerendy drzewa XML, zwracaniu takich wyników jako kolekcja elementów, Kolekcja atrybutów, kolekcja węzłów lub wartość elementu lub atrybutu. Istnieją również pewne różnice.  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>Różnice między XPath i LINQ to XML  
 Wyrażenie XPath nie zezwala na projekcji nowych typów. Jego może zwracać tylko kolekcje węzłów z drzewa, natomiast LINQ to XML można wykonać zapytania i projektu wykresu obiektu lub drzewa XML w nowy kształt. LINQ do XML zapytań uwzględniający znacznie więcej funkcji i są bardziej zaawansowane niż wyrażenia XPath.  
  
 Wyrażenia XPath istnieje w izolacji wewnątrz ciągu. Kompilator języka C# nie będzie mogła pomóc przeanalizować wyrażenia XPath w czasie kompilacji. Z drugiej strony LINQ to XML zapytania są analizowane i kompilowane przez kompilator języka C#. Kompilator jest w stanie przechwytywania wielu błędów zapytań.  
  
 Wyniki XPath nie są silnie typizowane. W wielu sytuacjach wynikiem obliczenia wyrażenia XPath jest obiektem, a zależy od dla deweloperów, aby ustalić odpowiedniego typu i Rzutuj wynik metody zgodnie z potrzebami. Z drugiej strony projekcje z LINQ do kwerendy XML są silnie typizowane.  
  
## <a name="result-ordering"></a>Wynik, porządkowanie  
 Wyrażenie XPath 1.0 zalecenie stanów, nieuporządkowane to kolekcja, która jest wynikiem obliczenia wyrażenia XPath.  
  
 Podczas iteracji przez kolekcję zwracane przez LINQ do XML XPath metody osi, węzły w kolekcji są zwracane w kolejności dokumentu. Jest to możliwe nawet wtedy, gdy dostęp do osi XPath gdzie predykaty są wyrażone w kolejności odwrotnej dokumentu, takich jak `preceding` i `preceding-sibling`.  
  
 Z kolei większość LINQ to XML osi zwrócić kolekcji w kolejności dokumentu, ale dwa z nich, <xref:System.Xml.Linq.XNode.Ancestors%2A> i <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, zwracają kolekcje w kolejności odwrotnej dokumentu. W poniższej tabeli wylicza osi i wskazuje kolejność kolekcji dla każdego:  
  
|LINQ do XML osi|Szeregowanie|  
|----------------------|--------------|  
|XContainer.DescendantNodes|Kolejności dokumentu|  
|XContainer.Descendants|Kolejności dokumentu|  
|XContainer.Elements|Kolejności dokumentu|  
|XContainer.Nodes|Kolejności dokumentu|  
|XContainer.NodesAfterSelf|Kolejności dokumentu|  
|XContainer.NodesBeforeSelf|Kolejności dokumentu|  
|XElement.AncestorsAndSelf|Kolejności odwrotnej dokumentu|  
|XElement.Attributes|Kolejności dokumentu|  
|XElement.DescendantNodesAndSelf|Kolejności dokumentu|  
|XElement.DescendantsAndSelf|Kolejności dokumentu|  
|XNode.Ancestors|Kolejności odwrotnej dokumentu|  
|XNode.ElementsAfterSelf|Kolejności dokumentu|  
|XNode.ElementsBeforeSelf|Kolejności dokumentu|  
|XNode.NodesAfterSelf|Kolejności dokumentu|  
|XNode.NodesBeforeSelf|Kolejności dokumentu|  
  
## <a name="positional-predicates"></a>Predykaty pozycyjne  
 W obrębie wyrażenia XPath predykaty pozycyjne są wyrażone w kolejności dokumentu dla wielu osi, ale są wyrażone w kolejności odwrotnej dokumentu dla odwrotnej osi, które są `preceding`, `preceding-sibling`, `ancestor`, i `ancestor-or-self`. Na przykład, wyrażenie XPath `preceding-sibling::*[1]` zwraca niezwłocznie poprzednich elementów równorzędnych. Dotyczy to nawet, jeśli zestaw wynik końcowy są prezentowane w kolejności dokumentu.  
  
 Z drugiej strony wszystkich predykaty pozycyjne w składniku LINQ to XML zawsze są wyrażone w kolejności osi. Na przykład `anElement.ElementsBeforeSelf().ElementAt(0)` zwraca pierwszy element podrzędny elementu nadrzędnego zapytanie o element, a nie bezpośrednio poprzednich elementów równorzędnych. Inny przykład: `anElement.Ancestors().ElementAt(0)` zwraca element nadrzędny.  
  
 Jeśli chcesz znaleźć bezpośrednio poprzedzający element w składniku LINQ to XML, należy napisać następujące wyrażenie:  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a>Różnice w wydajności  
 Kwerendy XPath, które używają funkcji XPath w składniku LINQ to XML nie wykona oraz LINQ do XML zapytań.  
  
## <a name="comparison-of-composition"></a>Porównanie kompozycji  
 Skład zapytaniu składnika LINQ to XML jest nieco zbliżony do składu wyrażenie XPath, mimo że jest to bardzo różne przy użyciu składni.  
  
 Na przykład, jeśli element w zmiennej o nazwie `customers`, i chcesz znaleźć element podwójnym o nazwie `CompanyName` w ramach wszystkich elementów podrzędnych o nazwie `Customer`, należy napisać wyrażenie XPath w następujący sposób:  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 Jest równoważne zapytaniu składnika LINQ to XML:  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 Istnieją podobne równoleżników dla każdej z osi XPath.  
  
|Wyrażenie XPath osi|LINQ do XML osi|  
|----------------|----------------------|  
|podrzędne (oś domyślny)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|Nadrzędny (.)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|osi atrybutu (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|osi nadrzędnym|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|osi nadrzędnym lub self|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|osi elementu podrzędnego (/ /)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|descendant-or-self|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|następujący element równorzędny|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|Poprzedni element równorzędny|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|następujące|Bezpośredniego odpowiednika.|  
|poprzedza|Bezpośredniego odpowiednika.|  
  
## <a name="see-also"></a>Zobacz także

- [LINQ to XML dla użytkowników metody XPath (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
