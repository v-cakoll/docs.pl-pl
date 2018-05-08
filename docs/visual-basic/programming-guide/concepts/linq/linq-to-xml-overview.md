---
title: LINQ do XML-Przegląd (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: 3818177c2ed14b1159b8e63e324894d7e89b72b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-xml-overview-visual-basic"></a>LINQ do XML-Przegląd (Visual Basic)
Powszechnie przyjęto XML jako sposób do formatowania danych w wielu sytuacjach. Na przykład XML można znaleźć w sieci Web, w plikach konfiguracji, pliki programu Microsoft Office Word i baz danych.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest aktualne, zmienioną podejście do programowania w języku XML. Udostępnia dokument w pamięci możliwości modyfikacji z modelu DOM (Document Object) i obsługuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażenia zapytań. Chociaż tych wyrażeń zapytania składniowo różnią się od wyrażenia XPath, zapewniają podobne funkcje.  
  
## <a name="linq-to-xml-developers"></a>LINQ do XML deweloperów  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Celem odmiany deweloperów. Dla średniej developer, który właśnie chce coś zrobić [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ułatwia XML, udostępniając środowisko zapytania, która jest podobna do bazy danych SQL. Tylko bit badań programistów dowiedzieć się do pisania zwięzły i zaawansowanych zapytań w języku programowania wyboru.  
  
 Professional deweloperzy mogą używać [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] znacznie zwiększyć ich wydajność. Z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], mogą zapisywać mniej kodu, który jest bardziej obszerne mniejszych i bardziej zaawansowanych. Wyrażenia zapytań z wielu domen danych użyciem w tym samym czasie.  
  
## <a name="what-is-linq-to-xml"></a>Co to jest LINQ do XML?  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to włączone LINQ, w pamięci XML programowania interfejs, który umożliwia pracę z językiem XML z poziomu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] języków programowania.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ma takie jak modelu DOM (Document Object) stwarza dokumentu XML do pamięci. Możesz zbadać i modyfikowanie dokumentu, a po jego modyfikacji można zapisać w pliku lub go serializować i wysłać go przez Internet. Jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] różni się od DOM: zapewnia nowy model, która jest mniejsza waga i łatwiejsze do pracy z, i który korzysta z funkcji języka w języku Visual Basic.  
  
 Najważniejszą korzyścią z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest integracji z [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Integracja ta umożliwia pisanie zapytań w dokumencie XML w pamięci można pobrać kolekcji elementów i atrybutów. Możliwości zapytania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można porównywać pod względem funkcji (ale nie w składni) XPath i XQuery. Integracja [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] w języku Visual Basic zapewnia silniejsze pisowni, kompilacji sprawdzanie i ulepszona obsługa debugera.  
  
 Inną zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest możliwość używania wyniki zapytania jako parametry <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> konstruktorów obiektów umożliwia wydajne podejście do tworzenia drzewa XML. Takie podejście, nazywany *funkcjonalności konstrukcji*, umożliwia deweloperom łatwe transformacji XML drzew z jednego kształtu do innego.  
  
 Na przykład może być typowe XML, zamówienie, zgodnie z opisem w [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348). Przy użyciu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można uruchomić następujące zapytanie, aby uzyskać części wartość atrybutu liczba dla każdego elementu w zamówieniu zakupu:  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 Innym przykładem może być listę posortowane według numer części elementów o wartości większej niż 100. Aby uzyskać te informacje, można uruchomić następujące zapytanie:  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 Oprócz wspomnianych [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] możliwości, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zawiera udoskonalony interfejs programowania XML. Przy użyciu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można wykonywać następujące czynności:  
  
-   Ładowanie XML z plików lub strumieni.  
  
-   Serializacji XML do plików i strumieni.  
  
-   Tworzenie XML od podstaw przy użyciu konstrukcji funkcjonalności.  
  
-   Badać kodu XML za pomocą notacji języka XPath osi.  
  
-   Manipulowanie drzewa XML w pamięci przy użyciu metod, takich jak <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, i <xref:System.Xml.Linq.XElement.SetValue%2A>.  
  
-   Sprawdź poprawność drzew XML za pomocą schematu XSD.  
  
-   Użyj kombinacji tych funkcji do transformacji XML drzew z jednego kształtu do innego.  
  
## <a name="creating-xml-trees"></a>Tworzenie XML drzewa  
 IOne najważniejszych zalet programowania w języku [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest łatwo tworzyć drzew XML. Na przykład aby utworzyć drzewo małych XML, można napisać kod w następujący sposób:  
  
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
  
 Kompilator Visual Basic tłumaczy literałów XML do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wywołania metody.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenia drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq>  
 [Wprowadzenie (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)  
 [Przegląd LINQ do XML w Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
