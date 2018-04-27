---
title: LINQ do XML-Przegląd (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 502661e0-bc5d-438d-94c2-7efb63bb6fbd
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f4ccc81f1f7b875c7388dc09cc45521c6257c00d
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="linq-to-xml-overview-visual-basic"></a><span data-ttu-id="2e22d-102">LINQ do XML-Przegląd (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e22d-102">LINQ to XML Overview (Visual Basic)</span></span>
<span data-ttu-id="2e22d-103">Powszechnie przyjęto XML jako sposób do formatowania danych w wielu sytuacjach.</span><span class="sxs-lookup"><span data-stu-id="2e22d-103">XML has been widely adopted as a way to format data in many contexts.</span></span> <span data-ttu-id="2e22d-104">Na przykład XML można znaleźć w sieci Web, w plikach konfiguracji, pliki programu Microsoft Office Word i baz danych.</span><span class="sxs-lookup"><span data-stu-id="2e22d-104">For example, you can find XML on the Web, in configuration files, in Microsoft Office Word files, and in databases.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2e22d-105"> jest aktualne, zmienioną podejście do programowania w języku XML.</span><span class="sxs-lookup"><span data-stu-id="2e22d-105"> is an up-to-date, redesigned approach to programming with XML.</span></span> <span data-ttu-id="2e22d-106">Udostępnia dokument w pamięci możliwości modyfikacji z modelu DOM (Document Object) i obsługuje [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażenia zapytań.</span><span class="sxs-lookup"><span data-stu-id="2e22d-106">It provides the in-memory document modification capabilities of the Document Object Model (DOM), and supports [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="2e22d-107">Chociaż tych wyrażeń zapytania składniowo różnią się od wyrażenia XPath, zapewniają podobne funkcje.</span><span class="sxs-lookup"><span data-stu-id="2e22d-107">Although these query expressions are syntactically different from XPath, they provide similar functionality.</span></span>  
  
## <a name="linq-to-xml-developers"></a><span data-ttu-id="2e22d-108">LINQ do XML deweloperów</span><span class="sxs-lookup"><span data-stu-id="2e22d-108">LINQ to XML Developers</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2e22d-109"> Celem odmiany deweloperów.</span><span class="sxs-lookup"><span data-stu-id="2e22d-109"> targets a variety of developers.</span></span> <span data-ttu-id="2e22d-110">Dla średniej developer, który właśnie chce coś zrobić [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ułatwia XML, udostępniając środowisko zapytania, która jest podobna do bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="2e22d-110">For an average developer who just wants to get something done, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] makes XML easier by providing a query experience that is similar to SQL.</span></span> <span data-ttu-id="2e22d-111">Tylko bit badań programistów dowiedzieć się do pisania zwięzły i zaawansowanych zapytań w języku programowania wyboru.</span><span class="sxs-lookup"><span data-stu-id="2e22d-111">With just a bit of study, programmers can learn to write succinct and powerful queries in their programming language of choice.</span></span>  
  
 <span data-ttu-id="2e22d-112">Professional deweloperzy mogą używać [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] znacznie zwiększyć ich wydajność.</span><span class="sxs-lookup"><span data-stu-id="2e22d-112">Professional developers can use [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to greatly increase their productivity.</span></span> <span data-ttu-id="2e22d-113">Z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], mogą zapisywać mniej kodu, który jest bardziej obszerne mniejszych i bardziej zaawansowanych.</span><span class="sxs-lookup"><span data-stu-id="2e22d-113">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], they can write less code that is more expressive, more compact, and more powerful.</span></span> <span data-ttu-id="2e22d-114">Wyrażenia zapytań z wielu domen danych użyciem w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="2e22d-114">They can use query expressions from multiple data domains at the same time.</span></span>  
  
## <a name="what-is-linq-to-xml"></a><span data-ttu-id="2e22d-115">Co to jest LINQ do XML?</span><span class="sxs-lookup"><span data-stu-id="2e22d-115">What Is LINQ to XML?</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2e22d-116"> to włączone LINQ, w pamięci XML programowania interfejs, który umożliwia pracę z językiem XML z poziomu [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] języków programowania.</span><span class="sxs-lookup"><span data-stu-id="2e22d-116"> is a LINQ-enabled, in-memory XML programming interface that enables you to work with XML from within the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] programming languages.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="2e22d-117"> ma takie jak modelu DOM (Document Object) stwarza dokumentu XML do pamięci.</span><span class="sxs-lookup"><span data-stu-id="2e22d-117"> is like the Document Object Model (DOM) in that it brings the XML document into memory.</span></span> <span data-ttu-id="2e22d-118">Możesz zbadać i modyfikowanie dokumentu, a po jego modyfikacji można zapisać w pliku lub go serializować i wysłać go przez Internet.</span><span class="sxs-lookup"><span data-stu-id="2e22d-118">You can query and modify the document, and after you modify it you can save it to a file or serialize it and send it over the Internet.</span></span> <span data-ttu-id="2e22d-119">Jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] różni się od DOM: zapewnia nowy model, która jest mniejsza waga i łatwiejsze do pracy z, i który korzysta z funkcji języka w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2e22d-119">However, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] differs from DOM: It provides a new object model that is lighter weight and easier to work with, and that takes advantage of language features in Visual Basic.</span></span>  
  
 <span data-ttu-id="2e22d-120">Najważniejszą korzyścią z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest integracji z [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e22d-120">The most important advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is its integration with [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)].</span></span> <span data-ttu-id="2e22d-121">Integracja ta umożliwia pisanie zapytań w dokumencie XML w pamięci można pobrać kolekcji elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="2e22d-121">This integration enables you to write queries on the in-memory XML document to retrieve collections of elements and attributes.</span></span> <span data-ttu-id="2e22d-122">Możliwości zapytania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można porównywać pod względem funkcji (ale nie w składni) XPath i XQuery.</span><span class="sxs-lookup"><span data-stu-id="2e22d-122">The query capability of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is comparable in functionality (although not in syntax) to XPath and XQuery.</span></span> <span data-ttu-id="2e22d-123">Integracja [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] w języku Visual Basic zapewnia silniejsze pisowni, kompilacji sprawdzanie i ulepszona obsługa debugera.</span><span class="sxs-lookup"><span data-stu-id="2e22d-123">The integration of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] in Visual Basic provides stronger typing, compile-time checking, and improved debugger support.</span></span>  
  
 <span data-ttu-id="2e22d-124">Inną zaletą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest możliwość używania wyniki zapytania jako parametry <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> konstruktorów obiektów umożliwia wydajne podejście do tworzenia drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="2e22d-124">Another advantage of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is the ability to use query results as parameters to <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> object constructors enables a powerful approach to creating XML trees.</span></span> <span data-ttu-id="2e22d-125">Takie podejście, nazywany *funkcjonalności konstrukcji*, umożliwia deweloperom łatwe transformacji XML drzew z jednego kształtu do innego.</span><span class="sxs-lookup"><span data-stu-id="2e22d-125">This approach, called *functional construction*, enables developers to easily transform XML trees from one shape to another.</span></span>  
  
 <span data-ttu-id="2e22d-126">Na przykład może być typowe XML, zamówienie, zgodnie z opisem w [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348).</span><span class="sxs-lookup"><span data-stu-id="2e22d-126">For example, you might have a typical XML purchase order as described in [Sample XML File: Typical Purchase Order (LINQ to XML)](http://msdn.microsoft.com/library/0606c09f-6e43-4f8d-95c8-e8e2e08d2348).</span></span> <span data-ttu-id="2e22d-127">Przy użyciu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można uruchomić następujące zapytanie, aby uzyskać części wartość atrybutu liczba dla każdego elementu w zamówieniu zakupu:</span><span class="sxs-lookup"><span data-stu-id="2e22d-127">By using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you could run the following query to obtain the part number attribute value for every item element in the purchase order:</span></span>  
  
```vb  
Dim partNos = _  
    From item In purchaseOrder...<Item> _  
    Select item.@PartNumber  
```  
  
 <span data-ttu-id="2e22d-128">Innym przykładem może być listę posortowane według numer części elementów o wartości większej niż 100.</span><span class="sxs-lookup"><span data-stu-id="2e22d-128">As another example, you might want a list, sorted by part number, of the items with a value greater than $100.</span></span> <span data-ttu-id="2e22d-129">Aby uzyskać te informacje, można uruchomić następujące zapytanie:</span><span class="sxs-lookup"><span data-stu-id="2e22d-129">To obtain this information, you could run the following query:</span></span>  
  
```vb  
Dim partNos = _  
From item In purchaseOrder...<Item> _  
Where (item.<Quantity>.Value * _  
       item.<USPrice>.Value) > 100 _  
Order By item.<PartNumber>.Value _  
Select item  
```  
  
 <span data-ttu-id="2e22d-130">Oprócz wspomnianych [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] możliwości, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zawiera udoskonalony interfejs programowania XML.</span><span class="sxs-lookup"><span data-stu-id="2e22d-130">In addition to these [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] capabilities, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] provides an improved XML programming interface.</span></span> <span data-ttu-id="2e22d-131">Przy użyciu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można wykonywać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="2e22d-131">Using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can:</span></span>  
  
-   <span data-ttu-id="2e22d-132">Ładowanie XML z plików lub strumieni.</span><span class="sxs-lookup"><span data-stu-id="2e22d-132">Load XML from files or streams.</span></span>  
  
-   <span data-ttu-id="2e22d-133">Serializacji XML do plików i strumieni.</span><span class="sxs-lookup"><span data-stu-id="2e22d-133">Serialize XML to files or streams.</span></span>  
  
-   <span data-ttu-id="2e22d-134">Tworzenie XML od podstaw przy użyciu konstrukcji funkcjonalności.</span><span class="sxs-lookup"><span data-stu-id="2e22d-134">Create XML from scratch by using functional construction.</span></span>  
  
-   <span data-ttu-id="2e22d-135">Badać kodu XML za pomocą notacji języka XPath osi.</span><span class="sxs-lookup"><span data-stu-id="2e22d-135">Query XML using XPath-like axes.</span></span>  
  
-   <span data-ttu-id="2e22d-136">Manipulowanie drzewa XML w pamięci przy użyciu metod, takich jak <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, i <xref:System.Xml.Linq.XElement.SetValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="2e22d-136">Manipulate the in-memory XML tree by using methods such as <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, and <xref:System.Xml.Linq.XElement.SetValue%2A>.</span></span>  
  
-   <span data-ttu-id="2e22d-137">Sprawdź poprawność drzew XML za pomocą schematu XSD.</span><span class="sxs-lookup"><span data-stu-id="2e22d-137">Validate XML trees using XSD.</span></span>  
  
-   <span data-ttu-id="2e22d-138">Użyj kombinacji tych funkcji do transformacji XML drzew z jednego kształtu do innego.</span><span class="sxs-lookup"><span data-stu-id="2e22d-138">Use a combination of these features to transform XML trees from one shape into another.</span></span>  
  
## <a name="creating-xml-trees"></a><span data-ttu-id="2e22d-139">Tworzenie XML drzewa</span><span class="sxs-lookup"><span data-stu-id="2e22d-139">Creating XML Trees</span></span>  
 <span data-ttu-id="2e22d-140">IOne najważniejszych zalet programowania w języku [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] jest łatwo tworzyć drzew XML.</span><span class="sxs-lookup"><span data-stu-id="2e22d-140">IOne of the most significant advantages of programming with [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] is that it is easy to create XML trees.</span></span> <span data-ttu-id="2e22d-141">Na przykład aby utworzyć drzewo małych XML, można napisać kod w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="2e22d-141">For example, to create a small XML tree, you can write  code as follows:</span></span>  
  
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
  
 <span data-ttu-id="2e22d-142">Kompilator Visual Basic tłumaczy literałów XML do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="2e22d-142">The Visual Basic compiler translates XML literals into [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] method calls.</span></span>  
  
 <span data-ttu-id="2e22d-143">Aby uzyskać więcej informacji, zobacz [tworzenia drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="2e22d-143">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e22d-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e22d-144">See Also</span></span>  
 <xref:System.Xml.Linq>  
 [<span data-ttu-id="2e22d-145">Wprowadzenie (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="2e22d-145">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)  
 [<span data-ttu-id="2e22d-146">Przegląd LINQ do XML w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e22d-146">Overview of LINQ to XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/overview-of-linq-to-xml.md)  
 [<span data-ttu-id="2e22d-147">XML</span><span class="sxs-lookup"><span data-stu-id="2e22d-147">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
