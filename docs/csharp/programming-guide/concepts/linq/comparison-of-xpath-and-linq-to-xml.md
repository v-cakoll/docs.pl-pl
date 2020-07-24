---
title: Porównanie metody XPath i LINQ to XML
description: Dowiedz się więcej o podobieństwach i różnicach w działaniu między XPath i LINQ to XML w języku C#. Można użyć obu tych metod do wykonywania zapytań w drzewie XML.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 87d361b1-daa9-4fd4-a53a-cbfa40111ad3
ms.openlocfilehash: e2f34903b20a53dea6e5ff4858d4fadaebd9c37a
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104001"
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>Porównanie metody XPath i LINQ to XML
Wyrażenia XPath i LINQ to XML oferują pewne podobne funkcje. Oba te funkcje mogą służyć do wykonywania zapytań w drzewie XML, zwracając takie wyniki jako kolekcja elementów, Kolekcja atrybutów, kolekcja węzłów lub wartość elementu lub atrybutu. Istnieją jednak również pewne różnice.  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>Różnice między XPath i LINQ to XML  
 Wyrażenie XPath nie zezwala na projekcję nowych typów. Można zwrócić kolekcje węzłów tylko z drzewa, podczas gdy LINQ to XML może wykonać zapytanie i projektować obiekt Graph lub drzewo XML w nowym kształcie. Zapytania LINQ to XML obejmują znacznie większą funkcjonalność i są znacznie bardziej wydajne niż wyrażenia XPath.  
  
 Wyrażenia XPath istnieją w izolacji w ciągu. Kompilator języka C# nie może pomóc w analizie wyrażenia XPath w czasie kompilacji. Z kolei LINQ to XML zapytania są analizowane i kompilowane przez kompilator języka C#. Kompilator może przechwycić wiele błędów zapytań.  
  
 Wyniki XPath nie są jednoznacznie wpisane. W wielu okolicznościach wynik oceny wyrażenia XPath jest obiektem, a programista może określić właściwy typ i rzutować wynik odpowiednio do potrzeb. Z kolei, projekcje z kwerendy LINQ to XML są jednoznacznie wpisane.  
  
## <a name="result-ordering"></a>Porządkowanie wyników  
 Zalecenie XPath 1,0 stwierdza, że kolekcja będąca wynikiem oceny wyrażenia XPath jest nieuporządkowana.  
  
 Jednak podczas iteracji w kolekcji zwróconej przez LINQ to XML metodę osi XPath węzły w kolekcji są zwracane w kolejności dokumentu. Jest to przypadek, nawet w przypadku uzyskiwania dostępu do osi XPath, gdzie predykaty są wyrażane w postaci odwrotnej kolejności dokumentu, takiej jak `preceding` i `preceding-sibling` .  
  
 Z kolei większość osi LINQ to XML zwraca kolekcje w kolejności dokumentu, ale dwa z nich, <xref:System.Xml.Linq.XNode.Ancestors%2A> a następnie <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A> zwraca kolekcje w odwrotnej kolejności dokumentu. Poniższa tabela zawiera Wyliczenie osi i wskazuje kolejność zbierania dla każdej z nich:  
  
|Oś LINQ to XML|Szeregowanie|  
|----------------------|--------------|  
|XContainer.DescendantNodes|Kolejność dokumentów|  
|XContainer. Descendants|Kolejność dokumentów|  
|XContainer. elementy|Kolejność dokumentów|  
|XContainer. węzły|Kolejność dokumentów|  
|XContainer.NodesAfterSelf|Kolejność dokumentów|  
|XContainer.NodesBeforeSelf|Kolejność dokumentów|  
|XElement. AncestorsAndSelf|Zamówienie odwrócenia dokumentu|  
|XElement. Attributes|Kolejność dokumentów|  
|XElement. DescendantNodesAndSelf|Kolejność dokumentów|  
|XElement. DescendantsAndSelf|Kolejność dokumentów|  
|XNode. przodków|Zamówienie odwrócenia dokumentu|  
|XNode.ElementsAfterSelf|Kolejność dokumentów|  
|XNode.ElementsBeforeSelf|Kolejność dokumentów|  
|XNode.NodesAfterSelf|Kolejność dokumentów|  
|XNode.NodesBeforeSelf|Kolejność dokumentów|  
  
## <a name="positional-predicates"></a>Predykaty pozycyjne  
 W wyrażeniu XPath predykaty pozycyjne są wyrażane w zakresie kolejności dokumentu dla wielu osi, ale są wyrażane w kolejności odwrotnego dokumentu dla odwróconych osi, które są `preceding` ,, `preceding-sibling` `ancestor` , i `ancestor-or-self` . Na przykład wyrażenie XPath `preceding-sibling::*[1]` zwraca bezpośrednio poprzedni element równorzędny. Dzieje się tak, mimo że końcowy zestaw wyników jest przedstawiony w kolejności dokumentu.  
  
 Z kolei wszystkie predykaty pozycyjne w LINQ to XML są zawsze wyrażane w warunkach kolejności osi. Na przykład `anElement.ElementsBeforeSelf().ElementAt(0)` zwraca pierwszy element podrzędny obiektu nadrzędnego z zapytania elementu, a nie bezpośrednio poprzedzającego element równorzędny. Inny przykład: `anElement.Ancestors().ElementAt(0)` zwraca element nadrzędny.  
  
 Aby znaleźć bezpośrednio poprzedzający element w LINQ to XML, należy napisać następujące wyrażenie:  
  
```csharp
ElementsBeforeSelf().Last()
```
  
```vb
ElementsBeforeSelf().Last()
```
  
## <a name="performance-differences"></a>Różnice w wydajności  
 Zapytania XPath korzystające z funkcji XPath w LINQ to XML nie będą wykonywać ani LINQ to XML zapytań.  
  
## <a name="comparison-of-composition"></a>Porównanie kompozycji  
 Kompozycja LINQ to XMLego zapytania jest nieco równoległa do kompozycji wyrażenia XPath, chociaż różni się w składni.  
  
 Na przykład jeśli masz element w zmiennej o nazwie `customers` i chcesz znaleźć element grandchild o nazwie `CompanyName` pod wszystkimi elementami podrzędnymi o nazwie `Customer` , Zapisz wyrażenie XPath w następujący sposób:  
  
```csharp  
customers.XPathSelectElements("./Customer/CompanyName")
```  
  
```vb
customers.XPathSelectElements("./Customer/CompanyName")
```

 Odpowiednik kwerendy LINQ to XML jest:  
  
```csharp  
customers.Elements("Customer").Elements("CompanyName")
```  
  
```vb
customers.Elements("Customer").Elements("CompanyName")
```  

 Istnieją podobne równoległości dla każdej z osi XPath.  
  
|Oś XPath|Oś LINQ to XML|  
|----------------|----------------------|  
|element podrzędny (oś domyślna)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|Nadrzędne (..)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|oś atrybutów (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|oś nadrzędna|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|obiekt nadrzędny lub samosamej osi|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|oś elementu podrzędnego (//)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|elementy podrzędne lub samodzielne|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|poniżej — element równorzędny|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|Poprzedni element równorzędny|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|dodaje|Brak bezpośredniego odpowiednika.|  
|licencyjn|Brak bezpośredniego odpowiednika.|  
  