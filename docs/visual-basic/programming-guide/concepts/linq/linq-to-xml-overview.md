---
title: LINQ to XML — przegląd
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: ef3fca844dc98440eb4816110a5a78482cfa4f4e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346798"
---
# <a name="linq-to-xml-overview-visual-basic"></a><span data-ttu-id="e818f-102">Przegląd LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e818f-102">LINQ to XML Overview (Visual Basic)</span></span>
<span data-ttu-id="e818f-103">Język XML został szeroko przyjęty jako sposób formatowania danych w wielu kontekstach.</span><span class="sxs-lookup"><span data-stu-id="e818f-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="e818f-104">Na przykład można znaleźć XML w sieci Web, w plikach konfiguracyjnych, w Microsoft Office pliki programu Word i w bazach danych.</span><span class="sxs-lookup"><span data-stu-id="e818f-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="e818f-105">to aktualne, przeprojektowane podejście do programowania w języku XML.</span><span class="sxs-lookup"><span data-stu-id="e818f-105">is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="e818f-106">Zapewnia możliwości modyfikacji dokumentów w pamięci Document Object Model (DOM) i obsługuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeń zapytań.</span><span class="sxs-lookup"><span data-stu-id="e818f-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="e818f-107">Mimo że te wyrażenia zapytania różnią się od składni XPath, zapewniają podobną funkcjonalność.</span><span class="sxs-lookup"><span data-stu-id="e818f-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="e818f-108">LINQ to XML deweloperzy</span><span class="sxs-lookup"><span data-stu-id="e818f-108">LINQ to XML Developers</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="e818f-109">są przeznaczone dla wielu deweloperów.</span><span class="sxs-lookup"><span data-stu-id="e818f-109">targets a variety of developers.</span></span> <span data-ttu-id="e818f-110">W przypadku przeciętnego dewelopera, który po prostu chce uzyskać coś gotowego, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ułatwia tworzenie kodu XML, zapewniając środowisko zapytania podobne do SQL.</span><span class="sxs-lookup"><span data-stu-id="e818f-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="e818f-111">Mając zaledwie kilka analiz, programiści mogą uczyć się pisać zwięzłe i zaawansowane zapytania w wybranym języku programowania.</span><span class="sxs-lookup"><span data-stu-id="e818f-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="e818f-112">Profesjonalni deweloperzy mogą korzystać z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], aby znacznie zwiększyć swoją produktywność.</span><span class="sxs-lookup"><span data-stu-id="e818f-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="e818f-113">Dzięki [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]mogą pisać mniej kod, który jest bardziej wyraźny, bardziej zwarty i bardziej wydajny.</span><span class="sxs-lookup"><span data-stu-id="e818f-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="e818f-114">Mogą używać wyrażeń zapytania z wielu domen danych w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="e818f-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="e818f-115">Co to jest LINQ to XML?</span><span class="sxs-lookup"><span data-stu-id="e818f-115">What Is LINQ to XML?</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="e818f-116">to interfejs programowania XML z obsługą technologii LINQ, który umożliwia współpracę z językiem XML w .NET Framework językach programowania.</span><span class="sxs-lookup"><span data-stu-id="e818f-116">is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the .NET Framework programming languages.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="e818f-117">przypomina Document Object Model (DOM) w tym, że dokument XML jest umieszczany w pamięci.</span><span class="sxs-lookup"><span data-stu-id="e818f-117">is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="e818f-118">Możesz wysyłać zapytania i modyfikować dokument, a po zmodyfikowaniu go można zapisać do pliku lub serializować go i wysłać za pośrednictwem Internetu.</span><span class="sxs-lookup"><span data-stu-id="e818f-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="e818f-119">Jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] różni się od modelu DOM: udostępnia nowy model obiektów, który jest jaśniejszy i ułatwia pracę z programem, a także korzysta z funkcji języka w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e818f-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in Visual Basic.</span></span>  
  
 <span data-ttu-id="e818f-120">Najważniejszym zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest integracja z [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e818f-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="e818f-121">Ta Integracja umożliwia pisanie zapytań dotyczących dokumentu XML w pamięci w celu pobrania kolekcji elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="e818f-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="e818f-122">Możliwość wykonywania zapytań w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest porównywalna w funkcji (choć nie w składni) do XPath i XQuery.</span><span class="sxs-lookup"><span data-stu-id="e818f-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="e818f-123">Integracja [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] w Visual Basic zapewnia silniejsze wpisywanie, sprawdzanie czasu kompilowania i udoskonaloną obsługę debugera.</span><span class="sxs-lookup"><span data-stu-id="e818f-123">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="e818f-124">Kolejną zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest możliwość używania wyników zapytania jako parametrów do <xref:System.Xml.Linq.XElement> i konstruktorów obiektów <xref:System.Xml.Linq.XAttribute> umożliwia zaawansowane podejście do tworzenia drzew XML.</span><span class="sxs-lookup"><span data-stu-id="e818f-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="e818f-125">Takie podejście, nazywane *konstrukcją funkcjonalną*, umożliwia deweloperom łatwe przekształcanie drzew XML z jednego kształtu do drugiego.</span><span class="sxs-lookup"><span data-stu-id="e818f-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="e818f-126">Na przykład może istnieć typowa kolejność zakupu XML, zgodnie z opisem w [przykładowym pliku XML: typowe zamówienie zakupu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="e818f-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span> <span data-ttu-id="e818f-127">Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]można uruchomić następujące zapytanie w celu uzyskania wartości atrybutu numer części dla każdego elementu elementu w zamówieniu zakupu:</span><span class="sxs-lookup"><span data-stu-id="e818f-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 <span data-ttu-id="e818f-128">Innym przykładem może być lista, posortowana według numeru części, dla elementów o wartości większej niż $100.</span><span class="sxs-lookup"><span data-stu-id="e818f-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="e818f-129">Aby uzyskać te informacje, można uruchomić następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="e818f-129">To obtain this information, you could run the following query:</span></span>  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 <span data-ttu-id="e818f-130">Oprócz tych [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] możliwości [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oferuje udoskonalony interfejs programowania XML.</span><span class="sxs-lookup"><span data-stu-id="e818f-130">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="e818f-131">Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]można:</span><span class="sxs-lookup"><span data-stu-id="e818f-131">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>  
  
- <span data-ttu-id="e818f-132">Załaduj plik XML z plików lub strumieni.</span><span class="sxs-lookup"><span data-stu-id="e818f-132">Load XML from files or streams.</span></span>  
  
- <span data-ttu-id="e818f-133">Serializacja XML do plików lub strumieni.</span><span class="sxs-lookup"><span data-stu-id="e818f-133">Serialize XML to files or streams.</span></span>  
  
- <span data-ttu-id="e818f-134">Utwórz plik XML od podstaw przy użyciu konstrukcji funkcjonalnej.</span><span class="sxs-lookup"><span data-stu-id="e818f-134">Create XML from scratch by using functional construction.</span></span>  
  
- <span data-ttu-id="e818f-135">Kwerenda XML przy użyciu osi podobnej do XPath.</span><span class="sxs-lookup"><span data-stu-id="e818f-135">Query XML using XPath-like axes.</span></span>  
  
- <span data-ttu-id="e818f-136">Manipulowanie drzewem XML w pamięci za pomocą metod, takich jak <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>i <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="e818f-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
- <span data-ttu-id="e818f-137">Sprawdzanie poprawności drzew XML przy użyciu XSD.</span><span class="sxs-lookup"><span data-stu-id="e818f-137">Validate XML trees using XSD.</span></span>  
  
- <span data-ttu-id="e818f-138">Aby przekształcić drzewa XML z jednego kształtu na inny, należy użyć kombinacji tych funkcji.</span><span class="sxs-lookup"><span data-stu-id="e818f-138">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="e818f-139">Tworzenie drzew XML</span><span class="sxs-lookup"><span data-stu-id="e818f-139">Creating XML Trees</span></span>  
 <span data-ttu-id="e818f-140">IOne z najbardziej znaczącymi zaletami programowania przy użyciu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] polega na tym, że tworzenie drzew XML jest łatwe.</span><span class="sxs-lookup"><span data-stu-id="e818f-140">IOne of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="e818f-141">Na przykład, aby utworzyć małe drzewo XML, można napisać kod w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="e818f-141">For example, to create a small XML tree, you can write  code as follows:</span></span>  
  
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
  
 <span data-ttu-id="e818f-142">Kompilator Visual Basic tłumaczy literały XML na wywołania metody [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e818f-142">The Visual Basic compiler translates XML literals into [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] method calls.</span></span>  
  
 <span data-ttu-id="e818f-143">Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="e818f-143">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e818f-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e818f-144">See also</span></span>

- <xref:System.Xml.Linq>
- [<span data-ttu-id="e818f-145">Wprowadzenie (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="e818f-145">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
- [<span data-ttu-id="e818f-146">Omówienie LINQ to XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e818f-146">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)
- [<span data-ttu-id="e818f-147">XML</span><span class="sxs-lookup"><span data-stu-id="e818f-147">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
