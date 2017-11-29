---
title: "LINQ do XML-Przegląd osie (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9161f151-cfa8-4408-94ba-08a9ba3a486d
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ae01d8c7257eb03d091a9e249475ef46a67a1c44
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-axes-overview-visual-basic"></a>LINQ do XML-Przegląd osie (Visual Basic)
Po drzewo XML utworzony lub załadowany dokumentu XML na drzewo XML można wykonać zapytanie, aby znaleźć elementy i atrybuty lub pobrać wartości. Pobrać kolekcji za pomocą *metody osi*, nazywany również *osi*. Niektóre z osi są metod w <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XDocument> klas, które zwraca <xref:System.Collections.Generic.IEnumerable%601> kolekcji. Niektóre z osi są metody rozszerzenia w <xref:System.Xml.Linq.Extensions> klasy. Osie, które są wdrażane jako metody rozszerzenia działać w kolekcjach, a następnie wróć kolekcji.  
  
 Zgodnie z opisem w [Przegląd klasy klasy XElement](http://msdn.microsoft.com/library/d35180fe-7016-4895-9bfc-ba1e3f7875ec), <xref:System.Xml.Linq.XElement> obiekt reprezentuje węzeł pojedynczy element. Zawartość elementu może być skomplikowane (nazywane również strukturalnych zawartości) lub może być prosty element. Prosty element może być pusta lub może zawierać wartości. Jeśli węzeł zawiera strukturalnych zawartości, można użyć różnych metod osi można pobrać wyliczenia elementów podrzędnych. Metody osi najczęściej używane są <xref:System.Xml.Linq.XContainer.Elements%2A> i <xref:System.Xml.Linq.XContainer.Descendants%2A>.  
  
 Oprócz metody osi, które zwraca kolekcje, istnieją dwie metody więcej, które będą najczęściej używane w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania. <xref:System.Xml.Linq.XContainer.Element%2A> Metoda zwraca pojedynczą <xref:System.Xml.Linq.XElement>. <xref:System.Xml.Linq.XElement.Attribute%2A> Metoda zwraca pojedynczą <xref:System.Xml.Linq.XAttribute>.  
  
 Dla wielu celów [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] kwerendy zapewniają najbardziej wydajny sposób do badania drzewa, wyodrębniania danych i przekształcenie go. [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]zapytania działać na obiekty, które implementują <xref:System.Collections.Generic.IEnumerable%601>i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osi powrotu <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> kolekcje, i <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XAttribute> kolekcji. Należy tych kolekcji do wykonywania zapytań.  
  
 Oprócz metody osi pobrać kolekcji elementów i atrybutów istnieją metody osi, które umożliwiają Iterowanie drzewa szczegółowo. Na przykład zamiast zajmowanie elementów i atrybutów, można pracować z węzłami drzewa. Węzły są bardziej precyzyjną poziom szczegółowości niż elementów i atrybutów. Podczas pracy z węzłów, można sprawdzić komentarze XML, węzły tekstowe przetwarzania instrukcje i inne. Ta funkcja jest ważne, na przykład do osoby, która zapisuje edytorze tekstów i chce zapisywanie dokumentów w formacie XML. Jednak większość programistów XML są przede wszystkim elementy, atrybuty i wartości.  
  
## <a name="methods-for-retrieving-a-collection-of-elements"></a>Metody do pobierania kolekcję elementów  
 Poniżej przedstawiono podsumowanie metod <xref:System.Xml.Linq.XElement> klasy (lub jej klas podstawowych), który można wywołać w <xref:System.Xml.Linq.XElement> zwrócić kolekcję elementów.  
  
|Metoda|Opis|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.Ancestors%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów nadrzędnych tego elementu. Zwraca przeciążenia <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> z obiektów nadrzędnych, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów podrzędnych tego elementu. Zwraca przeciążenia <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów podrzędnych, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów podrzędnych tego elementu. Zwraca przeciążenia <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów podrzędnych, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XNode.ElementsAfterSelf%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów, które pochodzą od tego elementu. Zwraca przeciążenia <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów po tym elemencie, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów, które pochodzą przed tym elementem. Zwraca przeciążenia <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów przed tym elementem, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XElement.AncestorsAndSelf%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> tego elementu i jego obiektów nadrzędnych. Zwraca przeciążenia <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów, które mają określony <xref:System.Xml.Linq.XName>.|  
|<xref:System.Xml.Linq.XElement.DescendantsAndSelf%2A?displayProperty=nameWithType>|Zwraca <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> tego elementu i jego obiektów podrzędnych. Zwraca przeciążenia <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> elementów, które mają określony <xref:System.Xml.Linq.XName>.|  
  
## <a name="method-for-retrieving-a-single-element"></a>Metoda pobierania jeden Element  
 Poniższa metoda pobiera pojedynczy element potomny z <xref:System.Xml.Linq.XElement> obiektu.  
  
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
 [LINQ do osi XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
