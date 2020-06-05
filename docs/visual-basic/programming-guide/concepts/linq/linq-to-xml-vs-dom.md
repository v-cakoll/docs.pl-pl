---
title: LINQ to XML a DOM
ms.date: 07/20/2015
ms.assetid: 18c36130-d598-40b7-9007-828232252978
ms.openlocfilehash: 5813ca410e3e2b1ec284681451d0c0cec6f5e393
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389335"
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a><span data-ttu-id="975e0-102">LINQ to XML a DOM (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="975e0-102">LINQ to XML vs. DOM (Visual Basic)</span></span>
<span data-ttu-id="975e0-103">W tej sekcji opisano niektóre kluczowe różnice między programem [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] a obecnym głównym interfejsem API programowania plików XML, W3C Document Object Model (dom).</span><span class="sxs-lookup"><span data-stu-id="975e0-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="975e0-104">Nowe sposoby konstruowania drzew XML</span><span class="sxs-lookup"><span data-stu-id="975e0-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="975e0-105">W modelu W3C DOM utworzysz drzewo XML od dołu do góry. oznacza to, że tworzysz dokument, tworzysz elementy, a następnie dodasz elementy do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="975e0-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="975e0-106">Na przykład poniżej przedstawiono typowy sposób tworzenia drzewa XML przy użyciu implementacji modelu DOM firmy Microsoft <xref:System.Xml.XmlDocument> :</span><span class="sxs-lookup"><span data-stu-id="975e0-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="975e0-107">Ten styl kodowania nie udostępnia wizualizacji więcej informacji o strukturze drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="975e0-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="975e0-108">obsługuje to podejście do konstruowania drzewa XML, ale również obsługuje alternatywne podejście, *konstrukcja funkcjonalna*.</span><span class="sxs-lookup"><span data-stu-id="975e0-108">supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="975e0-109">W Visual Basic, konstrukcja funkcjonalna używa literałów XML do tworzenia drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="975e0-109">In Visual Basic, functional construction uses XML literals to build an XML tree.</span></span>  
  
 <span data-ttu-id="975e0-110">Poniżej przedstawiono sposób konstruowania tego samego drzewa XML przy użyciu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] konstrukcji funkcjonalnej:</span><span class="sxs-lookup"><span data-stu-id="975e0-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="975e0-111">Zwróć uwagę, że Wcięcie kodu w celu skonstruowania drzewa XML pokazuje strukturę bazowego kodu XML.</span><span class="sxs-lookup"><span data-stu-id="975e0-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="975e0-112">Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML (Visual Basic)](creating-xml-trees.md).</span><span class="sxs-lookup"><span data-stu-id="975e0-112">For more information, see [Creating XML Trees (Visual Basic)](creating-xml-trees.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="975e0-113">Praca bezpośrednio z elementami XML</span><span class="sxs-lookup"><span data-stu-id="975e0-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="975e0-114">Gdy program jest używany w języku XML, główny fokus jest zazwyczaj na elementach XML i prawdopodobnie na atrybutach.</span><span class="sxs-lookup"><span data-stu-id="975e0-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="975e0-115">W programie można [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bezpośrednio korzystać z elementów i atrybutów XML.</span><span class="sxs-lookup"><span data-stu-id="975e0-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="975e0-116">Można na przykład wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="975e0-116">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="975e0-117">Utwórz elementy XML bez używania obiektu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="975e0-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="975e0-118">Upraszcza to programowanie, gdy trzeba będzie korzystać z fragmentów drzew XML.</span><span class="sxs-lookup"><span data-stu-id="975e0-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="975e0-119">Załaduj `T:System.Xml.Linq.XElement` obiekty bezpośrednio z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="975e0-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="975e0-120">Serializacja `T:System.Xml.Linq.XElement` obiektów do pliku lub strumienia.</span><span class="sxs-lookup"><span data-stu-id="975e0-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="975e0-121">Porównaj ten element z W3C DOM, w którym dokument XML jest używany jako kontener logiczny dla drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="975e0-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="975e0-122">W modelu DOM, węzły XML, w tym elementy i atrybuty, muszą zostać utworzone w kontekście dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="975e0-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="975e0-123">Oto fragment kodu do utworzenia elementu Name w modelu DOM:</span><span class="sxs-lookup"><span data-stu-id="975e0-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 <span data-ttu-id="975e0-124">Jeśli chcesz użyć elementu w wielu dokumentach, należy zaimportować węzły między dokumentami.</span><span class="sxs-lookup"><span data-stu-id="975e0-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="975e0-125">pozwala uniknąć tej warstwy złożoności.</span><span class="sxs-lookup"><span data-stu-id="975e0-125">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="975e0-126">W przypadku używania LINQ to XML Klasa jest używana <xref:System.Xml.Linq.XDocument> tylko wtedy, gdy chcesz dodać komentarz lub instrukcję przetwarzania na poziomie głównym dokumentu.</span><span class="sxs-lookup"><span data-stu-id="975e0-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="975e0-127">Uproszczona obsługa nazw i przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="975e0-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="975e0-128">Obsługa nazw, przestrzeni nazw i prefiksów przestrzeni nazw jest ogólnie złożonym elementem programowania XML.</span><span class="sxs-lookup"><span data-stu-id="975e0-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="975e0-129">upraszcza nazwy i przestrzenie nazw, eliminując wymóg postępowania z prefiksami przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="975e0-129">simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="975e0-130">Jeśli chcesz kontrolować prefiksy przestrzeni nazw, możesz.</span><span class="sxs-lookup"><span data-stu-id="975e0-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="975e0-131">Ale jeśli zdecydujesz się nie jawnie kontrolować prefiksów przestrzeni nazw, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] program przypisze prefiksy przestrzeni nazw podczas serializacji, jeśli są wymagane, lub będzie serializować przy użyciu domyślnych przestrzeni nazw, jeśli nie.</span><span class="sxs-lookup"><span data-stu-id="975e0-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="975e0-132">Jeśli są używane domyślne przestrzenie nazw, nie będzie żadnych prefiksów przestrzeni nazw w dokumencie będącym wynikiem.</span><span class="sxs-lookup"><span data-stu-id="975e0-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="975e0-133">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="975e0-133">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="975e0-134">Innym problemem z modelem DOM jest to, że nie pozwala na zmianę nazwy węzła.</span><span class="sxs-lookup"><span data-stu-id="975e0-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="975e0-135">Zamiast tego należy utworzyć nowy węzeł i skopiować do niego wszystkie węzły podrzędne, tracąc oryginalną tożsamość węzła.</span><span class="sxs-lookup"><span data-stu-id="975e0-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="975e0-136">pozwala uniknąć tego problemu, umożliwiając ustawienie <xref:System.Xml.Linq.XName> właściwości w węźle.</span><span class="sxs-lookup"><span data-stu-id="975e0-136">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="975e0-137">Obsługa metody statycznej do ładowania pliku XML</span><span class="sxs-lookup"><span data-stu-id="975e0-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="975e0-138">umożliwia ładowanie XML przy użyciu metod statycznych zamiast metod instancji.</span><span class="sxs-lookup"><span data-stu-id="975e0-138">lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="975e0-139">Upraszcza to ładowanie i analizowanie.</span><span class="sxs-lookup"><span data-stu-id="975e0-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="975e0-140">Aby uzyskać więcej informacji, zobacz [How to: Load XML from a File (Visual Basic)](how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="975e0-140">For more information, see [How to: Load XML from a File (Visual Basic)](how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="975e0-141">Usuwanie obsługi dla konstrukcji DTD</span><span class="sxs-lookup"><span data-stu-id="975e0-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="975e0-142">bardziej upraszcza programowanie XML przez usunięcie obsługi jednostek i odwołań do jednostek.</span><span class="sxs-lookup"><span data-stu-id="975e0-142">further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="975e0-143">Zarządzanie jednostkami jest skomplikowane i rzadko jest używane.</span><span class="sxs-lookup"><span data-stu-id="975e0-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="975e0-144">Usunięcie ich obsługi zwiększa wydajność i upraszcza interfejs programowania.</span><span class="sxs-lookup"><span data-stu-id="975e0-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="975e0-145">Po [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wypełnieniu drzewa wszystkie jednostki DTD są rozwinięte.</span><span class="sxs-lookup"><span data-stu-id="975e0-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="975e0-146">Obsługa fragmentów</span><span class="sxs-lookup"><span data-stu-id="975e0-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="975e0-147">nie zapewnia równoważnej `XmlDocumentFragment` klasy.</span><span class="sxs-lookup"><span data-stu-id="975e0-147">does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="975e0-148">W wielu przypadkach `XmlDocumentFragment` koncepcje mogą być obsługiwane przez wynik zapytania, które zostało wpisane w <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XNode> lub <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="975e0-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="975e0-149">Obsługa elementu XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="975e0-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="975e0-150">zapewnia obsługę <xref:System.Xml.XPath.XPathNavigator> za pomocą metod rozszerzających w <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="975e0-150">provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="975e0-151">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="975e0-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="975e0-152">Obsługa białych znaków i wcięć</span><span class="sxs-lookup"><span data-stu-id="975e0-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="975e0-153">obsługuje biały znak więcej niż w modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="975e0-153">handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="975e0-154">Typowym scenariuszem jest odczytywanie wciętych plików XML, tworzenie drzewa XML w pamięci bez jakichkolwiek białych węzłów tekstowych (to nie zachowuje białych znaków), wykonywanie niektórych operacji na pliku XML, a następnie zapisywanie kodu XML z wcięciem.</span><span class="sxs-lookup"><span data-stu-id="975e0-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="975e0-155">Podczas serializacji pliku XML z formatowaniem zachowywana jest tylko znaczący biały znak w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="975e0-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="975e0-156">Jest to zachowanie domyślne dla programu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="975e0-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="975e0-157">Inny typowy scenariusz polega na odczytaniu i zmodyfikowaniu kodu XML, który został już celowo wcięty.</span><span class="sxs-lookup"><span data-stu-id="975e0-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="975e0-158">W żaden sposób nie trzeba zmieniać tego wcięcia.</span><span class="sxs-lookup"><span data-stu-id="975e0-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="975e0-159">W programie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można to zrobić przez zachowanie białych znaków podczas ładowania lub analizowania kodu XML oraz wyłączanie formatowania podczas serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="975e0-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="975e0-160">zapisuje biały znak jako <xref:System.Xml.Linq.XText> węzeł, zamiast mieć wyspecjalizowany <xref:System.Xml.XmlNodeType.Whitespace> Typ węzła, jak dom.</span><span class="sxs-lookup"><span data-stu-id="975e0-160">stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="975e0-161">Obsługa adnotacji</span><span class="sxs-lookup"><span data-stu-id="975e0-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="975e0-162">elementy obsługują rozszerzalny zestaw adnotacji.</span><span class="sxs-lookup"><span data-stu-id="975e0-162">elements support an extensible set of annotations.</span></span> <span data-ttu-id="975e0-163">Jest to przydatne do śledzenia różnych informacji o elemencie, takich jak informacje o schemacie, informacje o tym, czy element jest powiązany z interfejsem użytkownika, czy też innym rodzajem informacji specyficznych dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="975e0-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="975e0-164">Aby uzyskać więcej informacji, zobacz [LINQ to XML adnotacje](linq-to-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="975e0-164">For more information, see [LINQ to XML Annotations](linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="975e0-165">Obsługa informacji o schemacie</span><span class="sxs-lookup"><span data-stu-id="975e0-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="975e0-166">zapewnia obsługę walidacji XSD za pomocą metod rozszerzających w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="975e0-166">provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="975e0-167">Można sprawdzić, czy drzewo XML jest zgodne z XSD.</span><span class="sxs-lookup"><span data-stu-id="975e0-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="975e0-168">Drzewo XML można wypełnić za pomocą sprawdzonych po walidacji schematu (PSVI).</span><span class="sxs-lookup"><span data-stu-id="975e0-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="975e0-169">Aby uzyskać więcej informacji, zobacz [How to: Validate using XSD](how-to-validate-using-xsd-linq-to-xml.md) i <xref:System.Xml.Schema.Extensions> .</span><span class="sxs-lookup"><span data-stu-id="975e0-169">For more information, see [How to: Validate Using XSD](how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="975e0-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="975e0-170">See also</span></span>

- [<span data-ttu-id="975e0-171">Wprowadzenie (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="975e0-171">Getting Started (LINQ to XML)</span></span>](getting-started-linq-to-xml.md)
