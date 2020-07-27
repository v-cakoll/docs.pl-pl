---
title: Przegląd osi LINQ to XML (C#)
description: Dowiedz się więcej na temat metod osi w języku C#, nazywanych również osiami. Możesz badać drzewo XML w LINQ, aby znaleźć elementy i atrybuty i pobrać ich wartości za poorednictwem osi.
ms.date: 07/20/2015
ms.assetid: 516792fb-461d-40a8-8a50-9993a51258fc
ms.openlocfilehash: bbda844e8cb2e3b1ff116fd834c6ab1fdd20c1f8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165441"
---
# <a name="linq-to-xml-axes-overview-c"></a>Przegląd osi LINQ to XML (C#)
Po utworzeniu drzewa XML lub załadowaniu dokumentu XML do drzewa XML można wykonać zapytania do niego, aby znaleźć elementy i atrybuty i pobrać ich wartości. Kolekcje są pobierane za pomocą *metod osi*, nazywanych również *osiami*. Niektóre osie są metodami <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> klasy i, które zwracają <xref:System.Collections.Generic.IEnumerable%601> kolekcje. Niektóre osie są metodami rozszerzającymi w <xref:System.Xml.Linq.Extensions> klasie. Osie zaimplementowane jako metody rozszerzające działają na kolekcjach i zwracają kolekcje.  
  
 Zgodnie z opisem w temacie [klasy XElement](./xelement-class-overview.md), <xref:System.Xml.Linq.XElement> obiekt reprezentuje węzeł pojedynczego elementu. Zawartość elementu może być złożona (czasami nazywana zawartością strukturalną) lub może być elementem prostym. Prosty element może być pusty lub może zawierać wartość. Jeśli węzeł zawiera zawartość strukturalną, można użyć różnych metod osi do pobierania wyliczeń elementów podrzędnych. Najczęściej używane metody osi to <xref:System.Xml.Linq.XContainer.Elements%2A> i <xref:System.Xml.Linq.XContainer.Descendants%2A> .  
  
 Oprócz metod osi, które zwracają kolekcje, istnieją dwie metody, które są często używane w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytaniach. <xref:System.Xml.Linq.XContainer.Element%2A>Metoda zwraca jeden <xref:System.Xml.Linq.XElement> . <xref:System.Xml.Linq.XElement.Attribute%2A>Metoda zwraca jeden <xref:System.Xml.Linq.XAttribute> .  
  
 W wielu celach zapytania LINQ zapewniają najbardziej wydajny sposób badania drzewa, wyodrębniania danych z niego i przekształcania. Zapytania LINQ działają na obiektach, które implementują <xref:System.Collections.Generic.IEnumerable%601> , oraz na [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osiach zwracających <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> kolekcje i <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XAttribute> kolekcje. Te kolekcje są potrzebne do wykonywania zapytań.  
  
 Oprócz metod osi, które pobierają kolekcje elementów i atrybutów, istnieją metody osi, które umożliwiają iteracyjne przechodzenie między drzewa. Na przykład zamiast zajmowania się elementami i atrybutami można współpracować z węzłami drzewa. Węzły to bardziej szczegółowy poziom szczegółowości niż elementy i atrybuty. Podczas pracy z węzłami można analizować Komentarze XML, węzły tekstowe, instrukcje przetwarzania i nie tylko. Ta funkcja jest ważna, na przykład do osoby, która piszą Edytor tekstów i chce zapisywać dokumenty jako XML. Jednakże większość programistów XML dotyczy głównie elementów, atrybutów i ich wartości.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Metody pobierania kolekcji elementów  
 Poniżej znajduje się podsumowanie metod <xref:System.Xml.Linq.XElement> klasy (lub jej klas podstawowych) wywoływanych w <xref:System.Xml.Linq.XElement> celu zwrócenia kolekcji elementów.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|Zwraca wartość <xref:System.Collections.Generic.IEnumerable%601> elementu <xref:System.Xml.Linq.XElement> nadrzędnego tego elementu. Przeciążenie zwraca element <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> nadrzędny, który ma określony <xref:System.Xml.Linq.XName> .|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|Zwraca wartość <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementów podrzędnych tego elementu. Przeciążenie zwraca element <xref:System.Collections.Generic.IEnumerable%601> podrzędny o <xref:System.Xml.Linq.XElement> określonej wartości <xref:System.Xml.Linq.XName> .|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|Zwraca z <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementów podrzędnych tego elementu. Przeciążenie zwraca element <xref:System.Collections.Generic.IEnumerable%601> podrzędny o <xref:System.Xml.Linq.XElement> określonej wartości <xref:System.Xml.Linq.XName> .|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|Zwraca z <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementów, które są dostępne po elemencie. Przeciążenie zwraca część <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementów po tym elemencie, który ma określony <xref:System.Xml.Linq.XName> .|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|Zwraca z <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementów, które są przed tym elementem. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> część elementów, <xref:System.Xml.Linq.XElement> zanim ten element ma określony <xref:System.Xml.Linq.XName> .|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|Zwraca z <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> tego elementu i jego elementy nadrzędne. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> liczbę <xref:System.Xml.Linq.XElement> elementów, które mają określony <xref:System.Xml.Linq.XName> .|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|Zwraca z <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> tego elementu i jego elementy podrzędne. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> liczbę <xref:System.Xml.Linq.XElement> elementów, które mają określony <xref:System.Xml.Linq.XName> .|  
  
## <a name="method-for-retrieving-a-single-element"></a>Metoda pobierania pojedynczego elementu  
 Poniższa metoda pobiera jeden element podrzędny z <xref:System.Xml.Linq.XElement> obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|Zwraca pierwszy obiekt podrzędny <xref:System.Xml.Linq.XElement> , który ma określony <xref:System.Xml.Linq.XName> .|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Metoda pobierania kolekcji atrybutów  
 Poniższa metoda pobiera atrybuty z <xref:System.Xml.Linq.XElement> obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|Zwraca spośród <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XAttribute> wszystkich atrybutów.|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Metoda pobierania pojedynczego atrybutu  
 Poniższa metoda pobiera jeden atrybut z <xref:System.Xml.Linq.XElement> obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|Zwraca wartość <xref:System.Xml.Linq.XAttribute> , która ma określony <xref:System.Xml.Linq.XName> .|  
  
## <a name="see-also"></a>Zobacz także

- [Osie LINQ to XML (C#)](linq-to-xml-axes-overview.md)
