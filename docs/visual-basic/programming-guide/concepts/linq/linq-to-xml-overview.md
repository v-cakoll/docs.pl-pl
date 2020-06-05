---
title: LINQ to XML — przegląd
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: afdec54ac05bb4a631de7fdb599123ffe964c443
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368742"
---
# <a name="linq-to-xml-overview-visual-basic"></a>Przegląd LINQ to XML (Visual Basic)
Język XML został szeroko przyjęty jako sposób formatowania danych w wielu kontekstach. Na przykład można znaleźć XML w sieci Web, w plikach konfiguracyjnych, w Microsoft Office pliki programu Word i w bazach danych.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]to aktualne, przeprojektowane podejście do programowania w języku XML. Zapewnia możliwości modyfikacji dokumentu w pamięci Document Object Model (DOM) i obsługuje wyrażenia zapytania LINQ. Mimo że te wyrażenia zapytania różnią się od składni XPath, zapewniają podobną funkcjonalność.  
  
## <a name="linq-to-xml-developers"></a>LINQ to XML deweloperzy  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]jest przeznaczony dla różnych deweloperów. W przypadku przeciętnego dewelopera, który po prostu chce uzyskać coś gotowego, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ułatwia tworzenie kodu XML, zapewniając środowisko zapytania podobne do SQL. Mając zaledwie kilka analiz, programiści mogą uczyć się pisać zwięzłe i zaawansowane zapytania w wybranym języku programowania.  
  
 Profesjonalne deweloperzy mogą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] znacznie zwiększyć swoją produktywność. Dzięki [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programom mogą pisać mniej kod, który jest bardziej wyraźny, bardziej zwarty i bardziej wydajny. Mogą używać wyrażeń zapytania z wielu domen danych w tym samym czasie.  
  
## <a name="what-is-linq-to-xml"></a>Co to jest LINQ to XML?  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]to interfejs programowania XML obsługujący LINQ, który umożliwia współpracę z danymi XML z poziomu języków programowania .NET Framework.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]przypomina Document Object Model (DOM) w tym, że dokument XML jest umieszczany w pamięci. Możesz wysyłać zapytania i modyfikować dokument, a po zmodyfikowaniu go można zapisać do pliku lub serializować go i wysłać za pośrednictwem Internetu. Jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] różni się od modelu DOM: udostępnia nowy model obiektów, który jest jaśniejszy i ułatwia pracę z programem, a także korzysta z funkcji języka w Visual Basic.  
  
 Najważniejsze korzyści wynikające z tej [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] integracji to integracja ze standardem Language-Integrated Query (LINQ). Ta Integracja umożliwia pisanie zapytań dotyczących dokumentu XML w pamięci w celu pobrania kolekcji elementów i atrybutów. Możliwość zapytania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest porównywalna w funkcji (choć nie w składni) do XPath i XQuery. Integracja LINQ w Visual Basic zapewnia silniejsze wpisywanie, sprawdzanie czasu kompilowania i udoskonaloną obsługę debugera.  
  
 Inną zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest możliwość używania wyników zapytania jako parametrów do <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> konstruktorów obiektów i umożliwia zaawansowane podejście do tworzenia drzew XML. Takie podejście, nazywane *konstrukcją funkcjonalną*, umożliwia deweloperom łatwe przekształcanie drzew XML z jednego kształtu do drugiego.  
  
 Na przykład może istnieć typowa kolejność zakupu XML, zgodnie z opisem w [przykładowym pliku XML: typowe zamówienie zakupu (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml.md). Korzystając z programu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , można uruchomić następujące zapytanie w celu uzyskania wartości atrybutu numer części dla każdego elementu elementu w zamówieniu zakupu:  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 Innym przykładem może być lista, posortowana według numeru części, dla elementów o wartości większej niż $100. Aby uzyskać te informacje, można uruchomić następujące zapytanie:  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 Oprócz tych funkcji LINQ program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] udostępnia udoskonalony interfejs programowania XML. Korzystając [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z programu, można:  
  
- Załaduj plik XML z plików lub strumieni.  
  
- Serializacja XML do plików lub strumieni.  
  
- Utwórz plik XML od podstaw przy użyciu konstrukcji funkcjonalnej.  
  
- Kwerenda XML przy użyciu osi podobnej do XPath.  
  
- Manipulowanie drzewem XML w pamięci za pomocą metod takich jak <xref:System.Xml.Linq.XContainer.Add%2A> , <xref:System.Xml.Linq.XNode.Remove%2A> , <xref:System.Xml.Linq.XNode.ReplaceWith%2A> i <xref:System.Xml.Linq.XElement.SetValue%2A> .  
  
- Sprawdzanie poprawności drzew XML przy użyciu XSD.  
  
- Aby przekształcić drzewa XML z jednego kształtu na inny, należy użyć kombinacji tych funkcji.  
  
## <a name="creating-xml-trees"></a>Tworzenie drzew XML  
 IOne z najbardziej znaczącymi zaletami programowania w programie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] polega na tym, że tworzenie drzew XML jest łatwe. Na przykład, aby utworzyć małe drzewo XML, można napisać kod w następujący sposób:  
  
```vb  
Dim contacts = _  
<Contacts>  
    <Contact>  
        <Name>Patrick Hines</Name>  
        <Phone Type="Home">206-555-0144</Phone>  
        <Phone Type="Work">425-555-0145</Phone>  
        <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
        </Address>  
    </Contact>  
</Contacts>  
```  
  
 Kompilator Visual Basic tłumaczy literały XML na [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wywołania metod.  
  
 Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML (Visual Basic)](creating-xml-trees.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq>
- [Wprowadzenie (LINQ to XML)](getting-started-linq-to-xml.md)
- [Przegląd LINQ to XML w Visual Basic](../../language-features/xml/overview-of-linq-to-xml.md)
- [XML](../../language-features/xml/index.md)
