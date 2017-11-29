---
title: LINQ do XML programu vs. Modelu DOM (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18c36130-d598-40b7-9007-828232252978
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1f89d3ded61daf16d4a59ccabb4d58625cae4a58
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a><span data-ttu-id="0815e-102">LINQ do XML programu vs. Modelu DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0815e-102">LINQ to XML vs. DOM (Visual Basic)</span></span>
<span data-ttu-id="0815e-103">W tej sekcji opisano niektóre podstawowe różnice między [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] i bieżącego XML dominujący programowania interfejsu API, W3C modelu DOM (Document Object).</span><span class="sxs-lookup"><span data-stu-id="0815e-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="0815e-104">Nowe sposoby tworzenia drzewa XML</span><span class="sxs-lookup"><span data-stu-id="0815e-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="0815e-105">W modelu DOM W3C drzewo XML od dołu kompilacji oznacza to Utwórz dokument, tworzenie elementów, a następnie dodaj elementy do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0815e-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="0815e-106">Na przykład następujące będzie typowy sposób tworzenia drzewa XML za pomocą przez firmę Microsoft implementacją modelu DOM, <xref:System.Xml.XmlDocument>:</span><span class="sxs-lookup"><span data-stu-id="0815e-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
Dim phone1 As XmlElement = doc.CreateElement("Phone")  
phone1.SetAttribute("Type", "Home")  
phone1.InnerText = "206-555-0144"  
Dim phone2 As XmlElement = doc.CreateElement("Phone")  
phone2.SetAttribute("Type", "Work")  
phone2.InnerText = "425-555-0145"  
Dim street1 As XmlElement = doc.CreateElement("Street1")  
street1.InnerText = "123 Main St"  
Dim city As XmlElement = doc.CreateElement("City")  
city.InnerText = "Mercer Island"  
Dim state As XmlElement = doc.CreateElement("State")  
state.InnerText = "WA"  
Dim postal As XmlElement = doc.CreateElement("Postal")  
postal.InnerText = "68042"  
Dim address As XmlElement = doc.CreateElement("Address")  
address.AppendChild(street1)  
address.AppendChild(city)  
address.AppendChild(state)  
address.AppendChild(postal)  
Dim contact As XmlElement = doc.CreateElement("Contact")  
contact.AppendChild(name)  
contact.AppendChild(phone1)  
contact.AppendChild(phone2)  
contact.AppendChild(address)  
Dim contacts As XmlElement = doc.CreateElement("Contacts")  
contacts.AppendChild(contact)  
doc.AppendChild(contacts)  
Console.WriteLine(doc.OuterXml)  
```  
  
 <span data-ttu-id="0815e-107">Ten styl kodowania nie zapewnia wizualnie dużej ilości informacji o strukturze drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="0815e-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0815e-108">obsługuje takie podejście do konstruowania drzewo XML, ale obsługuje także alternatywne podejście *funkcjonalności konstrukcji*.</span><span class="sxs-lookup"><span data-stu-id="0815e-108"> supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="0815e-109">W języku Visual Basic funkcjonalności konstrukcji używa literałów XML do konstruowania drzewo XML.</span><span class="sxs-lookup"><span data-stu-id="0815e-109">In Visual Basic, functional construction uses XML literals to build an XML tree.</span></span>  
  
 <span data-ttu-id="0815e-110">Oto jak będzie skonstruować tym samym drzewie XML za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] konstrukcji funkcjonalności:</span><span class="sxs-lookup"><span data-stu-id="0815e-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="0815e-111">Zwróć uwagę, że wcięcia kodu można utworzyć drzewa XML zawiera struktury XML podstawowej.</span><span class="sxs-lookup"><span data-stu-id="0815e-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="0815e-112">Aby uzyskać więcej informacji, zobacz [tworzenia drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="0815e-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="0815e-113">Praca bezpośrednio z elementów XML</span><span class="sxs-lookup"><span data-stu-id="0815e-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="0815e-114">Podczas programowania za pomocą XML programu głównym celem jest zwykle na elementy XML i być może w atrybutach.</span><span class="sxs-lookup"><span data-stu-id="0815e-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="0815e-115">W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], możesz pracować bezpośrednio z elementów XML oraz atrybuty.</span><span class="sxs-lookup"><span data-stu-id="0815e-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="0815e-116">Można na przykład, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="0815e-116">For example, you can do the following:</span></span>  
  
-   <span data-ttu-id="0815e-117">Utwórz elementy XML bez użycia obiektu dokumentu w ogóle.</span><span class="sxs-lookup"><span data-stu-id="0815e-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="0815e-118">Upraszcza programowanie podczas pracy z fragmenty XML drzewa.</span><span class="sxs-lookup"><span data-stu-id="0815e-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
-   <span data-ttu-id="0815e-119">Obciążenia `T:System.Xml.Linq.XElement` obiektów bezpośrednio z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="0815e-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
-   <span data-ttu-id="0815e-120">Serializować `T:System.Xml.Linq.XElement` obiektów w pliku lub strumienia.</span><span class="sxs-lookup"><span data-stu-id="0815e-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="0815e-121">To porównać do modelu DOM W3C, w którym dokumentu XML służy jako kontener logiczny do drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="0815e-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="0815e-122">W modelu DOM węzłów XML, w tym elementów i atrybutów, należy utworzyć w kontekście dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0815e-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="0815e-123">Oto fragment kodu, aby utworzyć element nazwy w modelu DOM:</span><span class="sxs-lookup"><span data-stu-id="0815e-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 <span data-ttu-id="0815e-124">Jeśli chcesz użyć elementu w wielu dokumentach, należy zaimportować węzłów w dokumentach.</span><span class="sxs-lookup"><span data-stu-id="0815e-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0815e-125">pozwala uniknąć tej warstwy złożoności.</span><span class="sxs-lookup"><span data-stu-id="0815e-125"> avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="0815e-126">Podczas korzystania z LINQ do XML, użyj <xref:System.Xml.Linq.XDocument> klasy tylko, jeśli chcesz dodać komentarz lub przetwarzania instrukcję na głównym poziomie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0815e-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="0815e-127">Uproszczone Obsługa nazwy i przestrzenie nazw</span><span class="sxs-lookup"><span data-stu-id="0815e-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="0815e-128">Obsługa nazwy przestrzeni nazw i prefiksy przestrzeni nazw jest zwykle złożonych częścią programowania w języku XML.</span><span class="sxs-lookup"><span data-stu-id="0815e-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0815e-129">upraszcza nazwy i przestrzenie nazw, eliminując konieczność postępowania w przypadku prefiksy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0815e-129"> simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="0815e-130">Jeśli chcesz kontrolować prefiksy przestrzeni nazw, możesz.</span><span class="sxs-lookup"><span data-stu-id="0815e-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="0815e-131">Jeśli zdecydujesz się nie jawnie kontrolować prefiksy przestrzeni nazw, jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] przypisze prefiksy przestrzeni nazw podczas serializacji, jeśli są wymagane lub będzie serializować przy użyciu domyślne obszary nazw, jeśli nie są one.</span><span class="sxs-lookup"><span data-stu-id="0815e-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="0815e-132">Jeśli są używane domyślne obszary nazw, nie będzie żadnych prefiksów przestrzeni nazw w wynikowym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="0815e-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="0815e-133">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeni nazw XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="0815e-133">For more information, see [Working with XML Namespaces (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).</span></span>  
  
 <span data-ttu-id="0815e-134">Inny problem z modelu DOM jest, że nie zezwala można zmienić nazwy węzła.</span><span class="sxs-lookup"><span data-stu-id="0815e-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="0815e-135">Zamiast tego należy utworzyć nowy węzeł i skopiuj wszystkie węzły podrzędne, utraty oryginalnej tożsamości węzła.</span><span class="sxs-lookup"><span data-stu-id="0815e-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0815e-136">w celu uniknięcia tego problemu, należy włączyć ustawienia <xref:System.Xml.Linq.XName> właściwość w węźle.</span><span class="sxs-lookup"><span data-stu-id="0815e-136"> avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="0815e-137">Obsługa statycznej metody ładowania danych XML</span><span class="sxs-lookup"><span data-stu-id="0815e-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0815e-138">Umożliwia ładowanie pliku XML przy użyciu metody statyczne, zamiast metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="0815e-138"> lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="0815e-139">Upraszcza to załadowanie i analiza kodu.</span><span class="sxs-lookup"><span data-stu-id="0815e-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="0815e-140">Aby uzyskać więcej informacji, zobacz [porady: obciążenia XML z pliku (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="0815e-140">For more information, see [How to: Load XML from a File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="0815e-141">Usunięcie wsparcia dla konstrukcji DTD</span><span class="sxs-lookup"><span data-stu-id="0815e-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0815e-142">dodatkowo upraszcza programowanie przez usunięcie obsługę jednostek i odwołań do jednostek XML.</span><span class="sxs-lookup"><span data-stu-id="0815e-142"> further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="0815e-143">Zarządzanie jednostkami jest złożony i jest rzadko używana.</span><span class="sxs-lookup"><span data-stu-id="0815e-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="0815e-144">Usunięcie ich obsługa zwiększa wydajność i upraszcza interfejsu programowania.</span><span class="sxs-lookup"><span data-stu-id="0815e-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="0815e-145">Gdy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] drzewa zostanie wypełnione, zostaną rozwinięte wszystkie jednostki DTD.</span><span class="sxs-lookup"><span data-stu-id="0815e-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="0815e-146">Obsługa fragmentów</span><span class="sxs-lookup"><span data-stu-id="0815e-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0815e-147">nie ma odpowiednika dla `XmlDocumentFragment` klasy.</span><span class="sxs-lookup"><span data-stu-id="0815e-147"> does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="0815e-148">W wielu przypadkach, jednak `XmlDocumentFragment` koncepcji są obsługiwane przez wyników zapytania, które jest typu <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XNode>, lub <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="0815e-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="0815e-149">Obsługa parametrem XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="0815e-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0815e-150">zapewnia obsługę <xref:System.Xml.XPath.XPathNavigator> za pośrednictwem metody rozszerzenia w <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0815e-150"> provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="0815e-151">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0815e-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="0815e-152">Obsługa biały znak i wcięcie</span><span class="sxs-lookup"><span data-stu-id="0815e-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0815e-153">obsługuje biały znak prostsze niż modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="0815e-153"> handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="0815e-154">Typowy scenariusz jest Odczytaj dane XML z wcięciami, utwórz drzewo XML w pamięci bez żadnych białe węzły tekstowe (to znaczy nie zachowania biały znak), operacji na pliku XML, a następnie zapisz plik XML z wcięcia.</span><span class="sxs-lookup"><span data-stu-id="0815e-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="0815e-155">Podczas formatowania kodu XML, tylko znaczący biały znak w drzewie XML są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="0815e-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="0815e-156">Jest to domyślne zachowanie dla [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0815e-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="0815e-157">Inny typowy scenariusz polega może odczytywać i modyfikować XML, który już został celowo wcięcia.</span><span class="sxs-lookup"><span data-stu-id="0815e-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="0815e-158">Nie można zmienić tej wcięcia w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="0815e-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="0815e-159">W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], aby to zrobić, zachowując biały znak po załadowaniu lub analizy kodu XML i wyłączanie formatowania podczas serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="0815e-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0815e-160">przechowuje biały znak jako <xref:System.Xml.Linq.XText> węzła, zamiast specjalistycznej <xref:System.Xml.XmlNodeType.Whitespace> typ węzła jako model DOM jest.</span><span class="sxs-lookup"><span data-stu-id="0815e-160"> stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="0815e-161">Obsługa adnotacji</span><span class="sxs-lookup"><span data-stu-id="0815e-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0815e-162">elementy obsługują rozszerzony zbiór adnotacji.</span><span class="sxs-lookup"><span data-stu-id="0815e-162"> elements support an extensible set of annotations.</span></span> <span data-ttu-id="0815e-163">Jest to przydatne w przypadku śledzenia dodatkowych informacji na temat elementu, takie jak informacje o schemacie, informacji na temat tego, czy element jest powiązany z interfejsu użytkownika lub inne informacje dotyczące rodzaju specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0815e-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="0815e-164">Aby uzyskać więcej informacji, zobacz [LINQ do XML adnotacje](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).</span><span class="sxs-lookup"><span data-stu-id="0815e-164">For more information, see [LINQ to XML Annotations](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="0815e-165">Obsługa informacji o schemacie</span><span class="sxs-lookup"><span data-stu-id="0815e-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0815e-166">zapewnia obsługę sprawdzania poprawności XSD za pośrednictwem metody rozszerzenia w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0815e-166"> provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="0815e-167">Aby zweryfikować, że drzewo XML jest zgodny z XSD.</span><span class="sxs-lookup"><span data-stu-id="0815e-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="0815e-168">Można go wypełnić drzewa XML z typu infoset po schema weryfikacji (PSVI).</span><span class="sxs-lookup"><span data-stu-id="0815e-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="0815e-169">Aby uzyskać więcej informacji, zobacz [porady: Sprawdzanie poprawności za pomocą schematu XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) i <xref:System.Xml.Schema.Extensions>.</span><span class="sxs-lookup"><span data-stu-id="0815e-169">For more information, see [How to: Validate Using XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0815e-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0815e-170">See Also</span></span>  
 [<span data-ttu-id="0815e-171">Wprowadzenie (LINQ do XML)</span><span class="sxs-lookup"><span data-stu-id="0815e-171">Getting Started (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
