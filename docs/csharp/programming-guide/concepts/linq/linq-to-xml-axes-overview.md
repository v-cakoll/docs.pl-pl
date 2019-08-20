---
title: Przegląd osi LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: 516792fb-461d-40a8-8a50-9993a51258fc
ms.openlocfilehash: b775a37869f0c8baa7d482475e301347cb77c538
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591924"
---
# <a name="linq-to-xml-axes-overview-c"></a>Przegląd osi LINQ to XML (C#)
Po utworzeniu drzewa XML lub załadowaniu dokumentu XML do drzewa XML można wykonać zapytania do niego, aby znaleźć elementy i atrybuty i pobrać ich wartości. Kolekcje są pobierane za pomocą *metod osi*, nazywanych również *osiami*. Niektóre osie są metodami <xref:System.Xml.Linq.XElement> klasy i <xref:System.Xml.Linq.XDocument> , które zwracają <xref:System.Collections.Generic.IEnumerable%601> kolekcje. Niektóre osie są metodami rozszerzającymi w <xref:System.Xml.Linq.Extensions> klasie. Osie zaimplementowane jako metody rozszerzające działają na kolekcjach i zwracają kolekcje.  
  
 Zgodnie z opisem w temacie [klasy XElement](./xelement-class-overview.md), <xref:System.Xml.Linq.XElement> obiekt reprezentuje węzeł pojedynczego elementu. Zawartość elementu może być złożona (czasami nazywana zawartością strukturalną) lub może być elementem prostym. Prosty element może być pusty lub może zawierać wartość. Jeśli węzeł zawiera zawartość strukturalną, można użyć różnych metod osi do pobierania wyliczeń elementów podrzędnych. Najczęściej używane metody osi to <xref:System.Xml.Linq.XContainer.Elements%2A> i. <xref:System.Xml.Linq.XContainer.Descendants%2A>  
  
 Oprócz metod osi, które zwracają kolekcje, istnieją dwie metody, które są często używane w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytaniach. Metoda zwraca jeden <xref:System.Xml.Linq.XElement>. <xref:System.Xml.Linq.XContainer.Element%2A> Metoda zwraca jeden <xref:System.Xml.Linq.XAttribute>. <xref:System.Xml.Linq.XElement.Attribute%2A>  
  
 W wielu celach [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania zapewniają najbardziej wydajny sposób badania drzewa, wyodrębniania danych z niego i przekształcania. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]zapytania działają na obiektach, <xref:System.Collections.Generic.IEnumerable%601>które implementują [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , oraz <xref:System.Collections.Generic.IEnumerable%601> na <xref:System.Xml.Linq.XElement> osiach zwracających <xref:System.Collections.Generic.IEnumerable%601> kolekcje <xref:System.Xml.Linq.XAttribute> i kolekcje. Te kolekcje są potrzebne do wykonywania zapytań.  
  
 Oprócz metod osi, które pobierają kolekcje elementów i atrybutów, istnieją metody osi, które umożliwiają iteracyjne przechodzenie między drzewa. Na przykład zamiast zajmowania się elementami i atrybutami można współpracować z węzłami drzewa. Węzły to bardziej szczegółowy poziom szczegółowości niż elementy i atrybuty. Podczas pracy z węzłami można analizować Komentarze XML, węzły tekstowe, instrukcje przetwarzania i nie tylko. Ta funkcja jest ważna, na przykład do osoby, która piszą Edytor tekstów i chce zapisywać dokumenty jako XML. Jednakże większość programistów XML dotyczy głównie elementów, atrybutów i ich wartości.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Metody pobierania kolekcji elementów  
 Poniżej znajduje się podsumowanie metod <xref:System.Xml.Linq.XElement> klasy (lub jej klas podstawowych) wywoływanych <xref:System.Xml.Linq.XElement> w celu zwrócenia kolekcji elementów.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> Zwracawartość<xref:System.Xml.Linq.XElement> elementu nadrzędnego tego elementu. Przeciążenie zwraca element <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> nadrzędny, który ma określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> Zwracawartość<xref:System.Xml.Linq.XElement> elementów podrzędnych tego elementu. Przeciążenie zwraca element <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> podrzędny o określonej <xref:System.Xml.Linq.XName>wartości.|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> Zwracaz<xref:System.Xml.Linq.XElement> elementów podrzędnych tego elementu. Przeciążenie zwraca element <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> podrzędny o określonej <xref:System.Xml.Linq.XName>wartości.|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> Zwracazelementów,które<xref:System.Xml.Linq.XElement> są dostępne po elemencie. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> część elementów po tym elemencie, który ma określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> Zwracazelementów,które<xref:System.Xml.Linq.XElement> są przed tym elementem. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> część <xref:System.Xml.Linq.XElement> elementów, zanim ten element ma określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> Zwracaztegoelementui<xref:System.Xml.Linq.XElement> jego elementy nadrzędne. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> liczbę <xref:System.Xml.Linq.XElement> elementów, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> Zwracaztegoelementu<xref:System.Xml.Linq.XElement> i jego elementy podrzędne. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> liczbę <xref:System.Xml.Linq.XElement> elementów, które mają określony <xref:System.Xml.Linq.XName>.|  
  
## <a name="method-for-retrieving-a-single-element"></a>Metoda pobierania pojedynczego elementu  
 Poniższa metoda pobiera jeden element podrzędny z <xref:System.Xml.Linq.XElement> obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|Zwraca pierwszy obiekt podrzędny <xref:System.Xml.Linq.XElement> , który ma określony. <xref:System.Xml.Linq.XName>|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Metoda pobierania kolekcji atrybutów  
 Poniższa metoda pobiera atrybuty z <xref:System.Xml.Linq.XElement> obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|<xref:System.Collections.Generic.IEnumerable%601> Zwraca<xref:System.Xml.Linq.XAttribute> spośród wszystkich atrybutów.|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Metoda pobierania pojedynczego atrybutu  
 Poniższa metoda pobiera jeden atrybut z <xref:System.Xml.Linq.XElement> obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|Zwraca wartość <xref:System.Xml.Linq.XName>, która ma określony. <xref:System.Xml.Linq.XAttribute>|  
  
## <a name="see-also"></a>Zobacz także

- [Osie LINQ to XML (C#)](./linq-to-xml-axes.md)
