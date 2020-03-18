---
title: Omówienie osi LINQ do XML (C#)
ms.date: 07/20/2015
ms.assetid: 516792fb-461d-40a8-8a50-9993a51258fc
ms.openlocfilehash: c8b64731925f37d54bded62fae4ccae9933ffbe9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635525"
---
# <a name="linq-to-xml-axes-overview-c"></a>Omówienie osi LINQ do XML (C#)
Po utworzeniu drzewa XML lub załadowaniu dokumentu XML do drzewa XML można zbadać go w celu znalezienia elementów i atrybutów oraz pobrania ich wartości. Kolekcje można pobierać za pomocą metod osi , *nazywanych*również *osiami*. Niektóre osie są metody w <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> i klas, które zwracają <xref:System.Collections.Generic.IEnumerable%601> kolekcje. Niektóre osie są metody rozszerzenia <xref:System.Xml.Linq.Extensions> w klasie. Osie, które są implementowane jako metody rozszerzenia działają na kolekcje i zwracakolekcje.  
  
 Zgodnie z opisem w <xref:System.Xml.Linq.XElement> Przegląd klasy [XElement](./xelement-class-overview.md), obiekt reprezentuje węzeł pojedynczego elementu. Zawartość elementu może być złożona (czasami nazywana zawartością strukturalną) lub może być prostym elementem. Prosty element może być pusty lub może zawierać wartość. Jeśli węzeł zawiera zawartość strukturalną, można użyć różnych metod osi do pobierania wyliczeń elementów podrzędnych. Najczęściej stosowanymi metodami osi <xref:System.Xml.Linq.XContainer.Elements%2A> <xref:System.Xml.Linq.XContainer.Descendants%2A>są i .  
  
 Oprócz metod osi, które zwracają kolekcje, istnieją dwie więcej metod, które [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] będą często używane w kwerendach. Metoda <xref:System.Xml.Linq.XContainer.Element%2A> zwraca pojedynczy <xref:System.Xml.Linq.XElement>. Metoda <xref:System.Xml.Linq.XElement.Attribute%2A> zwraca pojedynczy <xref:System.Xml.Linq.XAttribute>.  
  
 Dla wielu celów zapytania LINQ zapewniają najbardziej zaawansowany sposób, aby zbadać drzewo, wyodrębnić dane z niego i przekształcić go. Zapytania LINQ działają na <xref:System.Collections.Generic.IEnumerable%601>obiekty, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] które <xref:System.Collections.Generic.IEnumerable%601> implementują , a osie zwracają <xref:System.Xml.Linq.XElement> kolekcje i <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XAttribute> kolekcje. Te kolekcje są potrzebne do wykonywania zapytań.  
  
 Oprócz metod osi, które pobierają kolekcje elementów i atrybutów, istnieją metody osi, które umożliwiają itetensję przez drzewo bardzo szczegółowo. Na przykład zamiast zajmować się elementami i atrybutami, można pracować z węzłami drzewa. Węzły są drobniejszy poziom szczegółowości niż elementy i atrybuty. Podczas pracy z węzłami można sprawdzać komentarze XML, węzły tekstowe, instrukcje przetwarzania i inne. Ta funkcja jest ważna na przykład dla osoby piszącej edytor tekstu i która chce zapisać dokumenty jako XML. Jednak większość programistów XML dotyczy przede wszystkim elementów, atrybutów i ich wartości.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Metody pobierania kolekcji elementów  
 Poniżej przedstawiono podsumowanie metod <xref:System.Xml.Linq.XElement> klasy (lub jej klas podstawowych), które można <xref:System.Xml.Linq.XElement> wywołać na zwrócić kolekcję elementów.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> przodków tego elementu. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> element nadrzędnych, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> elementy <xref:System.Xml.Linq.XElement> podrzędne tego elementu. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementy podrzędne, które <xref:System.Xml.Linq.XName>mają określony .|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> elementy <xref:System.Xml.Linq.XElement> podrzędne tego elementu. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementy podrzędne, które <xref:System.Xml.Linq.XName>mają określony .|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów, które pochodzą po tym elemencie. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementy po tym elemencie, <xref:System.Xml.Linq.XName>które mają określony .|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów, które są przed tym elementem. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> elementy przed tym elementem, które <xref:System.Xml.Linq.XName>mają określony .|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> tego <xref:System.Xml.Linq.XElement> elementu i jego przodków. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> z elementów, które mają <xref:System.Xml.Linq.XName>określony .|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> tego <xref:System.Xml.Linq.XElement> elementu i jego elementy podrzędne. Przeciążenie zwraca <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> z elementów, które mają <xref:System.Xml.Linq.XName>określony .|  
  
## <a name="method-for-retrieving-a-single-element"></a>Metoda pobierania pojedynczego elementu  
 Poniższa metoda pobiera pojedynczego <xref:System.Xml.Linq.XElement> obiektu podrzędnego z obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.Element%2A?displayProperty=nameWithType>|Zwraca pierwszy <xref:System.Xml.Linq.XElement> obiekt podrzędny, <xref:System.Xml.Linq.XName>który ma określony .|  
  
## <a name="method-for-retrieving-a-collection-of-attributes"></a>Metoda pobierania kolekcji atrybutów  
 Poniższa metoda pobiera atrybuty <xref:System.Xml.Linq.XElement> z obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attributes%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> wartość <xref:System.Xml.Linq.XAttribute> wszystkich atrybutów.|  
  
## <a name="method-for-retrieving-a-single-attribute"></a>Metoda pobierania pojedynczego atrybutu  
 Poniższa metoda pobiera pojedynczy atrybut <xref:System.Xml.Linq.XElement> z obiektu.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Attribute%2A?displayProperty=nameWithType>|Zwraca <xref:System.Xml.Linq.XAttribute> wartość, która <xref:System.Xml.Linq.XName>ma określony .|  
  
## <a name="see-also"></a>Zobacz też

- [LINQ do osi XML (C#)](linq-to-xml-axes-overview.md)
