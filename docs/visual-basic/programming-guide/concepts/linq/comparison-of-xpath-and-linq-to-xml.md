---
title: Porównanie XPath i składnika LINQ to XML1
ms.date: 07/20/2015
ms.assetid: c3fd07c1-6761-4e4b-8eb1-ddd780ed8d44
ms.openlocfilehash: fe6b0b77f82a9fcb5475e31e096a636211faa578
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="comparison-of-xpath-and-linq-to-xml"></a>Porównanie XPath i LINQ do XML
Wyrażenie XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oferują niektórych podobnych możliwościach. Jednocześnie może służyć do badania drzewo XML zwracania wyników takich jako kolekcję elementów, Kolekcja atrybutów, kolekcja węzłów lub wartość elementu lub atrybutu. Istnieją jednak także pewne różnice.  
  
## <a name="differences-between-xpath-and-linq-to-xml"></a>Różnice między XPath i LINQ do XML  
 Wyrażenie XPath nie zezwala na projekcji nowych typów. Można tylko zwraca kolekcje węzłów w drzewie, natomiast [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można wykonać zapytania i projektu wykres obiektu lub drzewo XML w nowy kształt. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania obejmować większą funkcjonalność i są bardziej efektywne niż wyrażenia XPath.  
  
 Wyrażenia XPath istnieje w izolacji w ramach ciągu. Kompilator Visual Basic nie może pomóc przeanalizować wyrażenia XPath w czasie kompilacji. Z kolei [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania są przeanalizować i kompilowany przez kompilator podstawowe theVisual. Kompilator jest w stanie catch wiele błędów zapytania.  
  
 Wyniki XPath nie są silnie typizowane. W wielu sytuacjach wynikiem obliczenia wyrażenia XPath jest obiektem, a zależy od dewelopera określenie odpowiedniego typu i Rzutuj wynik w razie potrzeby. Przez kontrast, projekcje z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania są silnie typizowane.  
  
## <a name="result-ordering"></a>Powoduje porządkowanie  
 Wyrażenie XPath 1.0 zalecenie informujący nieuporządkowaną kolekcją będącą wynikiem obliczenia wyrażenia XPath.  
  
 Jednak gdy iteracji w kolekcji zwracane przez [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] metody osi XPath, węzły w kolekcji są zwracane w kolejności dokumentu. Jest to możliwe nawet wtedy, gdy dostęp do osi XPath gdzie predykaty są wyrażone w kolejności odwrotnej dokumentu, takich jak `preceding` i `preceding-sibling`.  
  
 Przez kontrast, większość [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osie zwracają kolekcje w kolejności dokumentu, ale dwa z nich, <xref:System.Xml.Linq.XNode.Ancestors%2A> i <xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A>, zwróć kolekcji w kolejności odwrotnej dokumentu. W poniższej tabeli wylicza osi i wskazuje kolejność kolekcji dla każdego:  
  
|LINQ do XML osi|Szeregowanie|  
|----------------------|--------------|  
|XContainer.DescendantNodes|Kolejności dokumentów|  
|XContainer.Descendants|Kolejności dokumentów|  
|XContainer.Elements|Kolejności dokumentów|  
|XContainer.Nodes|Kolejności dokumentów|  
|XContainer.NodesAfterSelf|Kolejności dokumentów|  
|XContainer.NodesBeforeSelf|Kolejności dokumentów|  
|XElement.AncestorsAndSelf|Odwracanie kolejności dokumentów|  
|XElement.Attributes|Kolejności dokumentów|  
|XElement.DescendantNodesAndSelf|Kolejności dokumentów|  
|XElement.DescendantsAndSelf|Kolejności dokumentów|  
|XNode.Ancestors|Odwracanie kolejności dokumentów|  
|XNode.ElementsAfterSelf|Kolejności dokumentów|  
|XNode.ElementsBeforeSelf|Kolejności dokumentów|  
|XNode.NodesAfterSelf|Kolejności dokumentów|  
|XNode.NodesBeforeSelf|Kolejności dokumentów|  
  
## <a name="positional-predicates"></a>Predykaty pozycyjne  
 W wyrażeniu XPath predykaty pozycyjne są wyrażone w kolejności dokumentów dla wielu osi, ale są wyrażane w kolejności odwrotnej dokumentu dla osi wstecznego, które są `preceding`, `preceding-sibling`, `ancestor`, i `ancestor-or-self`. Na przykład, wyrażenie XPath `preceding-sibling::*[1]` zwraca natychmiast poprzedni element równorzędny. Dotyczy to nawet, jeśli zestaw wyników końcowych są prezentowane w kolejności dokumentu.  
  
 Z kolei wszystkie predykaty pozycyjne w składniku LINQ to XML są zawsze wyrażone w porządku osi. Na przykład `anElement.ElementsBeforeSelf().ToList()[0]` zwraca pierwszy element podrzędny elementu nadrzędnego elementu, którego dotyczy kwerenda nie natychmiastowego poprzedniego elementu równorzędnego. Inny przykład: `anElement.Ancestors().ToList()[0]` zwraca element nadrzędny.  
  
 Należy pamiętać, że powyższe podejście zostaje całą kolekcję. Nie jest najbardziej wydajnym sposobem zapisu tego zapytania. Plik został zapisany w ten sposób, aby zademonstrować zachowanie pozycyjnych predykatów. Sposób bardziej odpowiednie do zapisu w jednym zapytaniu jest użycie <xref:System.Linq.Enumerable.First%2A> metody, w następujący sposób: `anElement.ElementsBeforeSelf().First()`.  
  
 Jeśli chcesz znaleźć natychmiast poprzedniego elementu w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], możesz zapisać następującego wyrażenia:  
  
 `ElementsBeforeSelf().Last()`  
  
## <a name="performance-differences"></a>Różnice dotyczące wydajności  
 Kwerendy XPath, korzystających z funkcji XPath w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nie będzie wykonywać oraz [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania.  
  
## <a name="comparison-of-composition"></a>Porównanie kompozycji  
 Skład [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytanie jest nieco zbliżony do kompozycji wyrażenie XPath, mimo że jest to bardzo różnią się w składni.  
  
 Na przykład, jeśli element w zmiennej o nazwie `customers`, i chcesz znaleźć podwójnym elementu o nazwie `CompanyName` w obszarze wszystkich elementów podrzędnych o nazwie `Customer`, możesz zapisać wyrażenie XPath w następujący sposób:  
  
```vb  
customers.XPathSelectElements("./Customer/CompanyName")  
```  
  
 Odpowiednik [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytanie jest:  
  
```vb  
customers.Element("Customer").Elements("CompanyName")  
```  
  
 Istnieją podobne równoleżników dla każdego osi XPath.  
  
|Wyrażenie XPath osi|LINQ do XML osi|  
|----------------|----------------------|  
|podrzędne (oś domyślne)|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|  
|Nadrzędny (.)|<xref:System.Xml.Linq.XObject.Parent%2A?displayProperty=nameWithType>|  
|osi atrybutu (@)|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|  
|elementem nadrzędnym osi|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|  
|elementem nadrzędnym or-self osi|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|  
|osi elementu podrzędnego (/ /)|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XContainer.DescendantNodes%2A?displayProperty=nameWithType>|  
|obiekt podrzędny lub własne|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XElement.DescendantNodesAndSelf%2A?displayProperty=nameWithType>|  
|element równorzędny poniżej|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XNode.NodesAfterSelf%2A?displayProperty=nameWithType>|  
|poprzedzający element równorzędny|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType><br /><br /> lub<br /><br /> <xref:System.Xml.Linq.XNode.NodesBeforeSelf%2A?displayProperty=nameWithType>|  
|Po|Bezpośredniego odpowiednika.|  
|poprzedzających|Bezpośredniego odpowiednika.|  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do XML dla wyrażenia XPath użytkowników (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
