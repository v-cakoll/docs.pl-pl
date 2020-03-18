---
title: Omówienie LINQ do XML (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: 334788a50832b8fe42ecc9a3272dd71f2f2af4ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168418"
---
# <a name="linq-to-xml-overview-c"></a>Omówienie LINQ do XML (C#)

LINQ do XML zapewnia interfejs programowania XML w pamięci, który wykorzystuje .NET Language-Integrated Query (LINQ) Framework. LINQ do XML korzysta z funkcji .NET i jest porównywalny z zaktualizowanym, przeprojektowanym interfejsem programowania XML (Document Object Model).

XML został powszechnie przyjęty jako sposób formatowania danych w wielu kontekstach. Na przykład można znaleźć XML w sieci Web, w plikach konfiguracyjnych, w plikach programu Microsoft Office Word i w bazach danych.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]to aktualne, przeprojektowane podejście do programowania za pomocą xml. Zapewnia możliwości modyfikacji dokumentu w pamięci modelu obiektu dokumentu (DOM) i obsługuje wyrażenia zapytań LINQ. Mimo że te wyrażenia kwerendy są syntaktycznie różni się od XPath, zapewniają one podobne funkcje.

## <a name="linq-to-xml-developers"></a>LINQ programistom XML

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]skierowane do różnych deweloperów. Dla przeciętnego dewelopera, który po [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] prostu chce coś zrobić, ułatwia XML, zapewniając środowisko zapytania, które jest podobne do SQL. Z zaledwie odrobiną nauki, programiści mogą nauczyć się pisać zwięzłe i potężne zapytania w wybranym języku programowania.

Profesjonalni deweloperzy mogą znacznie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zwiększyć swoją produktywność. Dzięki [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], mogą pisać mniej kodu, który jest bardziej wyrazisty, bardziej kompaktowy i bardziej wydajny. Mogą używać wyrażeń zapytań z wielu domen danych w tym samym czasie.

## <a name="what-is-linq-to-xml"></a>Co to jest LINQ do XML?

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]jest interfejsem programowania XML z obsługą LINQ, który umożliwia pracę z xml z poziomu języków programowania .NET Framework.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]jest jak model obiektu dokumentu (DOM), ponieważ wprowadza dokument XML do pamięci. Można wysyłać zapytania i modyfikować dokument, a po jego zmodyfikowaniu można zapisać go w pliku lub serializować i wysyłać go przez Internet. Jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] różni się od DOM: Zapewnia nowy model obiektu, który jest lżejszy i łatwiejszy w pracy i który wykorzystuje funkcje języka w języku C#.

Najważniejszą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zaletą jest jego integracja z language-Integrated Query (LINQ). Ta integracja umożliwia pisanie zapytań w dokumencie XML w pamięci, aby pobrać kolekcje elementów i atrybutów. Możliwość zapytania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest porównywalna w funkcjonalności (chociaż nie w składni) do XPath i XQuery. Integracja LINQ w języku C# zapewnia silniejsze pisanie, sprawdzanie czasu kompilacji i ulepszoną obsługę debugera.

Inną zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest możliwość używania wyników kwerendy <xref:System.Xml.Linq.XAttribute> jako parametry i <xref:System.Xml.Linq.XElement> konstruktorów obiektów umożliwia zaawansowane podejście do tworzenia drzew XML. Takie podejście, zwane *konstrukcją funkcjonalną,* umożliwia deweloperom łatwe przekształcanie drzew XML z jednego kształtu do drugiego.

Na przykład może mieć typowe zamówienie zakupu XML, zgodnie z opisem w [przykładowym pliku XML: Typowe zamówienie zakupu (LINQ do XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md). Za [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]pomocą , można uruchomić następujące zapytanie, aby uzyskać wartość atrybutu numeru części dla każdego elementu elementu w zamówieniu zakupu:

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

Można to przepisać w formularzu składni metody:

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

W innym przykładzie można wyświetlić listę elementów posortowanych według numeru części o wartości większej niż 100 USD. Aby uzyskać te informacje, można uruchomić następujące zapytanie:

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

Ponownie, można to przepisać w formularzu składni metody:

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

Oprócz tych funkcji LINQ [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapewnia ulepszony interfejs programowania XML. Za [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]pomocą , można:

- Załaduj xml z [plików](how-to-load-xml-from-a-file.md) lub [strumieni](how-to-stream-xml-fragments-from-an-xmlreader.md).

- Serializuj XML na pliki lub strumienie.

- Tworzenie XML od podstaw przy użyciu funkcjonalnej konstrukcji.

- Zapytanie XML przy użyciu osi xpath-like.

- Manipuluj drzewem XML w pamięci, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>używając <xref:System.Xml.Linq.XElement.SetValue%2A>metod takich jak <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, , i .

- Sprawdź poprawność drzew XML przy użyciu XSD.

- Użyj kombinacji tych funkcji, aby przekształcić drzewa XML z jednego kształtu w inny.

## <a name="creating-xml-trees"></a>Tworzenie drzew XML

Jedną z najważniejszych zalet programowania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest to, że łatwo jest tworzyć drzewa XML. Na przykład, aby utworzyć małe drzewo XML, można napisać kod w następujący sposób:

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

Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML (C#)](./creating-xml-trees-linq-to-xml-2.md).

## <a name="see-also"></a>Zobacz też

- [Odwołanie (LINQ to XML)](./reference-linq-to-xml.md)
- [LINQ do XML vs. DOM (C#)](./linq-to-xml-vs-dom.md)
- [LINQ do XML w porównaniu z innymi technologiami XML](./linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
