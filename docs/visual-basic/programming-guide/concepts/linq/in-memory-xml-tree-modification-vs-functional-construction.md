---
title: Vs modyfikacji drzewa XML w pamięci. Konstrukcja funkcjonalności (LINQ do XML) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: d91c4ebf-6549-43cc-9961-26d4a82f722b
ms.openlocfilehash: 71b8799d4da2f8f4fb10bdec6ca7cfcec76e036a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646607"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-visual-basic"></a>Vs modyfikacji drzewa XML w pamięci. Konstrukcja funkcjonalności (LINQ do XML) (Visual Basic)
Modyfikowanie drzewo XML w miejscu jest to tradycyjne podejście, aby zmiana kształtu dokumentu XML. Typowa aplikacja ładuje dokumentu do magazynu danych, takich jak modelu DOM lub [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; używa interfejsu programowania do wstawiania węzłów, usuń węzły lub zmienić zawartości węzłów; a następnie zapisuje w pliku XML lub przesyła go za pośrednictwem sieci.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Umożliwia innym rozwiązaniem, które są przydatne w wielu scenariuszach *: budowa funkcjonalności*. Funkcjonalności konstrukcji modyfikowanie dane są traktowane jako problem transformacji, a nie jako szczegółowe modyfikowanie magazynu danych. Jeśli możesz pobrać reprezentację dane i przetransformować je wydajnie z jednego formularza do innego, wynik jest taki sam, jakby miał jeden magazyn danych i manipulowanie go w celu podjęcia innego kształtu. Klucz do metody konstruowania funkcjonalności jest do przekazania wyników zapytania, aby <xref:System.Xml.Linq.XDocument> i <xref:System.Xml.Linq.XElement> konstruktorów.  
  
 W wielu przypadkach można napisać transformational kod w ułamku czasu, który zajmie się do manipulowania magazynu danych, a ten kod jest bardziej niezawodny i łatwiejsze w obsłudze. W takich przypadkach mimo że transformational podejście może zająć więcej mocy obliczeniowej jest bardziej efektywny sposób modyfikowania danych. W przypadku zapoznać się z funkcjonalności podejście dewelopera, wynikowy kod w wielu przypadkach jest łatwiejsze do zrozumienia. Jest łatwe do odnalezienia kod, który modyfikuje każdej części drzewa.  
  
 Podejście, w którym można zmodyfikować XML drzewa w miejscu jest lepiej znana wielu programistów modelu DOM, podczas gdy kod napisany za pomocą funkcjonalności podejście może wyglądać doświadczenia w pracy dla deweloperów, którzy jeszcze nie rozpoznaje tego podejścia. Jeśli konieczne będzie jedynie wprowadzenie małych modyfikację dużych drzewa XML, podejście, w którym można zmodyfikować w drzewie miejsce w wielu przypadkach będzie zająć mniej czasu Procesora.  
  
 Ten temat zawiera przykładowy jest realizowana za pomocą obu podejść.  
  
## <a name="transforming-attributes-into-elements"></a>Przekształcanie atrybutów do elementów  
 Na przykład załóżmy, że chcesz zmodyfikować następujące prostego dokumentu XML, aby atrybuty stają się elementów. W tym temacie przedstawiono najpierw podejście tradycyjnych modyfikacji w miejscu. Następnie pokaże podejście konstrukcji funkcjonalności.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a>Modyfikowanie drzewa XML  
 Napisanie kodu procedur tworzenia elementów z atrybutów i Usuń atrybutów, w następujący sposób:  
  
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
  
### <a name="functional-construction-approach"></a>Podejście funkcjonalności konstrukcji  
 Z kolei funkcjonalności podejście składa się z kodu w celu utworzenia nowego drzewa, pobierania i Wybieranie elementów i atrybutów z drzewa źródła i przekształcanie je jako odpowiednie, gdy są one dodawane do nowego drzewa. Podejście funkcjonalności wygląda następująco:  
  
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
  
 W tym przykładzie danych wyjściowych tego samego pliku XML, co w pierwszym przykładzie. Jednak zauważyć faktycznie widać Wynikowa struktura nowy kod XML w ujęciu funkcjonalności. Zostanie wyświetlony tworzenie `Root` element, kod, który pobiera `Child1` element z drzewa źródło i kod, który przekształca atrybutów z drzewa źródła do elementów w nowym drzewie.  
  
 Przykład funkcjonalności w takim przypadku nie jest żadnym krótszy niż pierwszym przykładzie, a nie jest to naprawdę any prostsze. Jednak jeśli masz wiele zmian, aby upewnić się na drzewo XML z systemem innym niż funkcjonalności podejście staną się dość złożone i nieco obtuse. Z kolei korzystając z funkcjonalności podejście, nadal właśnie formularz żądanego pliku XML osadzanie zapytania i wyrażenia, w celu ściągania w żądanej zawartości. Podejście funkcjonalności implikuje kod, który jest łatwiejsze w obsłudze.  
  
 Należy zauważyć, że w takim przypadku funkcjonalności podejście prawdopodobnie nie przeprowadza się bardzo, a także metoda manipulowania drzewa. Główny problem jest utworzoną za pomocą funkcjonalności podejście więcej krótkich okresów ważności obiektów. Jednak zależności jest skuteczne Jeśli funkcjonalności podejście pozwala na zwiększenie wydajności programisty.  
  
 To jest bardzo prosty przykład, ale służy do wyświetlenia różnicy w zasady klas dwa podejścia. Podejście funkcjonalności daje większą produktywność do transformacji dokumentów XML większy.  
  
## <a name="see-also"></a>Zobacz też  
 [Modyfikowanie drzew XML (LINQ do XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
