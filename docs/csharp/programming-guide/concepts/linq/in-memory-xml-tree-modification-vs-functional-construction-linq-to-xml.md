---
title: Modyfikowanie drzewa XML w pamięci a konstrukcja funkcjonalna (LINQ to XML) (C#)
description: Te przykłady zmieniają kształt dokumentu XML, modyfikując go na miejscu i korzystając z konstrukcji funkcjonalnej LINQ to XML w języku C#.
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 7a2e3d2ddcd452cf6a58e9d5cc886f3e8b8dd325
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165785"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a>Modyfikowanie drzewa XML w pamięci a konstrukcja funkcjonalna (LINQ to XML) (C#)
Modyfikowanie drzewa XML jest tradycyjnym podejściem do zmiany kształtu dokumentu XML. Typowa aplikacja ładuje dokument do magazynu danych, takiego jak DOM lub [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ; używa interfejsu programowania, aby wstawiać węzły, usuwać węzły lub zmieniać zawartość węzłów, a następnie zapisuje dane XML do pliku lub przesyła je za pośrednictwem sieci.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]umożliwia kolejną metodę, która jest przydatna w wielu scenariuszach: *konstrukcja funkcjonalna*. Konstrukcja funkcjonalna traktuje modyfikowanie danych jako problem transformacji, a nie jako szczegółowe manipulowanie magazynem danych. Jeśli możesz wykonać reprezentację danych i Przekształć ją efektywnie z jednego formularza na inny, wynik jest taki sam jak w przypadku, gdy został przestawiony jeden magazyn danych i manipulowanie nim w jakiś sposób, aby zastosować inny kształt. Najważniejszym podejściem do konstrukcji funkcjonalnej jest przekazanie wyników zapytań do <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement> konstruktorów.  
  
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
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 Ten kod spowoduje wygenerowanie następujących danych wyjściowych:  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a>Podejście funkcjonalne  
 Z kolei podejście funkcjonalne obejmuje kod służący do tworzenia nowego drzewa, wybierania i wybierania elementów i atrybutów z drzewa źródłowego i przekształcania ich zgodnie z potrzebami, gdy są dodawane do nowego drzewa. Podejście funkcjonalne wygląda następująco:  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 Ten przykład wyprowadza ten sam kod XML jako pierwszy przykład. Należy jednak zauważyć, że w metodzie funkcjonalnej można zobaczyć uzyskaną strukturę nowego kodu XML. Można zobaczyć `Root` , jak utworzyć element, kod, który ściąga `Child1` element z drzewa źródłowego, oraz kod, który przekształca atrybuty z drzewa źródłowego do elementów w nowym drzewie.  
  
 Przykład funkcjonalny w tym przypadku nie jest krótszy niż pierwszy przykład. nie jest to naprawdę prostsze. Jeśli jednak w drzewie XML wprowadzono wiele zmian, podejście niefunkcjonalne stanie się dość skomplikowane i dość obtuse. Natomiast w przypadku korzystania z podejścia funkcjonalnego nadal wystarczy utworzyć żądany kod XML, a następnie osadzić zapytania i wyrażenia, aby ściągnąć odpowiednią zawartość. Podejście funkcjonalne daje kod, który jest łatwiejszy w obsłudze.  
  
 Należy zauważyć, że w tym przypadku podejście funkcjonalne prawdopodobnie nie będzie działać w sposób niewidoczny, a także podejście do manipulowania drzewem. Główny problem polega na tym, że podejście funkcjonalne tworzy więcej obiektów krótkotrwałych. Jednak kompromis jest skuteczny, jeśli użycie podejścia funkcjonalnego pozwala zwiększyć produktywność programistyczną.  
  
 Jest to bardzo prosty przykład, ale służy do wyświetlania różnicy między dwoma podejściami. Podejście funkcjonalne daje większe korzyści produktywności związane z transformą większych dokumentów XML.  
  