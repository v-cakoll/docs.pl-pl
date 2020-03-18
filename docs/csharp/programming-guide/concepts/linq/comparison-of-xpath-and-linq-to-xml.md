---
title: Porównanie metody XPath i LINQ to XML
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e9bf192a2075653802f0c5a8b4e44ff0ceacb975
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "66487529"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>Porównanie metody XPath i LINQ to XML
XPath i LINQ do XML oferują pewne podobne funkcje. Oba mogą służyć do wykonywania zapytań drzewa XML, zwracając takie wyniki jak zbiór elementów, zbiór atrybutów, zbiór węzłów lub wartość elementu lub atrybutu. Istnieją jednak również pewne różnice.  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>Różnice między XPath i LINQ do XML  
 XPath nie zezwala na projekcję nowych typów. Może zwracać tylko kolekcje węzłów z drzewa, podczas gdy LINQ do XML może wykonać kwerendę i rzutować wykres obiektu lub drzewo XML w nowym kształcie. LINQ do xml zapytania obejmują znacznie więcej funkcji i są znacznie bardziej wydajne niż wyrażenia XPath.  
  
 Wyrażenia XPath istnieją w izolacji w ciągu. Kompilator Języka C# nie może pomóc w przeanalizowaniu wyrażenia XPath w czasie kompilacji. Natomiast zapytania LINQ do XML są analizowane i kompilowane przez kompilator C#. Kompilator jest w stanie przechwycić wiele błędów zapytań.  
  
 Wyniki XPath nie są silnie typowane. W wielu okolicznościach wynik oceny wyrażenia XPath jest obiektem i to do dewelopera należy określenie właściwego typu i rzutowanie wyniku w razie potrzeby. Natomiast rzutowania z kwerendy LINQ do XML są silnie typowane.  
  
## <a name="result-ordering"></a>Kolejność wyników  
 Zalecenie XPath 1.0 stwierdza, że kolekcja, która jest wynikiem oceny wyrażenia XPath jest nieuporządkowana.  
  
 Jednak podczas iteracji za pośrednictwem kolekcji zwracanej przez LINQ do XML XPath metody osi, węzły w kolekcji są zwracane w kolejności dokumentu. Dzieje się tak nawet podczas uzyskiwania dostępu do osi XPath, gdzie predykaty `preceding` są `preceding-sibling`wyrażone w kategoriach odwrotnej kolejności dokumentów, takich jak i .  
  
 Natomiast większość osi LINQ do XML zwraca kolekcje w kolejności dokumentu, ale dwie z nich, <xref:System.Xml.Linq.XNode.Ancestors%2A> a <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>kolekcje zwracają w odwrotnej kolejności dokumentu. W poniższej tabeli wylicza się osie i wskazuje kolejność zbierania dla każdego z nich:  
  
|LINQ do osi XML|Szeregowanie|  
|----------------------|--------------|  
|Węzły XContainer.Descendant|Kolejność dokumentów|  
|XContainer.Descendants (Podrzędne).|Kolejność dokumentów|  
|XContainer.Elements (Elementy XContainer.Elements)|Kolejność dokumentów|  
|XContainer.Węzły|Kolejność dokumentów|  
|XContainer.NodesAfterSelf|Kolejność dokumentów|  
|XContainer.NodesPrzedsiebie|Kolejność dokumentów|  
|XElement.AncestorsISelf|Odwróć kolejność dokumentów|  
|XElement.Atrybuty|Kolejność dokumentów|  
|XElement.DescendantNodesAndSelf|Kolejność dokumentów|  
|XElement.DescendantsAndSelf|Kolejność dokumentów|  
|XNode.Przodkowie|Odwróć kolejność dokumentów|  
|XNode.ElementsAfterSelf|Kolejność dokumentów|  
|XNode.ElementsBeforeSelf|Kolejność dokumentów|  
|XNode.NodesAfterSelf|Kolejność dokumentów|  
|XNode.NodesBeforeSelf|Kolejność dokumentów|  
  
## <a name="positional-predicates"></a>Predykaty pozycyjne  
 W wyrażeniu XPath predykaty pozycyjne są wyrażane w kolejności dokumentów dla wielu osi, ale są `preceding`wyrażone w odwrotnej kolejności dokumentu dla osi odwróconych, które są , `preceding-sibling`, `ancestor`, i `ancestor-or-self`. Na przykład wyrażenie `preceding-sibling::*[1]` XPath zwraca bezpośrednio poprzedzających elementu równorzędnego. Dzieje się tak, mimo że ostateczny zestaw wyników jest prezentowany w kolejności dokumentu.  
  
 Natomiast wszystkie predykaty pozycyjne w LINQ do XML są zawsze wyrażone w kolejności osi. Na przykład `anElement.ElementsBeforeSelf().ElementAt(0)` zwraca pierwszy element podrzędny elementu nadrzędnego elementu, którego dotyczy kwerenda, a nie bezpośrednio poprzedzających elementu równorzędnego. Inny przykład: `anElement.Ancestors().ElementAt(0)` zwraca element nadrzędny.  
  
 Jeśli chcesz znaleźć bezpośrednio poprzedzający element w LINQ do XML, należy napisać następujące wyrażenie:  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a>Różnice w wydajności  
 Kwerendy XPath, które używają funkcji XPath w LINQ do XML nie będzie działać, jak również LINQ do xml kwerend.  
  
## <a name="comparison-of-composition"></a>Porównanie składu  
 Skład kwerendy LINQ do XML jest nieco równoległy do kompozycji wyrażenia XPath, chociaż bardzo różni się składnią.  
  
 Na przykład jeśli masz element w `customers`zmiennej o nazwie i chcesz `CompanyName` znaleźć element wnuka o nazwie pod wszystkimi elementami podrzędnych o nazwie, `Customer`należy napisać wyrażenie XPath w następujący sposób:  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 Równoważne LINQ do kwerendy XML jest:  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 Istnieją podobne podobieństwa dla każdej z osi XPath.  
  
|Oś XPath|LINQ do osi XML|  
|----------------|----------------------|  
|podrzędny (oś domyślna)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|Element nadrzędny (..)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|oś atrybutu (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|oś przodka|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|oś przodka lub samo-siebie|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|oś podrzędna (//)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|pojechania lub-ja|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|kolejne rodzeństwo|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|poprzednia rodzeństwo|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|Następujące|Brak bezpośredniego odpowiednika.|  
|Poprzednim|Brak bezpośredniego odpowiednika.|  
  