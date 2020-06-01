---
title: Przegląd LINQ to XML (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: dd41d8607ef3f2e6e6be9a1f3964ef0ae937e2ac
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241841"
---
# <a name="linq-to-xml-overview-c"></a><span data-ttu-id="d62a1-102">Przegląd LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d62a1-102">LINQ to XML Overview (C#)</span></span>

<span data-ttu-id="d62a1-103">LINQ to XML udostępnia interfejs programowania XML w pamięci, który wykorzystuje architekturę programu .NET Language-Integrated Query (LINQ).</span><span class="sxs-lookup"><span data-stu-id="d62a1-103">LINQ to XML provides an in-memory XML programming interface that leverages the .NET Language-Integrated Query (LINQ) Framework.</span></span> <span data-ttu-id="d62a1-104">LINQ to XML używa możliwości platformy .NET i jest porównywalna z zaktualizowanym, przeprojektowanym Document Object Model (DOM) interfejsem programowania XML.</span><span class="sxs-lookup"><span data-stu-id="d62a1-104">LINQ to XML uses .NET capabilities and is comparable to an updated, redesigned Document Object Model (DOM) XML programming interface.</span></span>

<span data-ttu-id="d62a1-105">Język XML został szeroko przyjęty jako sposób formatowania danych w wielu kontekstach.</span><span class="sxs-lookup"><span data-stu-id="d62a1-105">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="d62a1-106">Na przykład można znaleźć XML w sieci Web, w plikach konfiguracyjnych, w Microsoft Office pliki programu Word i w bazach danych.</span><span class="sxs-lookup"><span data-stu-id="d62a1-106">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="d62a1-107">to aktualne, przeprojektowane podejście do programowania w języku XML.</span><span class="sxs-lookup"><span data-stu-id="d62a1-107">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="d62a1-108">Zapewnia możliwości modyfikacji dokumentów w pamięci Document Object Model (DOM) i obsługuje wyrażenia zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="d62a1-108">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports LINQ query expressions.</span></span> <span data-ttu-id="d62a1-109">Mimo że te wyrażenia zapytania różnią się od składni XPath, zapewniają podobną funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="d62a1-109">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>

## <a name="linq-to-xml-developers"></a><span data-ttu-id="d62a1-110">LINQ to XML deweloperzy</span><span class="sxs-lookup"><span data-stu-id="d62a1-110">LINQ to XML Developers</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="d62a1-111">jest przeznaczony dla różnych deweloperów.</span><span class="sxs-lookup"><span data-stu-id="d62a1-111">targets a variety of developers.</span></span> <span data-ttu-id="d62a1-112">W przypadku przeciętnego dewelopera, który po prostu chce uzyskać coś gotowego, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ułatwia tworzenie kodu XML, zapewniając środowisko zapytania podobne do SQL.</span><span class="sxs-lookup"><span data-stu-id="d62a1-112">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="d62a1-113">Mając zaledwie kilka analiz, programiści mogą uczyć się pisać zwięzłe i zaawansowane zapytania w wybranym języku programowania.</span><span class="sxs-lookup"><span data-stu-id="d62a1-113">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>

<span data-ttu-id="d62a1-114">Profesjonalne deweloperzy mogą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] znacznie zwiększyć swoją produktywność.</span><span class="sxs-lookup"><span data-stu-id="d62a1-114">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="d62a1-115">Dzięki [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] programom mogą pisać mniej kod, który jest bardziej wyraźny, bardziej zwarty i bardziej wydajny.</span><span class="sxs-lookup"><span data-stu-id="d62a1-115">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="d62a1-116">Mogą używać wyrażeń zapytania z wielu domen danych w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="d62a1-116">They can use query expressions from multiple data domains at the same time.</span></span>

## <a name="what-is-linq-to-xml"></a><span data-ttu-id="d62a1-117">Co to jest LINQ to XML?</span><span class="sxs-lookup"><span data-stu-id="d62a1-117">What Is LINQ to XML?</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="d62a1-118">to interfejs programowania XML obsługujący LINQ, który umożliwia korzystanie z kodu XML z poziomu języków programowania .NET.</span><span class="sxs-lookup"><span data-stu-id="d62a1-118">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET programming languages.</span></span>

[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="d62a1-119">przypomina Document Object Model (DOM) w tym, że dokument XML jest umieszczany w pamięci.</span><span class="sxs-lookup"><span data-stu-id="d62a1-119">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="d62a1-120">Możesz wysyłać zapytania i modyfikować dokument, a po zmodyfikowaniu go można zapisać do pliku lub serializować go i wysłać za pośrednictwem Internetu.</span><span class="sxs-lookup"><span data-stu-id="d62a1-120">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="d62a1-121">Jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] różni się od modelu DOM: udostępnia nowy model obiektów, który jest jaśniejszy i ułatwia pracę z programem, a także korzysta z funkcji języka w języku C#.</span><span class="sxs-lookup"><span data-stu-id="d62a1-121">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in C#.</span></span>

<span data-ttu-id="d62a1-122">Najważniejsze korzyści wynikające z tej [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] integracji to integracja ze standardem Language-Integrated Query (LINQ).</span><span class="sxs-lookup"><span data-stu-id="d62a1-122">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with Language-Integrated Query (LINQ).</span></span> <span data-ttu-id="d62a1-123">Ta Integracja umożliwia pisanie zapytań dotyczących dokumentu XML w pamięci w celu pobrania kolekcji elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="d62a1-123">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="d62a1-124">Możliwość zapytania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest porównywalna w funkcji (choć nie w składni) do XPath i XQuery.</span><span class="sxs-lookup"><span data-stu-id="d62a1-124">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="d62a1-125">Integracja LINQ w języku C# zapewnia silniejsze wpisywanie, sprawdzanie czasu kompilowania i udoskonaloną obsługę debugera.</span><span class="sxs-lookup"><span data-stu-id="d62a1-125">The integration of LINQ in C# provides stronger typing, compile-time checking, and improved debugger support.</span></span>

<span data-ttu-id="d62a1-126">Inną zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest możliwość używania wyników zapytania jako parametrów do <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> konstruktorów obiektów i umożliwia zaawansowane podejście do tworzenia drzew XML.</span><span class="sxs-lookup"><span data-stu-id="d62a1-126">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="d62a1-127">Takie podejście, nazywane *konstrukcją funkcjonalną*, umożliwia deweloperom łatwe przekształcanie drzew XML z jednego kształtu do drugiego.</span><span class="sxs-lookup"><span data-stu-id="d62a1-127">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>

<span data-ttu-id="d62a1-128">Na przykład może istnieć typowa kolejność zakupu XML, zgodnie z opisem w [przykładowym pliku XML: typowe zamówienie zakupu (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="d62a1-128">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span> <span data-ttu-id="d62a1-129">Korzystając z programu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , można uruchomić następujące zapytanie w celu uzyskania wartości atrybutu numer części dla każdego elementu elementu w zamówieniu zakupu:</span><span class="sxs-lookup"><span data-stu-id="d62a1-129">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load(purchaseOrderFilepath);

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

<span data-ttu-id="d62a1-130">Można to zrobić ponownie w postaci składni metody:</span><span class="sxs-lookup"><span data-stu-id="d62a1-130">This can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

<span data-ttu-id="d62a1-131">Innym przykładem może być lista, posortowana według numeru części, dla elementów o wartości większej niż $100.</span><span class="sxs-lookup"><span data-stu-id="d62a1-131">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="d62a1-132">Aby uzyskać te informacje, można uruchomić następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="d62a1-132">To obtain this information, you could run the following query:</span></span>

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

<span data-ttu-id="d62a1-133">Można to zrobić ponownie w postaci składni metody:</span><span class="sxs-lookup"><span data-stu-id="d62a1-133">Again, this can be rewritten in method syntax form:</span></span>

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

<span data-ttu-id="d62a1-134">Oprócz tych funkcji LINQ program [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] udostępnia udoskonalony interfejs programowania XML.</span><span class="sxs-lookup"><span data-stu-id="d62a1-134">In addition to these LINQ capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="d62a1-135">Korzystając [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] z programu, można:</span><span class="sxs-lookup"><span data-stu-id="d62a1-135">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>

- <span data-ttu-id="d62a1-136">Załaduj plik XML z [plików](how-to-load-xml-from-a-file.md) lub [strumieni](how-to-stream-xml-fragments-from-an-xmlreader.md).</span><span class="sxs-lookup"><span data-stu-id="d62a1-136">Load XML from [files](how-to-load-xml-from-a-file.md) or [streams](how-to-stream-xml-fragments-from-an-xmlreader.md).</span></span>

- <span data-ttu-id="d62a1-137">Serializacja XML do plików lub strumieni.</span><span class="sxs-lookup"><span data-stu-id="d62a1-137">Serialize XML to files or streams.</span></span>

- <span data-ttu-id="d62a1-138">Utwórz plik XML od podstaw przy użyciu konstrukcji funkcjonalnej.</span><span class="sxs-lookup"><span data-stu-id="d62a1-138">Create XML from scratch by using functional construction.</span></span>

- <span data-ttu-id="d62a1-139">Kwerenda XML przy użyciu osi podobnej do XPath.</span><span class="sxs-lookup"><span data-stu-id="d62a1-139">Query XML using XPath-like axes.</span></span>

- <span data-ttu-id="d62a1-140">Manipulowanie drzewem XML w pamięci za pomocą metod takich jak <xref:System.Xml.Linq.XContainer.Add%2A> , <xref:System.Xml.Linq.XNode.Remove%2A> , <xref:System.Xml.Linq.XNode.ReplaceWith%2A> i <xref:System.Xml.Linq.XElement.SetValue%2A> .</span><span class="sxs-lookup"><span data-stu-id="d62a1-140">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>

- <span data-ttu-id="d62a1-141">Sprawdzanie poprawności drzew XML przy użyciu XSD.</span><span class="sxs-lookup"><span data-stu-id="d62a1-141">Validate XML trees using XSD.</span></span>

- <span data-ttu-id="d62a1-142">Aby przekształcić drzewa XML z jednego kształtu na inny, należy użyć kombinacji tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="d62a1-142">Use a combination of these features to transform XML trees from one shape into another.</span></span>

## <a name="creating-xml-trees"></a><span data-ttu-id="d62a1-143">Tworzenie drzew XML</span><span class="sxs-lookup"><span data-stu-id="d62a1-143">Creating XML Trees</span></span>

<span data-ttu-id="d62a1-144">Jedną z najbardziej znaczących zalet programowania w programie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest łatwość tworzenia drzew XML.</span><span class="sxs-lookup"><span data-stu-id="d62a1-144">One of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="d62a1-145">Na przykład, aby utworzyć małe drzewo XML, można napisać kod w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d62a1-145">For example, to create a small XML tree, you can write code as follows:</span></span>

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

<span data-ttu-id="d62a1-146">Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML (C#)](./creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="d62a1-146">For more information, see [Creating XML Trees (C#)](./creating-xml-trees-linq-to-xml-2.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d62a1-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d62a1-147">See also</span></span>

- [<span data-ttu-id="d62a1-148">Odwołanie (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="d62a1-148">Reference (LINQ to XML)</span></span>](./reference-linq-to-xml.md)
- [<span data-ttu-id="d62a1-149">LINQ to XML a DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="d62a1-149">LINQ to XML vs. DOM (C#)</span></span>](./linq-to-xml-vs-dom.md)
- [<span data-ttu-id="d62a1-150">LINQ to XML a inne technologie XML</span><span class="sxs-lookup"><span data-stu-id="d62a1-150">LINQ to XML vs. Other XML Technologies</span></span>](./linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
