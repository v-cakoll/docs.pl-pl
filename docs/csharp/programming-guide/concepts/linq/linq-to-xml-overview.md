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
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="b8d1a-102">Omówienie LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b8d1a-102">LINQ to XML Overview (C#)</span></span>

<span data-ttu-id="b8d1a-103">LINQ do XML zapewnia interfejs programowania XML w pamięci, który wykorzystuje .NET Language-Integrated Query (LINQ) Framework.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-103">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="b8d1a-104">LINQ do XML korzysta z funkcji .NET i jest porównywalny z zaktualizowanym, przeprojektowanym interfejsem programowania XML (Document Object Model).</span><span class="sxs-lookup"><span data-stu-id="b8d1a-104">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span>

<span data-ttu-id="b8d1a-105">XML został powszechnie przyjęty jako sposób formatowania danych w wielu kontekstach.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-105">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="b8d1a-106">Na przykład można znaleźć XML w sieci Web, w plikach konfiguracyjnych, w plikach programu Microsoft Office Word i w bazach danych.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-106">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b8d1a-107">to aktualne, przeprojektowane podejście do programowania za pomocą xml.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-107">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="b8d1a-108">Zapewnia możliwości modyfikacji dokumentu w pamięci modelu obiektu dokumentu (DOM) i obsługuje wyrażenia zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-108">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports LINQ query expressions.</span></span> <span data-ttu-id="b8d1a-109">Mimo że te wyrażenia kwerendy są syntaktycznie różni się od XPath, zapewniają one podobne funkcje.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-109">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="b8d1a-110">LINQ programistom XML</span><span class="sxs-lookup"><span data-stu-id="b8d1a-110">LINQ to XML Developers</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b8d1a-111">skierowane do różnych deweloperów.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-111">targets a variety of developers.</span></span> <span data-ttu-id="b8d1a-112">Dla przeciętnego dewelopera, który po [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] prostu chce coś zrobić, ułatwia XML, zapewniając środowisko zapytania, które jest podobne do SQL.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-112">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="b8d1a-113">Z zaledwie odrobiną nauki, programiści mogą nauczyć się pisać zwięzłe i potężne zapytania w wybranym języku programowania.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-113">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="b8d1a-114">Profesjonalni deweloperzy mogą znacznie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zwiększyć swoją produktywność.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-114">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="b8d1a-115">Dzięki [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], mogą pisać mniej kodu, który jest bardziej wyrazisty, bardziej kompaktowy i bardziej wydajny.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-115">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="b8d1a-116">Mogą używać wyrażeń zapytań z wielu domen danych w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-116">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="what-is-linq-to-xml"></a><span data-ttu-id="b8d1a-117">Co to jest LINQ do XML?</span><span class="sxs-lookup"><span data-stu-id="b8d1a-117">What Is LINQ to XML?</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b8d1a-118">jest interfejsem programowania XML z obsługą LINQ, który umożliwia pracę z xml z poziomu języków programowania .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-118">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET Framework programming languages.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="b8d1a-119">jest jak model obiektu dokumentu (DOM), ponieważ wprowadza dokument XML do pamięci.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-119">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="b8d1a-120">Można wysyłać zapytania i modyfikować dokument, a po jego zmodyfikowaniu można zapisać go w pliku lub serializować i wysyłać go przez Internet.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-120">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="b8d1a-121">Jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] różni się od DOM: Zapewnia nowy model obiektu, który jest lżejszy i łatwiejszy w pracy i który wykorzystuje funkcje języka w języku C#.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-121">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>

<span data-ttu-id="b8d1a-122">Najważniejszą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zaletą jest jego integracja z language-Integrated Query (LINQ).</span><span class="sxs-lookup"><span data-stu-id="b8d1a-122">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="b8d1a-123">Ta integracja umożliwia pisanie zapytań w dokumencie XML w pamięci, aby pobrać kolekcje elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-123">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="b8d1a-124">Możliwość zapytania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest porównywalna w funkcjonalności (chociaż nie w składni) do XPath i XQuery.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-124">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="b8d1a-125">Integracja LINQ w języku C# zapewnia silniejsze pisanie, sprawdzanie czasu kompilacji i ulepszoną obsługę debugera.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-125">The integration of LINQ in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="b8d1a-126">Inną zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest możliwość używania wyników kwerendy <xref:System.Xml.Linq.XAttribute> jako parametry i <xref:System.Xml.Linq.XElement> konstruktorów obiektów umożliwia zaawansowane podejście do tworzenia drzew XML.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-126">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="b8d1a-127">Takie podejście, zwane *konstrukcją funkcjonalną,* umożliwia deweloperom łatwe przekształcanie drzew XML z jednego kształtu do drugiego.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-127">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="b8d1a-128">Na przykład może mieć typowe zamówienie zakupu XML, zgodnie z opisem w [przykładowym pliku XML: Typowe zamówienie zakupu (LINQ do XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="b8d1a-128">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="b8d1a-129">Za [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]pomocą , można uruchomić następujące zapytanie, aby uzyskać wartość atrybutu numeru części dla każdego elementu elementu w zamówieniu zakupu:</span><span class="sxs-lookup"><span data-stu-id="b8d1a-129">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

<span data-ttu-id="b8d1a-130">Można to przepisać w formularzu składni metody:</span><span class="sxs-lookup"><span data-stu-id="b8d1a-130">This can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="b8d1a-131">W innym przykładzie można wyświetlić listę elementów posortowanych według numeru części o wartości większej niż 100 USD.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-131">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="b8d1a-132">Aby uzyskać te informacje, można uruchomić następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="b8d1a-132">To obtain this information, you could run the following query:</span></span>

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

<span data-ttu-id="b8d1a-133">Ponownie, można to przepisać w formularzu składni metody:</span><span class="sxs-lookup"><span data-stu-id="b8d1a-133">Again, this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="b8d1a-134">Oprócz tych funkcji LINQ [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zapewnia ulepszony interfejs programowania XML.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-134">In addition to these LINQ capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="b8d1a-135">Za [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]pomocą , można:</span><span class="sxs-lookup"><span data-stu-id="b8d1a-135">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>

- <span data-ttu-id="b8d1a-136">Załaduj xml z [plików](how-to-load-xml-from-a-file.md) lub [strumieni](how-to-stream-xml-fragments-from-an-xmlreader.md).</span><span class="sxs-lookup"><span data-stu-id="b8d1a-136">Load XML from [files](how-to-load-xml-from-a-file.md) or [streams](how-to-stream-xml-fragments-from-an-xmlreader.md).</span></span>

- <span data-ttu-id="b8d1a-137">Serializuj XML na pliki lub strumienie.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-137">Serialize XML to files or streams.</span></span>

- <span data-ttu-id="b8d1a-138">Tworzenie XML od podstaw przy użyciu funkcjonalnej konstrukcji.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-138">Create XML from scratch by using functional construction.</span></span>

- <span data-ttu-id="b8d1a-139">Zapytanie XML przy użyciu osi xpath-like.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-139">Query XML using XPath-like axes.</span></span>

- <span data-ttu-id="b8d1a-140">Manipuluj drzewem XML w pamięci, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>używając <xref:System.Xml.Linq.XElement.SetValue%2A>metod takich jak <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, , i .</span><span class="sxs-lookup"><span data-stu-id="b8d1a-140">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>

- <span data-ttu-id="b8d1a-141">Sprawdź poprawność drzew XML przy użyciu XSD.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-141">Validate XML trees using XSD.</span></span>

- <span data-ttu-id="b8d1a-142">Użyj kombinacji tych funkcji, aby przekształcić drzewa XML z jednego kształtu w inny.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-142">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="creating-xml-trees"></a><span data-ttu-id="b8d1a-143">Tworzenie drzew XML</span><span class="sxs-lookup"><span data-stu-id="b8d1a-143">Creating XML Trees</span></span>

<span data-ttu-id="b8d1a-144">Jedną z najważniejszych zalet programowania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest to, że łatwo jest tworzyć drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="b8d1a-144">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="b8d1a-145">Na przykład, aby utworzyć małe drzewo XML, można napisać kod w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="b8d1a-145">For example, to create a small XML tree, you can write code as follows:</span></span>

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

<span data-ttu-id="b8d1a-146">Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML (C#)](./creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="b8d1a-146">For more information, see [Creating XML Trees (C#)](./creating-xml-trees-linq-to-xml-2.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b8d1a-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8d1a-147">See also</span></span>

- [<span data-ttu-id="b8d1a-148">Odwołanie (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="b8d1a-148">Reference (LINQ to XML)</span></span>](./reference-linq-to-xml.md)
- [<span data-ttu-id="b8d1a-149">LINQ do XML vs. DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="b8d1a-149">LINQ to XML vs. DOM (C#)</span></span>](./linq-to-xml-vs-dom.md)
- [<span data-ttu-id="b8d1a-150">LINQ do XML w porównaniu z innymi technologiami XML</span><span class="sxs-lookup"><span data-stu-id="b8d1a-150">LINQ to XML vs. Other XML Technologies</span></span>](./linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
