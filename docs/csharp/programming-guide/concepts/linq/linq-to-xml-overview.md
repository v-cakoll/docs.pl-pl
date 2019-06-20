---
title: LINQ to XML — Przegląd (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: 6a7d681b52bbc6ce515e2202f3f448ce4ba79ced
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267960"
---
# <a name="linq-to-xml-overview-c"></a>LINQ to XML — Przegląd (C#)

LINQ to XML udostępnia interfejs programowania XML w pamięci, który wykorzystuje platformę .NET Language-Integrated Query (LINQ). LINQ to XML używa funkcji platformy .NET i jest porównywalna do zaktualizowanych, przeprojektowana modelu DOM (Document Object) interfejs programowania XML. 
 
XML ma powszechnie zaakceptowany jako sposób na formatowanie danych w wielu kontekstach. Na przykład możesz znaleźć XML w sieci Web, w plikach konfiguracji, pliki programu Microsoft Office Word i baz danych.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to aktualne, przeprojektowana podejście do programowania w języku XML. Zawiera on dokumentów w pamięci możliwości modyfikacji Document Object Model (DOM) i obsługuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach zapytań. Mimo że te wyrażenia kwerendy są składniowo różni się od XPath, zapewniają podobne funkcje.

## <a name="linq-to-xml-developers"></a>LINQ to XML deweloperów

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest przeznaczony dla różnych deweloperów. Dla średniej deweloperem właśnie coś zrobić [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ułatwia XML, zapewniając środowisko zapytania, która jest podobna do bazy danych SQL. Po prostu bit analiza programistów można Dowiedz się, jak pisać zapytania zwięzły i Zaawansowane w ich dowolny język programowania.

Profesjonalni deweloperzy mogą używać [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] znacznie zwiększyć ich wydajność. Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], mogą zapisywać mniejszej ilości kodu, który jest bardziej ekspresyjnego, bardziej zwarty i bardziej wydajne. Ich użyć wyrażeń zapytania z wieloma domenami danych, w tym samym czasie.

## <a name="what-is-linq-to-xml"></a>Co to jest LINQ to XML?

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest włączone LINQ, wewnątrzpamięciowe XML programowania interfejsem, który umożliwia pracę z danymi XML w programie .NET Framework w językach programowania.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest jak modelu DOM (Document Object) zapewnia dokumentu XML do pamięci. Można wykonywać zapytania i modyfikować dokument, a po jego modyfikacji można zapisać w pliku lub serializować go i wysyłać je przez Internet. Jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] różni się od modelu DOM: Zapewnia nowy model obiektu, który jest mniejsza waga i łatwiej pracować z, i który korzysta z funkcji języka w C#.

Najważniejszą zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest integracji z [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Ta integracja umożliwia pisanie zapytań dotyczących dokumentu XML w pamięci, aby pobierać kolekcje elementów i atrybutów. Możliwości zapytania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można porównywać pod względem funkcji (ale nie w składni) XPath i XQuery. Integracja [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] w języku C# zapewnia lepsze Pisownia, kompilacji sprawdzenie i ulepszona obsługa debugera.

Inną zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest możliwość używania wyników zapytania jako parametry <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> konstruktorach obiektów umożliwia wydajne podejście do tworzenia drzew XML. Takie podejście, nazywane *konstrukcja funkcjonalna*, umożliwia deweloperom łatwe Przekształcanie drzew XML z jednego kształtu do innego.

Na przykład, Niewykluczone, że typowy XML, zamówienie zakupu, zgodnie z opisem w [przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md). Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można uruchomić następujące zapytanie, aby uzyskać część wartości atrybutu numeru dla każdego elementu w porządku zakupu:

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

Można to inaczej w formularzu składni metody:

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

Inny przykład, możesz zechcieć listę, posortowane według numer części, elementów o wartości większej niż 100 USD. Aby uzyskać te informacje, można uruchomić następujące zapytanie:

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

Ponownie to może zostać przepisany forma składni metody:

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

Oprócz wspomnianych [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] możliwości [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] udostępnia Ulepszony interfejs programowania XML. Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], możesz:

- Ładowanie kodu XML z [pliki](how-to-load-xml-from-a-file.md) lub [strumieni](how-to-stream-xml-fragments-from-an-xmlreader.md).

- Serializacji XML do plików i strumieni.

- Tworzenie XML od podstaw przy użyciu konstrukcja funkcjonalna.

- Zapytanie XML przy użyciu notacji XPath osi.

- Manipulowanie drzewa XML w pamięci przy użyciu metod, takich jak <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, i <xref:System.Xml.Linq.XElement.SetValue%2A>.

- Sprawdź poprawność drzew XML przy użyciu XSD.

- Kombinacja tych funkcji umożliwia przekształcanie drzew XML z jednego kształtu do innego.

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

Aby uzyskać więcej informacji, zobacz [tworzenie drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).

## <a name="see-also"></a>Zobacz także

- [Odwołanie (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/reference-linq-to-xml.md)
- [LINQ to XML a MODELU DOM (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [LINQ to XML a inne technologie XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
