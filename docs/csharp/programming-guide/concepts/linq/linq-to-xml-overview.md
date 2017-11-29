---
title: "LINQ do XML-Przegląd (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1c66e87ecc72bf711dfda33cd7c0ea35f126c1e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-xml-overview-c"></a>LINQ do XML-Przegląd (C#)
Powszechnie przyjęto XML jako sposób do formatowania danych w wielu sytuacjach. Na przykład XML można znaleźć w sieci Web, w plikach konfiguracji, pliki programu Microsoft Office Word i baz danych.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]jest aktualne, zmienioną podejście do programowania w języku XML. Udostępnia dokument w pamięci możliwości modyfikacji z modelu DOM (Document Object) i obsługuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażenia zapytań. Chociaż tych wyrażeń zapytania składniowo różnią się od wyrażenia XPath, zapewniają podobne funkcje.  
  
## <a name="linq-to-xml-developers"></a>LINQ do XML deweloperów  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Celem odmiany deweloperów. Dla średniej developer, który właśnie chce coś zrobić [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ułatwia XML, udostępniając środowisko zapytania, która jest podobna do bazy danych SQL. Tylko bit badań programistów dowiedzieć się do pisania zwięzły i zaawansowanych zapytań w języku programowania wyboru.  
  
 Professional deweloperzy mogą używać [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] znacznie zwiększyć ich wydajność. Z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], mogą zapisywać mniej kodu, który jest bardziej obszerne mniejszych i bardziej zaawansowanych. Wyrażenia zapytań z wielu domen danych użyciem w tym samym czasie.  
  
## <a name="what-is-linq-to-xml"></a>Co to jest LINQ do XML?  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]to włączone LINQ, w pamięci XML programowania interfejs, który umożliwia pracę z językiem XML z poziomu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] języków programowania.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ma takie jak modelu DOM (Document Object) stwarza dokumentu XML do pamięci. Możesz zbadać i modyfikowanie dokumentu, a po jego modyfikacji można zapisać w pliku lub go serializować i wysłać go przez Internet. Jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] różni się od DOM: zapewnia nowy model, która jest mniejsza waga i łatwiejsze do pracy z, i który korzysta z funkcji języka w języku C#.  
  
 Najważniejszą korzyścią z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest integracji z [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Integracja ta umożliwia pisanie zapytań w dokumencie XML w pamięci można pobrać kolekcji elementów i atrybutów. Możliwości zapytania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można porównywać pod względem funkcji (ale nie w składni) XPath i XQuery. Integracja [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] w języku C# zapewnia silniejsze pisowni, kompilacji sprawdzanie i ulepszona obsługa debugera.  
  
 Inną zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest możliwość używania wyniki zapytania jako parametry <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> konstruktorów obiektów umożliwia wydajne podejście do tworzenia drzewa XML. Takie podejście, nazywany *funkcjonalności konstrukcji*, umożliwia deweloperom łatwe transformacji XML drzew z jednego kształtu do innego.  
  
 Na przykład może być typowe XML, zamówienie, zgodnie z opisem w [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348). Przy użyciu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można uruchomić następujące zapytanie, aby uzyskać części wartość atrybutu liczba dla każdego elementu w zamówieniu zakupu:  
  
```csharp  
IEnumerable<string> partNos =  
from item in purchaseOrder.Descendants("Item")  
select (string) item.Attribute("PartNumber");  
```  
  
 Innym przykładem może być listę posortowane według numer części elementów o wartości większej niż 100. Aby uzyskać te informacje, można uruchomić następujące zapytanie:  
  
```csharp  
IEnumerable<XElement> partNos =  
from item in purchaseOrder.Descendants("Item")  
where (int) item.Element("Quantity") *  
    (decimal) item.Element("USPrice") > 100  
orderby (string)item.Element("PartNumber")  
select item;  
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
 Jedną z najważniejszych zalet programowania w języku [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest łatwo tworzyć drzew XML. Na przykład aby utworzyć drzewo małych XML, można napisać kod w następujący sposób:  
  
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
  
 Aby uzyskać więcej informacji, zobacz [tworzenia drzewa XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq>  
 [Wprowadzenie (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
