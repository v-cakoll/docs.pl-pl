---
title: LINQ to XML a DOM (C#)
description: Poznaj kilka najważniejszych różnic między LINQ to XML i interfejsem API programowania W3C Document Object Model (DOM) XML.
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: f5fc3fd7869079d47d7c9031e3668afeed7a117b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165343"
---
# <a name="linq-to-xml-vs-dom-c"></a><span data-ttu-id="59de6-103">LINQ to XML a DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="59de6-103">LINQ to XML vs. DOM (C#)</span></span>
<span data-ttu-id="59de6-104">W tej sekcji opisano niektóre kluczowe różnice między programem [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] a obecnym głównym interfejsem API programowania plików XML, W3C Document Object Model (dom).</span><span class="sxs-lookup"><span data-stu-id="59de6-104">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="59de6-105">Nowe sposoby konstruowania drzew XML</span><span class="sxs-lookup"><span data-stu-id="59de6-105">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="59de6-106">W modelu W3C DOM utworzysz drzewo XML od dołu do góry. oznacza to, że tworzysz dokument, tworzysz elementy, a następnie dodasz elementy do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="59de6-106">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="59de6-107">Na przykład poniżej przedstawiono typowy sposób tworzenia drzewa XML przy użyciu implementacji modelu DOM firmy Microsoft <xref:System.Xml.XmlDocument> :</span><span class="sxs-lookup"><span data-stu-id="59de6-107">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
XmlElement phone1 = doc.CreateElement("Phone");  
phone1.SetAttribute("Type", "Home");  
phone1.InnerText = "206-555-0144";
XmlElement phone2 = doc.CreateElement("Phone");  
phone2.SetAttribute("Type", "Work");  
phone2.InnerText = "425-555-0145";
XmlElement street1 = doc.CreateElement("Street1");
street1.InnerText = "123 Main St";  
XmlElement city = doc.CreateElement("City");  
city.InnerText = "Mercer Island";  
XmlElement state = doc.CreateElement("State");  
state.InnerText = "WA";  
XmlElement postal = doc.CreateElement("Postal");  
postal.InnerText = "68042";  
XmlElement address = doc.CreateElement("Address");  
address.AppendChild(street1);  
address.AppendChild(city);  
address.AppendChild(state);  
address.AppendChild(postal);  
XmlElement contact = doc.CreateElement("Contact");  
contact.AppendChild(name);  
contact.AppendChild(phone1);  
contact.AppendChild(phone2);  
contact.AppendChild(address);  
XmlElement contacts = doc.CreateElement("Contacts");  
contacts.AppendChild(contact);  
doc.AppendChild(contacts);  
```  
  
 <span data-ttu-id="59de6-108">Ten styl kodowania nie udostępnia wizualizacji więcej informacji o strukturze drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="59de6-108">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="59de6-109">obsługuje to podejście do konstruowania drzewa XML, ale również obsługuje alternatywne podejście, *konstrukcja funkcjonalna*.</span><span class="sxs-lookup"><span data-stu-id="59de6-109">supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="59de6-110">Konstrukcja funkcjonalna używa <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> konstruktorów i do tworzenia drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="59de6-110">Functional construction uses the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors to build an XML tree.</span></span>  
  
 <span data-ttu-id="59de6-111">Poniżej przedstawiono sposób konstruowania tego samego drzewa XML przy użyciu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] konstrukcji funkcjonalnej:</span><span class="sxs-lookup"><span data-stu-id="59de6-111">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="59de6-112">Zwróć uwagę, że Wcięcie kodu w celu skonstruowania drzewa XML pokazuje strukturę bazowego kodu XML.</span><span class="sxs-lookup"><span data-stu-id="59de6-112">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="59de6-113">Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML (C#)](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="59de6-113">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="59de6-114">Praca bezpośrednio z elementami XML</span><span class="sxs-lookup"><span data-stu-id="59de6-114">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="59de6-115">Gdy program jest używany w języku XML, główny fokus jest zazwyczaj na elementach XML i prawdopodobnie na atrybutach.</span><span class="sxs-lookup"><span data-stu-id="59de6-115">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="59de6-116">W programie można [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bezpośrednio korzystać z elementów i atrybutów XML.</span><span class="sxs-lookup"><span data-stu-id="59de6-116">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="59de6-117">Można na przykład wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="59de6-117">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="59de6-118">Utwórz elementy XML bez używania obiektu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="59de6-118">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="59de6-119">Upraszcza to programowanie, gdy trzeba będzie korzystać z fragmentów drzew XML.</span><span class="sxs-lookup"><span data-stu-id="59de6-119">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="59de6-120">Załaduj `T:System.Xml.Linq.XElement` obiekty bezpośrednio z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="59de6-120">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="59de6-121">Serializacja `T:System.Xml.Linq.XElement` obiektów do pliku lub strumienia.</span><span class="sxs-lookup"><span data-stu-id="59de6-121">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="59de6-122">Porównaj ten element z W3C DOM, w którym dokument XML jest używany jako kontener logiczny dla drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="59de6-122">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="59de6-123">W modelu DOM, węzły XML, w tym elementy i atrybuty, muszą zostać utworzone w kontekście dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="59de6-123">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="59de6-124">Oto fragment kodu do utworzenia elementu Name w modelu DOM:</span><span class="sxs-lookup"><span data-stu-id="59de6-124">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 <span data-ttu-id="59de6-125">Jeśli chcesz użyć elementu w wielu dokumentach, należy zaimportować węzły między dokumentami.</span><span class="sxs-lookup"><span data-stu-id="59de6-125">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="59de6-126">pozwala uniknąć tej warstwy złożoności.</span><span class="sxs-lookup"><span data-stu-id="59de6-126">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="59de6-127">W przypadku używania LINQ to XML Klasa jest używana <xref:System.Xml.Linq.XDocument> tylko wtedy, gdy chcesz dodać komentarz lub instrukcję przetwarzania na poziomie głównym dokumentu.</span><span class="sxs-lookup"><span data-stu-id="59de6-127">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="59de6-128">Uproszczona obsługa nazw i przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="59de6-128">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="59de6-129">Obsługa nazw, przestrzeni nazw i prefiksów przestrzeni nazw jest ogólnie złożonym elementem programowania XML.</span><span class="sxs-lookup"><span data-stu-id="59de6-129">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="59de6-130">upraszcza nazwy i przestrzenie nazw, eliminując wymóg postępowania z prefiksami przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="59de6-130">simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="59de6-131">Jeśli chcesz kontrolować prefiksy przestrzeni nazw, możesz.</span><span class="sxs-lookup"><span data-stu-id="59de6-131">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="59de6-132">Ale jeśli zdecydujesz się nie jawnie kontrolować prefiksów przestrzeni nazw, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] program przypisze prefiksy przestrzeni nazw podczas serializacji, jeśli są wymagane, lub będzie serializować przy użyciu domyślnych przestrzeni nazw, jeśli nie.</span><span class="sxs-lookup"><span data-stu-id="59de6-132">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="59de6-133">Jeśli są używane domyślne przestrzenie nazw, nie będzie żadnych prefiksów przestrzeni nazw w dokumencie będącym wynikiem.</span><span class="sxs-lookup"><span data-stu-id="59de6-133">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="59de6-134">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="59de6-134">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="59de6-135">Innym problemem z modelem DOM jest to, że nie pozwala na zmianę nazwy węzła.</span><span class="sxs-lookup"><span data-stu-id="59de6-135">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="59de6-136">Zamiast tego należy utworzyć nowy węzeł i skopiować do niego wszystkie węzły podrzędne, tracąc oryginalną tożsamość węzła.</span><span class="sxs-lookup"><span data-stu-id="59de6-136">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="59de6-137">pozwala uniknąć tego problemu, umożliwiając ustawienie <xref:System.Xml.Linq.XName> właściwości w węźle.</span><span class="sxs-lookup"><span data-stu-id="59de6-137">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="59de6-138">Obsługa metody statycznej do ładowania pliku XML</span><span class="sxs-lookup"><span data-stu-id="59de6-138">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="59de6-139">umożliwia ładowanie XML przy użyciu metod statycznych zamiast metod instancji.</span><span class="sxs-lookup"><span data-stu-id="59de6-139">lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="59de6-140">Upraszcza to ładowanie i analizowanie.</span><span class="sxs-lookup"><span data-stu-id="59de6-140">This simplifies loading and parsing.</span></span> <span data-ttu-id="59de6-141">Aby uzyskać więcej informacji, zobacz [jak załadować XML z pliku (C#)](./how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="59de6-141">For more information, see [How to load XML from a file (C#)](./how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="59de6-142">Usuwanie obsługi dla konstrukcji DTD</span><span class="sxs-lookup"><span data-stu-id="59de6-142">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="59de6-143">bardziej upraszcza programowanie XML przez usunięcie obsługi jednostek i odwołań do jednostek.</span><span class="sxs-lookup"><span data-stu-id="59de6-143">further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="59de6-144">Zarządzanie jednostkami jest skomplikowane i rzadko jest używane.</span><span class="sxs-lookup"><span data-stu-id="59de6-144">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="59de6-145">Usunięcie ich obsługi zwiększa wydajność i upraszcza interfejs programowania.</span><span class="sxs-lookup"><span data-stu-id="59de6-145">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="59de6-146">Po [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wypełnieniu drzewa wszystkie jednostki DTD są rozwinięte.</span><span class="sxs-lookup"><span data-stu-id="59de6-146">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="59de6-147">Obsługa fragmentów</span><span class="sxs-lookup"><span data-stu-id="59de6-147">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="59de6-148">nie zapewnia równoważnej `XmlDocumentFragment` klasy.</span><span class="sxs-lookup"><span data-stu-id="59de6-148">does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="59de6-149">W wielu przypadkach `XmlDocumentFragment` koncepcje mogą być obsługiwane przez wynik zapytania, które zostało wpisane w <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XNode> lub <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="59de6-149">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="59de6-150">Obsługa elementu XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="59de6-150">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="59de6-151">zapewnia obsługę <xref:System.Xml.XPath.XPathNavigator> za pomocą metod rozszerzających w <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="59de6-151">provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="59de6-152">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="59de6-152">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="59de6-153">Obsługa białych znaków i wcięć</span><span class="sxs-lookup"><span data-stu-id="59de6-153">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="59de6-154">obsługuje biały znak więcej niż w modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="59de6-154">handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="59de6-155">Typowym scenariuszem jest odczytywanie wciętych plików XML, tworzenie drzewa XML w pamięci bez jakichkolwiek białych węzłów tekstowych (to nie zachowuje białych znaków), wykonywanie niektórych operacji na pliku XML, a następnie zapisywanie kodu XML z wcięciem.</span><span class="sxs-lookup"><span data-stu-id="59de6-155">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="59de6-156">Podczas serializacji pliku XML z formatowaniem zachowywana jest tylko znaczący biały znak w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="59de6-156">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="59de6-157">Jest to zachowanie domyślne dla programu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="59de6-157">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="59de6-158">Inny typowy scenariusz polega na odczytaniu i zmodyfikowaniu kodu XML, który został już celowo wcięty.</span><span class="sxs-lookup"><span data-stu-id="59de6-158">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="59de6-159">W żaden sposób nie trzeba zmieniać tego wcięcia.</span><span class="sxs-lookup"><span data-stu-id="59de6-159">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="59de6-160">W programie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można to zrobić przez zachowanie białych znaków podczas ładowania lub analizowania kodu XML oraz wyłączanie formatowania podczas serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="59de6-160">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="59de6-161">zapisuje biały znak jako <xref:System.Xml.Linq.XText> węzeł, zamiast mieć wyspecjalizowany <xref:System.Xml.XmlNodeType.Whitespace> Typ węzła, jak dom.</span><span class="sxs-lookup"><span data-stu-id="59de6-161">stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="59de6-162">Obsługa adnotacji</span><span class="sxs-lookup"><span data-stu-id="59de6-162">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="59de6-163">elementy obsługują rozszerzalny zestaw adnotacji.</span><span class="sxs-lookup"><span data-stu-id="59de6-163">elements support an extensible set of annotations.</span></span> <span data-ttu-id="59de6-164">Jest to przydatne do śledzenia różnych informacji o elemencie, takich jak informacje o schemacie, informacje o tym, czy element jest powiązany z interfejsem użytkownika, czy też innym rodzajem informacji specyficznych dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="59de6-164">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="59de6-165">Aby uzyskać więcej informacji, zobacz [LINQ to XML adnotacje](./linq-to-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="59de6-165">For more information, see [LINQ to XML Annotations](./linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="59de6-166">Obsługa informacji o schemacie</span><span class="sxs-lookup"><span data-stu-id="59de6-166">Support for Schema Information</span></span>  
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="59de6-167">zapewnia obsługę walidacji XSD za pomocą metod rozszerzających w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="59de6-167">provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="59de6-168">Można sprawdzić, czy drzewo XML jest zgodne z XSD.</span><span class="sxs-lookup"><span data-stu-id="59de6-168">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="59de6-169">Drzewo XML można wypełnić za pomocą sprawdzonych po walidacji schematu (PSVI).</span><span class="sxs-lookup"><span data-stu-id="59de6-169">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="59de6-170">Aby uzyskać więcej informacji, zobacz [Jak sprawdzić przy użyciu XSD](./how-to-validate-using-xsd-linq-to-xml.md) i <xref:System.Xml.Schema.Extensions> .</span><span class="sxs-lookup"><span data-stu-id="59de6-170">For more information, see [How to validate using XSD](./how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="59de6-171">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="59de6-171">See also</span></span>

- [<span data-ttu-id="59de6-172">Wprowadzenie (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="59de6-172">Getting Started (LINQ to XML)</span></span>](./linq-to-xml-overview.md)
