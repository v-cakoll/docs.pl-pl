---
title: LINQ to XML — Przegląd (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
ms.openlocfilehash: 962fddcfec04259425c1094f07adf0e3966dfab0
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361837"
---
# <a name="linq-to-xml-overview-visual-basic"></a><span data-ttu-id="630eb-102">LINQ to XML — Przegląd (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="630eb-102">LINQ to XML Overview (Visual Basic)</span></span>
<span data-ttu-id="630eb-103">XML ma powszechnie zaakceptowany jako sposób na formatowanie danych w wielu kontekstach.</span><span class="sxs-lookup"><span data-stu-id="630eb-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="630eb-104">Na przykład możesz znaleźć XML w sieci Web, w plikach konfiguracji, pliki programu Microsoft Office Word i baz danych.</span><span class="sxs-lookup"><span data-stu-id="630eb-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="630eb-105"> to aktualne, przeprojektowana podejście do programowania w języku XML.</span><span class="sxs-lookup"><span data-stu-id="630eb-105"> is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="630eb-106">Zawiera on dokumentów w pamięci możliwości modyfikacji Document Object Model (DOM) i obsługuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażeniach zapytań.</span><span class="sxs-lookup"><span data-stu-id="630eb-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="630eb-107">Mimo że te wyrażenia kwerendy są składniowo różni się od XPath, zapewniają podobne funkcje.</span><span class="sxs-lookup"><span data-stu-id="630eb-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="630eb-108">LINQ to XML deweloperów</span><span class="sxs-lookup"><span data-stu-id="630eb-108">LINQ to XML Developers</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="630eb-109"> jest przeznaczony dla różnych deweloperów.</span><span class="sxs-lookup"><span data-stu-id="630eb-109"> targets a variety of developers.</span></span> <span data-ttu-id="630eb-110">Dla średniej deweloperem właśnie coś zrobić [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ułatwia XML, zapewniając środowisko zapytania, która jest podobna do bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="630eb-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="630eb-111">Po prostu bit analiza programistów można Dowiedz się, jak pisać zapytania zwięzły i Zaawansowane w ich dowolny język programowania.</span><span class="sxs-lookup"><span data-stu-id="630eb-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="630eb-112">Profesjonalni deweloperzy mogą używać [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] znacznie zwiększyć ich wydajność.</span><span class="sxs-lookup"><span data-stu-id="630eb-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="630eb-113">Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], mogą zapisywać mniejszej ilości kodu, który jest bardziej ekspresyjnego, bardziej zwarty i bardziej wydajne.</span><span class="sxs-lookup"><span data-stu-id="630eb-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="630eb-114">Ich użyć wyrażeń zapytania z wieloma domenami danych, w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="630eb-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="630eb-115">Co to jest LINQ to XML?</span><span class="sxs-lookup"><span data-stu-id="630eb-115">What Is LINQ to XML?</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="630eb-116"> to włączone LINQ, wewnątrzpamięciowe XML programowania interfejs, który umożliwia pracę z danymi XML, z poziomu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] języków programowania.</span><span class="sxs-lookup"><span data-stu-id="630eb-116"> is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programming languages.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="630eb-117"> jest jak modelu DOM (Document Object) zapewnia dokumentu XML do pamięci.</span><span class="sxs-lookup"><span data-stu-id="630eb-117"> is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="630eb-118">Można wykonywać zapytania i modyfikować dokument, a po jego modyfikacji można zapisać w pliku lub serializować go i wysyłać je przez Internet.</span><span class="sxs-lookup"><span data-stu-id="630eb-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="630eb-119">Jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] różni się od modelu DOM: zapewnia nowy model obiektu, który jest mniejsza waga i łatwiej pracować z, i który korzysta z funkcji języka w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="630eb-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in Visual Basic.</span></span>  
  
 <span data-ttu-id="630eb-120">Najważniejszą zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest integracji z [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="630eb-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="630eb-121">Ta integracja umożliwia pisanie zapytań dotyczących dokumentu XML w pamięci, aby pobierać kolekcje elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="630eb-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="630eb-122">Możliwości zapytania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można porównywać pod względem funkcji (ale nie w składni) XPath i XQuery.</span><span class="sxs-lookup"><span data-stu-id="630eb-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="630eb-123">Integracja [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] w języku Visual Basic oferuje lepsze Pisownia, kompilacji sprawdzenie i ulepszona obsługa debugera.</span><span class="sxs-lookup"><span data-stu-id="630eb-123">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="630eb-124">Inną zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest możliwość używania wyników zapytania jako parametry <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> konstruktorach obiektów umożliwia wydajne podejście do tworzenia drzew XML.</span><span class="sxs-lookup"><span data-stu-id="630eb-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="630eb-125">Takie podejście, nazywane *konstrukcja funkcjonalna*, umożliwia deweloperom łatwe Przekształcanie drzew XML z jednego kształtu do innego.</span><span class="sxs-lookup"><span data-stu-id="630eb-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="630eb-126">Na przykład, Niewykluczone, że typowy XML, zamówienie zakupu, zgodnie z opisem w [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="630eb-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).</span></span> <span data-ttu-id="630eb-127">Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można uruchomić następujące zapytanie, aby uzyskać część wartości atrybutu numeru dla każdego elementu w porządku zakupu:</span><span class="sxs-lookup"><span data-stu-id="630eb-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 <span data-ttu-id="630eb-128">Inny przykład, możesz zechcieć listę, posortowane według numer części, elementów o wartości większej niż 100 USD.</span><span class="sxs-lookup"><span data-stu-id="630eb-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="630eb-129">Aby uzyskać te informacje, można uruchomić następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="630eb-129">To obtain this information, you could run the following query:</span></span>  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 <span data-ttu-id="630eb-130">Oprócz wspomnianych [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] możliwości [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] udostępnia Ulepszony interfejs programowania XML.</span><span class="sxs-lookup"><span data-stu-id="630eb-130">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="630eb-131">Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], możesz:</span><span class="sxs-lookup"><span data-stu-id="630eb-131">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>  
  
-   <span data-ttu-id="630eb-132">Ładowanie kodu XML z plików i strumieni.</span><span class="sxs-lookup"><span data-stu-id="630eb-132">Load XML from files or streams.</span></span>  
  
-   <span data-ttu-id="630eb-133">Serializacji XML do plików i strumieni.</span><span class="sxs-lookup"><span data-stu-id="630eb-133">Serialize XML to files or streams.</span></span>  
  
-   <span data-ttu-id="630eb-134">Tworzenie XML od podstaw przy użyciu konstrukcja funkcjonalna.</span><span class="sxs-lookup"><span data-stu-id="630eb-134">Create XML from scratch by using functional construction.</span></span>  
  
-   <span data-ttu-id="630eb-135">Zapytanie XML przy użyciu notacji XPath osi.</span><span class="sxs-lookup"><span data-stu-id="630eb-135">Query XML using XPath-like axes.</span></span>  
  
-   <span data-ttu-id="630eb-136">Manipulowanie drzewa XML w pamięci przy użyciu metod, takich jak <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, i <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="630eb-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
-   <span data-ttu-id="630eb-137">Sprawdź poprawność drzew XML przy użyciu XSD.</span><span class="sxs-lookup"><span data-stu-id="630eb-137">Validate XML trees using XSD.</span></span>  
  
-   <span data-ttu-id="630eb-138">Kombinacja tych funkcji umożliwia przekształcanie drzew XML z jednego kształtu do innego.</span><span class="sxs-lookup"><span data-stu-id="630eb-138">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="630eb-139">Tworzenie drzew XML</span><span class="sxs-lookup"><span data-stu-id="630eb-139">Creating XML Trees</span></span>  
 <span data-ttu-id="630eb-140">IOne najbardziej znaczące korzyści wynikające z programowania, korzystając z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest łatwe tworzenie drzew XML.</span><span class="sxs-lookup"><span data-stu-id="630eb-140">IOne of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="630eb-141">Na przykład do tworzenia małych drzewa XML, należy można napisać kod w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="630eb-141">For example, to create a small XML tree, you can write  code as follows:</span></span>  
  
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
  
 <span data-ttu-id="630eb-142">Kompilator języka Visual Basic tłumaczy literałów XML do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="630eb-142">The Visual Basic compiler translates XML literals into [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] method calls.</span></span>  
  
 <span data-ttu-id="630eb-143">Aby uzyskać więcej informacji, zobacz [tworzenie drzew XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="630eb-143">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="630eb-144">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="630eb-144">See also</span></span>

- <xref:System.Xml.Linq>  
- [<span data-ttu-id="630eb-145">Wprowadzenie (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="630eb-145">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)  
- [<span data-ttu-id="630eb-146">Przegląd interfejsu LINQ to XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="630eb-146">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
- [<span data-ttu-id="630eb-147">XML</span><span class="sxs-lookup"><span data-stu-id="630eb-147">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
