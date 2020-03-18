---
title: Modyfikacja drzewa XML w pamięci a konstrukcja funkcjonalna (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 55eb95585bdd5d2c52175cacae2e6d049bd06f69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484556"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a>Modyfikacja drzewa XML w pamięci a konstrukcja funkcjonalna (LINQ do XML) (C#)
Modyfikowanie drzewa XML w miejscu jest tradycyjnym podejściem do zmiany kształtu dokumentu XML. Typowa aplikacja ładuje dokument do magazynu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]danych, takiego jak DOM lub ; używa interfejsu programowania do wstawiania węzłów, usuwania węzłów lub zmiany zawartości węzłów; a następnie zapisuje kod XML w pliku lub przesyła go przez sieć.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]umożliwia inne podejście, które jest przydatne w wielu scenariuszach: *konstrukcja funkcjonalna*. Funkcjonalna konstrukcja traktuje modyfikowanie danych jako problem transformacji, a nie jako szczegółową manipulację magazynem danych. Jeśli można wziąć reprezentację danych i przekształcić je wydajnie z jednego formularza do drugiego, wynik jest taki sam, jak w przypadku, gdy byś wziął jeden magazyn danych i manipulował nim w jakiś sposób, aby nabrać innego kształtu. Kluczem do podejścia konstrukcji funkcjonalnych jest przekazywanie <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> wyników zapytań do i konstruktorów.  
  
 W wielu przypadkach można napisać kod transformacji w ułamku czasu, który zajmie manipulowanie magazyn danych, a ten kod jest bardziej niezawodne i łatwiejsze w utrzymaniu. W takich przypadkach, mimo że podejście transformacyjne może zająć więcej mocy obliczeniowej, jest to bardziej skuteczny sposób modyfikowania danych. Jeśli deweloper jest zaznajomiony z podejściem funkcjonalnym, wynikowy kod w wielu przypadkach jest łatwiejsze do zrozumienia. Łatwo jest znaleźć kod, który modyfikuje każdą część drzewa.  
  
 Podejście, w którym można zmodyfikować drzewo XML w miejscu jest bardziej znane wielu programistów DOM, podczas gdy kod napisany przy użyciu podejścia funkcjonalnego może wyglądać nieznane deweloperowi, który jeszcze nie rozumie tego podejścia. Jeśli trzeba tylko dokonać małej modyfikacji do dużego drzewa XML, podejście, w którym można zmodyfikować drzewo w miejscu w wielu przypadkach zajmie mniej czasu procesora CPU.  
  
 W tym temacie przedstawiono przykład, który jest implementowany z obu podejść.  
  
## <a name="transforming-attributes-into-elements"></a>Przekształcanie atrybutów w elementy  
 W tym przykładzie załóżmy, że chcesz zmodyfikować następujący prosty dokument XML, aby atrybuty stały się elementami. W tym temacie najpierw przedstawiono tradycyjne podejście modyfikacji w miejscu. Następnie pokazuje funkcjonalne podejście budowlane.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a>Modyfikowanie drzewa XML  
 Można napisać kod proceduralny, aby utworzyć elementy z atrybutów, a następnie usunąć atrybuty, w następujący sposób:  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 Ten kod generuje następujące dane wyjściowe:  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a>Funkcjonalne podejście budowlane  
 Natomiast podejście funkcjonalne składa się z kodu do tworzenia nowego drzewa, zbieranie i wybieranie elementów i atrybutów z drzewa źródłowego i przekształcanie ich odpowiednio, ponieważ są one dodawane do nowego drzewa. Podejście funkcjonalne wygląda następująco:  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 W tym przykładzie wyprowadza ten sam kod XML, co pierwszy przykład. Należy jednak zauważyć, że faktycznie można zobaczyć wynikową strukturę nowego kodu XML w podejściu funkcjonalnym. Możesz zobaczyć tworzenie `Root` elementu, kod, który pobiera `Child1` element z drzewa źródłowego i kod, który przekształca atrybuty z drzewa źródłowego do elementów w nowym drzewie.  
  
 Funkcjonalny przykład w tym przypadku nie jest krótszy niż w pierwszym przykładzie i tak naprawdę nie jest prostszy. Jeśli jednak masz wiele zmian do drzewa XML, niefunkcjonalne podejście stanie się dość skomplikowane i nieco rozwlekłe. Z drugiej strony, korzystając z podejścia funkcjonalnego, nadal po prostu tworzą żądane XML, osadzanie zapytań i wyrażeń, w stosownych przypadkach, aby wyciągnąć żądaną zawartość. Podejście funkcjonalne daje kod, który jest łatwiejszy w utrzymaniu.  
  
 Należy zauważyć, że w tym przypadku podejście funkcjonalne prawdopodobnie nie będzie działać tak dobrze, jak podejście manipulacji drzewa. Głównym problemem jest to, że podejście funkcjonalne tworzy bardziej krótkotrwałe obiekty. Jednak kompromis jest skuteczny, jeśli zastosowanie podejścia funkcjonalnego pozwala na większą wydajność programisty.  
  
 Jest to bardzo prosty przykład, ale służy do pokazania różnicy w filozofii między tymi dwoma podejściami. Podejście funkcjonalne zapewnia większy wzrost wydajności w przypadku przekształcania większych dokumentów XML.  
  