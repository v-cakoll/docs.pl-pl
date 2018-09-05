---
title: LINQ to XML — Przegląd (C#)
ms.date: 07/20/2015
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: 5b557c95993d7f1e907a8eb6ef1e5ec23a2988ab
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43539073"
---
# <a name="linq-to-xml-overview-c"></a>LINQ to XML — Przegląd (C#)
XML ma powszechnie zaakceptowany jako sposób na formatowanie danych w wielu kontekstach. Na przykład możesz znaleźć XML w sieci Web, w plikach konfiguracji, pliki programu Microsoft Office Word i baz danych.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to aktualne, przeprojektowana podejście do programowania w języku XML. Zawiera on dokumentów w pamięci możliwości modyfikacji Document Object Model (DOM) i obsługuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach zapytań. Mimo że te wyrażenia kwerendy są składniowo różni się od XPath, zapewniają podobne funkcje.  
  
## <a name="linq-to-xml-developers"></a>LINQ to XML deweloperów  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest przeznaczony dla różnych deweloperów. Dla średniej deweloperem właśnie coś zrobić [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ułatwia XML, zapewniając środowisko zapytania, która jest podobna do bazy danych SQL. Po prostu bit analiza programistów można Dowiedz się, jak pisać zapytania zwięzły i Zaawansowane w ich dowolny język programowania.  
  
 Profesjonalni deweloperzy mogą używać [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] znacznie zwiększyć ich wydajność. Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], mogą zapisywać mniejszej ilości kodu, który jest bardziej ekspresyjnego, bardziej zwarty i bardziej wydajne. Ich użyć wyrażeń zapytania z wieloma domenami danych, w tym samym czasie.  
  
## <a name="what-is-linq-to-xml"></a>Co to jest LINQ to XML?  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to włączone LINQ, wewnątrzpamięciowe XML programowania interfejs, który umożliwia pracę z danymi XML, z poziomu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] języków programowania.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest jak modelu DOM (Document Object) zapewnia dokumentu XML do pamięci. Można wykonywać zapytania i modyfikować dokument, a po jego modyfikacji można zapisać w pliku lub serializować go i wysyłać je przez Internet. Jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] różni się od modelu DOM: zapewnia nowy model obiektu, który jest mniejsza waga i łatwiej pracować z, i który korzysta z funkcji języka C#.  
  
 Najważniejszą zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest integracji z [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Ta integracja umożliwia pisanie zapytań dotyczących dokumentu XML w pamięci, aby pobierać kolekcje elementów i atrybutów. Możliwości zapytania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można porównywać pod względem funkcji (ale nie w składni) XPath i XQuery. Integracja [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] w języku C# zapewnia lepsze Pisownia, kompilacji sprawdzenie i ulepszona obsługa debugera.  
  
 Inną zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest możliwość używania wyników zapytania jako parametry <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> konstruktorach obiektów umożliwia wydajne podejście do tworzenia drzew XML. Takie podejście, nazywane *konstrukcja funkcjonalna*, umożliwia deweloperom łatwe Przekształcanie drzew XML z jednego kształtu do innego.  
  
 Na przykład, Niewykluczone, że typowy XML, zamówienie zakupu, zgodnie z opisem w [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md). Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można uruchomić następujące zapytanie, aby uzyskać część wartości atrybutu numeru dla każdego elementu w porządku zakupu:  
  
```csharp  
IEnumerable<string> partNos =  
from item in purchaseOrder.Descendants("Item")  
select (string) item.Attribute("PartNumber");  
```  
  
 Inny przykład, możesz zechcieć listę, posortowane według numer części, elementów o wartości większej niż 100 USD. Aby uzyskać te informacje, można uruchomić następujące zapytanie:  
  
```csharp  
IEnumerable<XElement> partNos =  
from item in purchaseOrder.Descendants("Item")  
where (int) item.Element("Quantity") *  
    (decimal) item.Element("USPrice") > 100  
orderby (string)item.Element("PartNumber")  
select item;  
```  
  
 Oprócz wspomnianych [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] możliwości [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] udostępnia Ulepszony interfejs programowania XML. Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], możesz:  
  
-   Ładowanie kodu XML z plików i strumieni.  
  
-   Serializacji XML do plików i strumieni.  
  
-   Tworzenie XML od podstaw przy użyciu konstrukcja funkcjonalna.  
  
-   Zapytanie XML przy użyciu notacji XPath osi.  
  
-   Manipulowanie drzewa XML w pamięci przy użyciu metod, takich jak <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, i <xref:System.Xml.Linq.XElement.SetValue%2A>.  
  
-   Sprawdź poprawność drzew XML przy użyciu XSD.  
  
-   Kombinacja tych funkcji umożliwia przekształcanie drzew XML z jednego kształtu do innego.  
  
## <a name="creating-xml-trees"></a>Tworzenie drzew XML  
 Jedną z najbardziej znaczących korzyści wynikające z programowania, korzystając z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest łatwe tworzenie drzew XML. Na przykład do tworzenia małych drzewa XML, należy można napisać kod w następujący sposób:  
  
```csharp  
XElement contacts =  
new XElement("Contacts",  
    new XElement("Contact",  
        new XElement("Name", "Patrick Hines"),  
        new XElement("Phone", "206-555-0144",   
            new XAttribute("Type", "Home")),  
        new XElement("phone", "425-555-0145",  
            new XAttribute("Type", "Work")),  
        new XElement("Address",  
            new XElement("Street1", "123 Main St"),  
            new XElement("City", "Mercer Island"),  
            new XElement("State", "WA"),  
            new XElement("Postal", "68042")  
        )  
    )  
);  
```  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq>  
- [Wprowadzenie (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
