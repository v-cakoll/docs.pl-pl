---
title: LINQ to XML — Przegląd osi (C#)
ms.date: 07/20/2015
ms.assetid: 516792fb-461d-40a8-8a50-9993a51258fc
ms.openlocfilehash: 9b771e0157d1fcfbbb4643d24ccdbf096787f08b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486860"
---
# <a name="linq-to-xml-axes-overview-c"></a>LINQ to XML — Przegląd osi (C#)
Po drzewa XML utworzone lub ładowany dokument XML do drzewa XML można tworzyć zapytania, do znajdowania elementów i atrybutów i pobierania ich wartości. Pobieranie kolekcji za pomocą *metody osi*, nazywane również *osi*. Niektóre z osi są metody <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XDocument> klasy, które zwraca <xref:System.Collections.Generic.IEnumerable%601> kolekcji. Niektóre z osi są metody rozszerzające w <xref:System.Xml.Linq.Extensions> klasy. Osi, które są implementowane jako metody rozszerzenia działają w kolekcjach, a następnie zwracają kolekcje.  
  
 Zgodnie z opisem w [Przegląd klasy XElement](https://msdn.microsoft.com/library/d35180fe-7016-4895-9bfc-ba1e3f7875ec), <xref:System.Xml.Linq.XElement> obiekt reprezentuje węzeł pojedynczy element. Zawartość elementu może być złożonym procesem (czasami nazywany zawartość ze strukturą) lub może być prosty element. Prosty element może być pusta lub może zawierać wartość. Jeśli węzeł zawiera zawartość ze strukturą, można użyć różnych metod osi do pobrania wyliczenia elementów podrzędnych. Metody osi najczęściej używane są <xref:System.Xml.Linq.XContainer.Elements%2A> i <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
 Oprócz metody osi, które zwracają kolekcje, istnieją dwie metody więcej, które będzie najczęściej używany w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania. <xref:System.Xml.Linq.XContainer.Element%2A> Metoda zwraca pojedynczą <xref:System.Xml.Linq.XElement>. <xref:System.Xml.Linq.XElement.Attribute%2A> Metoda zwraca pojedynczą <xref:System.Xml.Linq.XAttribute>.  
  
 Do wielu celów [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania umożliwiają najbardziej wydajnymi procesorami zbadać drzewa, wyodrębnić z niej dane i przekształcić je. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] kwerend działają na obiektach, które implementują <xref:System.Collections.Generic.IEnumerable%601>i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osi powrotu <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> kolekcji, a <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute> kolekcji. Potrzebujesz tych kolekcji do wykonywania zapytań.  
  
 Oprócz metod osi, które pobierają kolekcji elementów i atrybutów istnieją metody osi, które pozwalają na Iterowanie drzewa bardzo szczegółowo. Na przykład zamiast zajmowanie się elementów i atrybutów, można pracować z węzłami drzewa. Węzły są bardziej precyzyjną stopień szczegółowości niż elementów i atrybutów. Podczas pracy z węzłów, można sprawdzić komentarze XML, węzły tekstowe przetwarzania instrukcji i nie tylko. Ta funkcja jest ważna, na przykład, aby osoba, która zapisuje do edytora tekstów i chce, aby zapisywać dokumenty w formacie XML. Jednak większość programistów XML są przede wszystkim elementów, atrybutów i ich wartości.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Metody do pobierania kolekcji elementów  
 Poniżej przedstawiono podsumowanie metod <xref:System.Xml.Linq.XElement> klasy (lub jej klasy bazowe), który chcesz wywołać w <xref:System.Xml.Linq.XElement> zwracać kolekcję elementów.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> z elementów nadrzędnych tego elementu. Zwraca przeciążenia <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> z elementów nadrzędnych, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> z elementami podrzędnymi tego elementu. Zwraca przeciążenia <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> obiektów podrzędnych, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów podrzędnych tego elementu. Zwraca przeciążenia <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów podrzędnych, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów, które pochodzą od tego elementu. Zwraca przeciążenia <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów po tym elemencie, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów, które występować przed tym elementem. Zwraca przeciążenia <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów przed tego elementu, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> ten element i jego elementów nadrzędnych. Zwraca przeciążenia <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> ten element i jego elementy podrzędne. Zwraca przeciążenia <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów, które mają określony <xref:System.Xml.Linq.XName>.|  
  
## <a name="method-for-retrieving-a-single-element"></a>Metoda pobierania pojedynczego elementu  
 Poniższa metoda pobiera pojedynczy element podrzędny z <xref:System.Xml.Linq.XElement> obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|Zwraca pierwszy element podrzędny <xref:System.Xml.Linq.XElement> obiekt, który ma określony <xref:System.Xml.Linq.XName>.|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Metoda pobierania kolekcję atrybutów  
 Poniższa metoda pobiera atrybuty z <xref:System.Xml.Linq.XElement> obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute> wszystkich atrybutów.|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Metoda pobierania jeden atrybut  
 Poniższa metoda pobiera jeden atrybut z <xref:System.Xml.Linq.XElement> obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|Zwraca <xref:System.Xml.Linq.XAttribute> ma określony <xref:System.Xml.Linq.XName>.|  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do XML osi (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
