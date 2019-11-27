---
title: Modyfikowanie drzewa XML w pamięci a konstrukcja funkcjonalna (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: d91c4ebf-6549-43cc-9961-26d4a82f722b
ms.openlocfilehash: 15c38cdf7ce860b34d8d3e9d59b8f06d80f6edd8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344435"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-visual-basic"></a>Modyfikowanie drzewa XML w pamięci a konstrukcja funkcjonalna (LINQ to XML) (Visual Basic)
Modyfikowanie drzewa XML jest tradycyjnym podejściem do zmiany kształtu dokumentu XML. Typowa aplikacja ładuje dokument do magazynu danych, takiego jak DOM lub [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; za pomocą interfejsu programowania można wstawiać węzły, usuwać węzły lub zmieniać zawartość węzłów; a następnie zapisuje plik XML do pliku lub przesyła go za pośrednictwem sieci.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapewnia kolejną metodę, która jest przydatna w wielu scenariuszach *: konstrukcja funkcjonalna*. Konstrukcja funkcjonalna traktuje modyfikowanie danych jako problem transformacji, a nie jako szczegółowe manipulowanie magazynem danych. Jeśli możesz wykonać reprezentację danych i Przekształć ją efektywnie z jednego formularza na inny, wynik jest taki sam jak w przypadku, gdy został przestawiony jeden magazyn danych i manipulowanie nim w jakiś sposób, aby zastosować inny kształt. Najważniejszym podejściem do konstrukcji funkcjonalnej jest przekazanie wyników zapytań do <xref:System.Xml.Linq.XDocument> i konstruktorów <xref:System.Xml.Linq.XElement>.  
  
 W wielu przypadkach można napisać przekształcenie kod w ułamku czasu, jaki mógłby wykonać w celu manipulowania magazynem danych, a ten kod jest bardziej niezawodny i łatwiejszy w obsłudze. W takich przypadkach, mimo że podejście przekształcenie może mieć większą moc obliczeniową, jest to bardziej efektywny sposób modyfikacji danych. Jeśli programista zna podejście funkcjonalne, kod wynikający z wielu przypadków jest łatwiejszy do zrozumienia. Można łatwo znaleźć kod modyfikujący poszczególne części drzewa.  
  
 Podejście, w którym modyfikujesz drzewo XML w miejscu, jest bardziej znane dla wielu programistów modelu DOM, natomiast kod zapisany przy użyciu podejścia funkcjonalnego może wyglądać nieznajomo dla deweloperów, który nie rozumie tego podejścia. Jeśli konieczne jest tylko małe modyfikacje w dużym drzewie XML, podejście, w którym można modyfikować drzewo w wielu przypadkach, zajmie mniej czasu procesora.  
  
 Ten temat zawiera przykład, który jest implementowany przy obu podejściach.  
  
## <a name="transforming-attributes-into-elements"></a>Transformowanie atrybutów do elementów  
 Na potrzeby tego przykładu Załóżmy, że chcesz zmodyfikować następujący prosty dokument XML, aby atrybuty staną się elementami. Ten temat najpierw przedstawia tradycyjne podejście do modyfikacji w miejscu. Następnie zostanie wyświetlone podejście konstrukcja funkcjonalna.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a>Modyfikowanie drzewa XML  
 Można napisać kod proceduralny, aby utworzyć elementy z atrybutów, a następnie usunąć atrybuty w następujący sposób:  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
For Each att As XAttribute In root.Attributes()  
    root.Add(New XElement(att.Name, att.Value))  
Next  
root.Attributes().Remove()  
Console.WriteLine(root)  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a>Podejście funkcjonalne  
 Z kolei podejście funkcjonalne obejmuje kod służący do tworzenia nowego drzewa, wybierania i wybierania elementów i atrybutów z drzewa źródłowego i przekształcania ich zgodnie z potrzebami, gdy są dodawane do nowego drzewa. Podejście funkcjonalne wygląda następująco:  
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim newTree As XElement = _  
    <Root>  
        <%= root.<Child1> %>  
        <%= From att In root.Attributes() _  
            Select New XElement(att.Name, att.Value) %>  
    </Root>  
Console.WriteLine(newTree)  
```  
  
 Ten przykład wyprowadza ten sam kod XML jako pierwszy przykład. Należy jednak zauważyć, że w metodzie funkcjonalnej można zobaczyć uzyskaną strukturę nowego kodu XML. Można zobaczyć, jak utworzyć element `Root`, kod, który ściąga element `Child1` z drzewa źródłowego, oraz kod, który przekształca atrybuty z drzewa źródłowego do elementów w nowym drzewie.  
  
 Przykład funkcjonalny w tym przypadku nie jest krótszy niż pierwszy przykład. nie jest to naprawdę prostsze. Jeśli jednak w drzewie XML wprowadzono wiele zmian, podejście niefunkcjonalne stanie się dość skomplikowane i dość obtuse. Natomiast w przypadku korzystania z podejścia funkcjonalnego nadal wystarczy utworzyć żądany kod XML, a następnie osadzić zapytania i wyrażenia, aby ściągnąć odpowiednią zawartość. Podejście funkcjonalne daje kod, który jest łatwiejszy w obsłudze.  
  
 Należy zauważyć, że w tym przypadku podejście funkcjonalne prawdopodobnie nie będzie działać w sposób niewidoczny, a także podejście do manipulowania drzewem. Główny problem polega na tym, że podejście funkcjonalne tworzy więcej obiektów krótkotrwałych. Jednak kompromis jest skuteczny, jeśli użycie podejścia funkcjonalnego pozwala zwiększyć produktywność programistyczną.  
  
 Jest to bardzo prosty przykład, ale służy do wyświetlania różnicy między dwoma podejściami. Podejście funkcjonalne daje większe korzyści produktywności związane z transformą większych dokumentów XML.  
  
## <a name="see-also"></a>Zobacz także

- [Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
