---
title: Przegląd LINQ to XML (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: 313abae6e8a82414ead90d5a4fdab7406492784f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785231"
---
# <a name="linq-to-xml-overview-c"></a>Przegląd LINQ to XML (C#)

LINQ to XML udostępnia interfejs programowania XML w pamięci, który wykorzystuje architekturę programu .NET Language-Integrated Query (LINQ). LINQ to XML używa możliwości platformy .NET i jest porównywalna z zaktualizowanym, przeprojektowanym Document Object Model (DOM) interfejsem programowania XML. 
 
Język XML został szeroko przyjęty jako sposób formatowania danych w wielu kontekstach. Na przykład można znaleźć XML w sieci Web, w plikach konfiguracyjnych, w Microsoft Office pliki programu Word i w bazach danych.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]to aktualne, przeprojektowane podejście do programowania w języku XML. Zapewnia możliwości modyfikacji dokumentów w pamięci Document Object Model (dom) i obsługuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażenia zapytań. Mimo że te wyrażenia zapytania różnią się od składni XPath, zapewniają podobną funkcjonalność.

## <a name="linq-to-xml-developers"></a>LINQ to XML deweloperzy

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]jest przeznaczony dla różnych deweloperów. W przypadku przeciętnego dewelopera, który po prostu chce uzyskać [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] coś gotowego, ułatwia tworzenie kodu XML, zapewniając środowisko zapytania podobne do SQL. Mając zaledwie kilka analiz, programiści mogą uczyć się pisać zwięzłe i zaawansowane zapytania w wybranym języku programowania.

Profesjonalne deweloperzy mogą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] znacznie zwiększyć swoją produktywność. Dzięki [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]programom mogą pisać mniej kod, który jest bardziej wyraźny, bardziej zwarty i bardziej wydajny. Mogą używać wyrażeń zapytania z wielu domen danych w tym samym czasie.

## <a name="what-is-linq-to-xml"></a>Co to jest LINQ to XML?

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]to interfejs programowania XML obsługujący LINQ, który umożliwia współpracę z danymi XML z poziomu języków programowania .NET Framework.

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]przypomina Document Object Model (DOM) w tym, że dokument XML jest umieszczany w pamięci. Możesz wysyłać zapytania i modyfikować dokument, a po zmodyfikowaniu go można zapisać do pliku lub serializować go i wysłać za pośrednictwem Internetu. Jednak różni [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] się od modelu DOM: Oferuje nowy model obiektów, który jest jaśniejszy i łatwiejszy w obejść i który korzysta z funkcji języka w C#systemie.

Najważniejszym zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest integracja z programem [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Ta Integracja umożliwia pisanie zapytań dotyczących dokumentu XML w pamięci w celu pobrania kolekcji elementów i atrybutów. Możliwość [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapytania jest porównywalna w funkcji (choć nie w składni) do XPath i XQuery. Integracja [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] programu w programie C# zapewnia lepsze wpisywanie, sprawdzanie czasu kompilowania i udoskonaloną obsługę debugera.

Inną zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest możliwość używania wyników zapytania jako parametrów do <xref:System.Xml.Linq.XElement> konstruktorów obiektów <xref:System.Xml.Linq.XAttribute> i umożliwia zaawansowane podejście do tworzenia drzew XML. Takie podejście, nazywane *konstrukcją funkcjonalną*, umożliwia deweloperom łatwe przekształcanie drzew XML z jednego kształtu do drugiego.

Można na przykład mieć typowe zamówienie zakupu XML, zgodnie z opisem w [przykładowym pliku XML: Typowe zamówienie zakupu (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md). Korzystając [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]z programu, można uruchomić następujące zapytanie w celu uzyskania wartości atrybutu numer części dla każdego elementu elementu w zamówieniu zakupu:

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

Można to zrobić ponownie w postaci składni metody:

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

Innym przykładem może być lista, posortowana według numeru części, dla elementów o wartości większej niż $100. Aby uzyskać te informacje, można uruchomić następujące zapytanie:

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

Można to zrobić ponownie w postaci składni metody:

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

Oprócz tych [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] funkcji program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] udostępnia udoskonalony interfejs programowania XML. Korzystając [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]z programu, można:

- Załaduj plik XML z [plików](how-to-load-xml-from-a-file.md) lub [strumieni](how-to-stream-xml-fragments-from-an-xmlreader.md).

- Serializacja XML do plików lub strumieni.

- Utwórz plik XML od podstaw przy użyciu konstrukcji funkcjonalnej.

- Kwerenda XML przy użyciu osi podobnej do XPath.

- Manipulowanie drzewem XML w pamięci za pomocą metod takich jak <xref:System.Xml.Linq.XContainer.Add%2A> <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, i <xref:System.Xml.Linq.XElement.SetValue%2A>.

- Sprawdzanie poprawności drzew XML przy użyciu XSD.

- Aby przekształcić drzewa XML z jednego kształtu na inny, należy użyć kombinacji tych funkcji.

## <a name="creating-xml-trees"></a>Tworzenie drzew XML

Jedną z najbardziej znaczących zalet programowania w programie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest łatwość tworzenia drzew XML. Na przykład, aby utworzyć małe drzewo XML, można napisać kod w następujący sposób:

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

Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XMLC#()](./creating-xml-trees-linq-to-xml-2.md).

## <a name="see-also"></a>Zobacz także

- [Odwołanie (LINQ to XML)](./reference-linq-to-xml.md)
- [LINQ to XML a DOM (C#)](./linq-to-xml-vs-dom.md)
- [LINQ to XML a inne technologie XML](./linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
