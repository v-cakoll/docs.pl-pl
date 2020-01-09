---
title: Osie LINQ to XML — przegląd
ms.date: 07/20/2015
ms.assetid: 9161f151-cfa8-4408-94ba-08a9ba3a486d
ms.openlocfilehash: 0cf3c20266d0ca9d861eec963afda8f2e71a55a3
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636487"
---
# <a name="linq-to-xml-axes-overview-visual-basic"></a>Przegląd osi LINQ to XML (Visual Basic)
Po utworzeniu drzewa XML lub załadowaniu dokumentu XML do drzewa XML można wykonać zapytania do niego, aby znaleźć elementy i atrybuty i pobrać ich wartości. Kolekcje są pobierane za pomocą *metod osi*, nazywanych również *osiami*. Niektóre osie są metodami klas <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XDocument>, które zwracają <xref:System.Collections.Generic.IEnumerable%601> kolekcje. Niektóre osie są metodami rozszerzającymi w klasie <xref:System.Xml.Linq.Extensions>. Osie zaimplementowane jako metody rozszerzające działają na kolekcjach i zwracają kolekcje.  
  
 Zgodnie z opisem w temacie [XElement Class](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md)— obiekt <xref:System.Xml.Linq.XElement> reprezentuje węzeł pojedynczego elementu. Zawartość elementu może być złożona (czasami nazywana zawartością strukturalną) lub może być elementem prostym. Prosty element może być pusty lub może zawierać wartość. Jeśli węzeł zawiera zawartość strukturalną, można użyć różnych metod osi do pobierania wyliczeń elementów podrzędnych. Najczęściej używane metody osi są <xref:System.Xml.Linq.XContainer.Elements%2A> i <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
 Oprócz metod osi, które zwracają kolekcje, istnieją dwie metody, które są często używane w kwerendach [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]. Metoda <xref:System.Xml.Linq.XContainer.Element%2A> zwraca pojedynczy <xref:System.Xml.Linq.XElement>. Metoda <xref:System.Xml.Linq.XElement.Attribute%2A> zwraca pojedynczy <xref:System.Xml.Linq.XAttribute>.  
  
 W wielu celach zapytania LINQ zapewniają najbardziej wydajny sposób badania drzewa, wyodrębniania danych z niego i przekształcania. Zapytania LINQ działają na obiektach, które implementują <xref:System.Collections.Generic.IEnumerable%601>, a osie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zwracają <xref:System.Collections.Generic.IEnumerable%601> kolekcji <xref:System.Xml.Linq.XElement> i <xref:System.Collections.Generic.IEnumerable%601> kolekcje <xref:System.Xml.Linq.XAttribute>. Te kolekcje są potrzebne do wykonywania zapytań.  
  
 Oprócz metod osi, które pobierają kolekcje elementów i atrybutów, istnieją metody osi, które umożliwiają iteracyjne przechodzenie między drzewa. Na przykład zamiast zajmowania się elementami i atrybutami można współpracować z węzłami drzewa. Węzły to bardziej szczegółowy poziom szczegółowości niż elementy i atrybuty. Podczas pracy z węzłami można analizować Komentarze XML, węzły tekstowe, instrukcje przetwarzania i nie tylko. Ta funkcja jest ważna, na przykład do osoby, która piszą Edytor tekstów i chce zapisywać dokumenty jako XML. Jednakże większość programistów XML dotyczy głównie elementów, atrybutów i ich wartości.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Metody pobierania kolekcji elementów  
 Poniżej znajduje się podsumowanie metod klasy <xref:System.Xml.Linq.XElement> (lub jej klas podstawowych) wywoływanych na <xref:System.Xml.Linq.XElement> w celu zwrócenia kolekcji elementów.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> nadrzędnych tego elementu. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementów nadrzędnych, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementów podrzędnych tego elementu. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementów podrzędnych, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementów podrzędnych tego elementu. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementów podrzędnych, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementów, które są dostępne po elemencie. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementów po tym elemencie, który ma określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementów, które są przed tym elementem. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementów przed tym elementem, który ma określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> tego elementu i jego elementów nadrzędnych. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementów, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> tego elementu i jego elementów podrzędnych. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementów, które mają określony <xref:System.Xml.Linq.XName>.|  
  
## <a name="method-for-retrieving-a-single-element"></a>Metoda pobierania pojedynczego elementu  
 Poniższa metoda pobiera jeden element podrzędny z obiektu <xref:System.Xml.Linq.XElement>.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|Zwraca pierwszy obiekt podrzędny <xref:System.Xml.Linq.XElement>, który ma określony <xref:System.Xml.Linq.XName>.|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Metoda pobierania kolekcji atrybutów  
 Poniższa metoda pobiera atrybuty z obiektu <xref:System.Xml.Linq.XElement>.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XAttribute> wszystkich atrybutów.|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Metoda pobierania pojedynczego atrybutu  
 Poniższa metoda pobiera jeden atrybut z obiektu <xref:System.Xml.Linq.XElement>.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|Zwraca <xref:System.Xml.Linq.XAttribute>, która ma określony <xref:System.Xml.Linq.XName>.|  
  
## <a name="see-also"></a>Zobacz także

- [Osie LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
