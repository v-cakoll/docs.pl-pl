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
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="63db9-102">LINQ to XML — Przegląd (C#)</span><span class="sxs-lookup"><span data-stu-id="63db9-102">LINQ to XML Overview (C#)</span></span>

<span data-ttu-id="63db9-103">LINQ to XML udostępnia interfejs programowania XML w pamięci, który wykorzystuje platformę .NET Language-Integrated Query (LINQ).</span><span class="sxs-lookup"><span data-stu-id="63db9-103">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="63db9-104">LINQ to XML używa funkcji platformy .NET i jest porównywalna do zaktualizowanych, przeprojektowana modelu DOM (Document Object) interfejs programowania XML.</span><span class="sxs-lookup"><span data-stu-id="63db9-104">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span> 
 
<span data-ttu-id="63db9-105">XML ma powszechnie zaakceptowany jako sposób na formatowanie danych w wielu kontekstach.</span><span class="sxs-lookup"><span data-stu-id="63db9-105">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="63db9-106">Na przykład możesz znaleźć XML w sieci Web, w plikach konfiguracji, pliki programu Microsoft Office Word i baz danych.</span><span class="sxs-lookup"><span data-stu-id="63db9-106">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="63db9-107">to aktualne, przeprojektowana podejście do programowania w języku XML.</span><span class="sxs-lookup"><span data-stu-id="63db9-107">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="63db9-108">Zawiera on dokumentów w pamięci możliwości modyfikacji Document Object Model (DOM) i obsługuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach zapytań.</span><span class="sxs-lookup"><span data-stu-id="63db9-108">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="63db9-109">Mimo że te wyrażenia kwerendy są składniowo różni się od XPath, zapewniają podobne funkcje.</span><span class="sxs-lookup"><span data-stu-id="63db9-109">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="63db9-110">LINQ to XML deweloperów</span><span class="sxs-lookup"><span data-stu-id="63db9-110">LINQ to XML Developers</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="63db9-111">jest przeznaczony dla różnych deweloperów.</span><span class="sxs-lookup"><span data-stu-id="63db9-111">targets a variety of developers.</span></span> <span data-ttu-id="63db9-112">Dla średniej deweloperem właśnie coś zrobić [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ułatwia XML, zapewniając środowisko zapytania, która jest podobna do bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="63db9-112">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="63db9-113">Po prostu bit analiza programistów można Dowiedz się, jak pisać zapytania zwięzły i Zaawansowane w ich dowolny język programowania.</span><span class="sxs-lookup"><span data-stu-id="63db9-113">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="63db9-114">Profesjonalni deweloperzy mogą używać [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] znacznie zwiększyć ich wydajność.</span><span class="sxs-lookup"><span data-stu-id="63db9-114">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="63db9-115">Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], mogą zapisywać mniejszej ilości kodu, który jest bardziej ekspresyjnego, bardziej zwarty i bardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="63db9-115">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="63db9-116">Ich użyć wyrażeń zapytania z wieloma domenami danych, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="63db9-116">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="what-is-linq-to-xml"></a><span data-ttu-id="63db9-117">Co to jest LINQ to XML?</span><span class="sxs-lookup"><span data-stu-id="63db9-117">What Is LINQ to XML?</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="63db9-118">jest włączone LINQ, wewnątrzpamięciowe XML programowania interfejsem, który umożliwia pracę z danymi XML w programie .NET Framework w językach programowania.</span><span class="sxs-lookup"><span data-stu-id="63db9-118">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET Framework programming languages.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="63db9-119">jest jak modelu DOM (Document Object) zapewnia dokumentu XML do pamięci.</span><span class="sxs-lookup"><span data-stu-id="63db9-119">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="63db9-120">Można wykonywać zapytania i modyfikować dokument, a po jego modyfikacji można zapisać w pliku lub serializować go i wysyłać je przez Internet.</span><span class="sxs-lookup"><span data-stu-id="63db9-120">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="63db9-121">Jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] różni się od modelu DOM: Zapewnia nowy model obiektu, który jest mniejsza waga i łatwiej pracować z, i który korzysta z funkcji języka w C#.</span><span class="sxs-lookup"><span data-stu-id="63db9-121">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>

<span data-ttu-id="63db9-122">Najważniejszą zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest integracji z [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63db9-122">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="63db9-123">Ta integracja umożliwia pisanie zapytań dotyczących dokumentu XML w pamięci, aby pobierać kolekcje elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="63db9-123">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="63db9-124">Możliwości zapytania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można porównywać pod względem funkcji (ale nie w składni) XPath i XQuery.</span><span class="sxs-lookup"><span data-stu-id="63db9-124">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="63db9-125">Integracja [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] w języku C# zapewnia lepsze Pisownia, kompilacji sprawdzenie i ulepszona obsługa debugera.</span><span class="sxs-lookup"><span data-stu-id="63db9-125">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="63db9-126">Inną zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest możliwość używania wyników zapytania jako parametry <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> konstruktorach obiektów umożliwia wydajne podejście do tworzenia drzew XML.</span><span class="sxs-lookup"><span data-stu-id="63db9-126">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="63db9-127">Takie podejście, nazywane *konstrukcja funkcjonalna*, umożliwia deweloperom łatwe Przekształcanie drzew XML z jednego kształtu do innego.</span><span class="sxs-lookup"><span data-stu-id="63db9-127">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="63db9-128">Na przykład, Niewykluczone, że typowy XML, zamówienie zakupu, zgodnie z opisem w [przykładowy plik XML: Typowe zamówienie zakupu (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="63db9-128">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="63db9-129">Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można uruchomić następujące zapytanie, aby uzyskać część wartości atrybutu numeru dla każdego elementu w porządku zakupu:</span><span class="sxs-lookup"><span data-stu-id="63db9-129">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

<span data-ttu-id="63db9-130">Można to inaczej w formularzu składni metody:</span><span class="sxs-lookup"><span data-stu-id="63db9-130">This can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="63db9-131">Inny przykład, możesz zechcieć listę, posortowane według numer części, elementów o wartości większej niż 100 USD.</span><span class="sxs-lookup"><span data-stu-id="63db9-131">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="63db9-132">Aby uzyskać te informacje, można uruchomić następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="63db9-132">To obtain this information, you could run the following query:</span></span>

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

<span data-ttu-id="63db9-133">Ponownie to może zostać przepisany forma składni metody:</span><span class="sxs-lookup"><span data-stu-id="63db9-133">Again, this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="63db9-134">Oprócz wspomnianych [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] możliwości [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] udostępnia Ulepszony interfejs programowania XML.</span><span class="sxs-lookup"><span data-stu-id="63db9-134">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="63db9-135">Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], możesz:</span><span class="sxs-lookup"><span data-stu-id="63db9-135">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>

- <span data-ttu-id="63db9-136">Ładowanie kodu XML z [pliki](how-to-load-xml-from-a-file.md) lub [strumieni](how-to-stream-xml-fragments-from-an-xmlreader.md).</span><span class="sxs-lookup"><span data-stu-id="63db9-136">Load XML from [files](how-to-load-xml-from-a-file.md) or [streams](how-to-stream-xml-fragments-from-an-xmlreader.md).</span></span>

- <span data-ttu-id="63db9-137">Serializacji XML do plików i strumieni.</span><span class="sxs-lookup"><span data-stu-id="63db9-137">Serialize XML to files or streams.</span></span>

- <span data-ttu-id="63db9-138">Tworzenie XML od podstaw przy użyciu konstrukcja funkcjonalna.</span><span class="sxs-lookup"><span data-stu-id="63db9-138">Create XML from scratch by using functional construction.</span></span>

- <span data-ttu-id="63db9-139">Zapytanie XML przy użyciu notacji XPath osi.</span><span class="sxs-lookup"><span data-stu-id="63db9-139">Query XML using XPath-like axes.</span></span>

- <span data-ttu-id="63db9-140">Manipulowanie drzewa XML w pamięci przy użyciu metod, takich jak <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, i <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="63db9-140">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>

- <span data-ttu-id="63db9-141">Sprawdź poprawność drzew XML przy użyciu XSD.</span><span class="sxs-lookup"><span data-stu-id="63db9-141">Validate XML trees using XSD.</span></span>

- <span data-ttu-id="63db9-142">Kombinacja tych funkcji umożliwia przekształcanie drzew XML z jednego kształtu do innego.</span><span class="sxs-lookup"><span data-stu-id="63db9-142">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="creating-xml-trees"></a><span data-ttu-id="63db9-143">Tworzenie drzew XML</span><span class="sxs-lookup"><span data-stu-id="63db9-143">Creating XML Trees</span></span>

<span data-ttu-id="63db9-144">Jedną z najbardziej znaczących korzyści wynikające z programowania, korzystając z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest łatwe tworzenie drzew XML.</span><span class="sxs-lookup"><span data-stu-id="63db9-144">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="63db9-145">Na przykład do tworzenia małych drzewa XML, należy można napisać kod w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="63db9-145">For example, to create a small XML tree, you can write code as follows:</span></span>

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

<span data-ttu-id="63db9-146">Aby uzyskać więcej informacji, zobacz [tworzenie drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="63db9-146">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="63db9-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63db9-147">See also</span></span>

- [<span data-ttu-id="63db9-148">Odwołanie (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="63db9-148">Reference (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/reference-linq-to-xml.md)
- [<span data-ttu-id="63db9-149">LINQ to XML a MODELU DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="63db9-149">LINQ to XML vs. DOM (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [<span data-ttu-id="63db9-150">LINQ to XML a inne technologie XML</span><span class="sxs-lookup"><span data-stu-id="63db9-150">LINQ to XML vs. Other XML Technologies</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
