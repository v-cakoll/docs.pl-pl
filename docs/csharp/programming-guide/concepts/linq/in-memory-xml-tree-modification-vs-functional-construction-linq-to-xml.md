---
title: Modyfikowanie drzewa XML w pamięci a Konstrukcja funkcjonalna (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 55eb95585bdd5d2c52175cacae2e6d049bd06f69
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484556"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a>Modyfikowanie drzewa XML w pamięci a Konstrukcja funkcjonalna (LINQ to XML) (C#)
Modyfikowanie drzewa XML w miejscu jest tradycyjne podejście na zmieniające się kształt dokumentu XML. Typowa aplikacja ładuje dokumentu do magazynu danych, takich jak modelu DOM lub [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; używa interfejsu programowania wstawić węzłów, usuń węzły lub zmienić zawartość węzłów; a następnie zapisuje w pliku XML lub przesyła je za pośrednictwem sieci.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Umożliwia innym rozwiązaniem, które są przydatne w wielu scenariuszach: *konstrukcja funkcjonalna*. Konstrukcja funkcjonalna modyfikowania dane są traktowane jako problem transformacji, a nie jako szczegółowe manipulowania magazynu danych. Jeśli możesz wykonać reprezentację danych i przekształcić je wydajnie z jednego formularza do innego, wynik jest taki sam, tak, jakby miały jeden magazyn danych i modyfikować je w jakiś sposób, aby móc innego kształtu. Klucz podejścia konstrukcja funkcjonalna służy do przekazywania wyniki zapytania w celu <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement> konstruktorów.  
  
 W wielu przypadkach można napisać kod innowacyjne w zaledwie ułamku czasu, który zajmie się do manipulowania magazynu danych, a ten kod jest bardziej niezawodne i łatwiejsze w utrzymaniu. W takich przypadkach pomimo innowacyjne podejście może zająć więcej mocy obliczeniowej, jest bardziej efektywny sposób modyfikowania danych. Jeśli deweloper jest dobrze znanych funkcjonalności podejście, wynikowy kod w wielu przypadkach jest łatwiejsze do zrozumienia. Jest to łatwe do znalezienia kod, który modyfikuje każdej części drzewa.  
  
 Podejścia, w którym można zmodyfikować XML drzewa w miejscu jest bardziej znane dużą liczbą programistów modelu DOM, natomiast kod napisany za pomocą funkcjonalne podejście może być nieznane dla deweloperów, którzy jeszcze nie rozpoznaje tego podejścia. Jeśli konieczne będzie jedynie wprowadzenie niewielkiej modyfikacji do dużych drzewa XML, podejście, gdzie można modyfikować drzewa w miejscu, w wielu przypadkach zajmie mniej czasu procesora CPU.  
  
 Ten temat zawiera przykład, który jest implementowane za pomocą obu metod.  
  
## <a name="transforming-attributes-into-elements"></a>Przekształcanie atrybutów do elementów  
 Na przykład załóżmy, że chcesz zmodyfikować prostego następujący dokument XML, dzięki czemu atrybuty stają się elementy. W tym temacie przedstawiono pierwsze podejście tradycyjnych modyfikacji w miejscu. Następnie prezentuje podejście konstrukcja funkcjonalna.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a>Modyfikowanie drzewa XML  
 Napisanie kodu procedur do tworzenia elementów z atrybutów i następnie usuwanie atrybutów, w następujący sposób:  
  
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
  
### <a name="functional-construction-approach"></a>Konstrukcja funkcjonalna podejście  
 Z drugiej strony funkcjonalne podejście składa się z kodu w celu utworzenia nowego drzewa, pobierania i wybierania elementów i atrybutów w drzewie źródła i przekształcanie ich odpowiednie zostaną one dodane do nowego drzewa. Funkcjonalne podejście wygląda podobnie do poniższego:  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 W tym przykładzie generuje ten sam kod XML jako pierwszy przykład. Jednak należy zauważyć, może faktycznie zobaczysz Wynikowa struktura nowym XML w ujęciu funkcjonalności. Możesz zobaczyć tworzenie `Root` element, kod, który ściąga `Child1` elementu w drzewie źródła i kod, który przekształca atrybuty z drzewa źródłowego do elementów w nowym drzewie.  
  
 Przykład funkcjonalności w tym przypadku nie jest żadnym krótszy niż pierwszy przykład i nie jest tak naprawdę wszelkie prostsze. Jednak w przypadku wielu zmiany do drzewa XML bez funkcjonalne podejście staną się dość skomplikowane i nieco obtuse. Korzystając z podejścia funkcjonalności, natomiast nadal formularza po prostu żądanego pliku XML osadzania zapytań i wyrażeń, zgodnie z potrzebami pobrać żądaną zawartość. Funkcjonalne podejście dwuoddziałowe zapewnia kod, który jest łatwiejszy w utrzymaniu.  
  
 Należy zauważyć, że w tym przypadku funkcjonalne podejście prawdopodobnie nie wykona dość oraz podejście manipulowania drzewa. Główny problem polega na tym, że funkcjonalne podejście tworzy więcej krótki czas życia obiektów. Jednak kosztem jest skuteczne Jeśli funkcjonalne podejście pozwala uzyskać większą wydajność pracy programisty.  
  
 Jest to bardzo prosty przykład, ale służy do pokazania różnicy w filozofia dwa podejścia. Funkcjonalne podejście dwuoddziałowe zapewnia większą produktywność w przypadku transformacji dokumentów XML większe.  
  