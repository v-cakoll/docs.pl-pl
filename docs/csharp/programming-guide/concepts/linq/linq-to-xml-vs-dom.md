---
title: LINQ do XML vs. DOM (C#)
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 92d0da494829d57517d52fe93a3cbcf1398fdbe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168392"
---
# <a name="linq-to-xml-vs-dom-c"></a><span data-ttu-id="c9967-102">LINQ do XML vs. DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="c9967-102">LINQ to XML vs. DOM (C#)</span></span>
<span data-ttu-id="c9967-103">W tej sekcji opisano [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pewne kluczowe różnice między dominującym interfejsem API programowania XML, modelem obiektów dokumentu W3C (DOM).</span><span class="sxs-lookup"><span data-stu-id="c9967-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="c9967-104">Nowe sposoby konstruowania drzew XML</span><span class="sxs-lookup"><span data-stu-id="c9967-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="c9967-105">W w3C DOM, można utworzyć drzewo XML od dołu do góry; oznacza to, że tworzysz dokument, tworzysz elementy, a następnie dodajesz elementy do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c9967-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="c9967-106">Na przykład, w następujący sposób, aby utworzyć drzewo XML przy <xref:System.Xml.XmlDocument>użyciu implementacji microsoft dom, :</span><span class="sxs-lookup"><span data-stu-id="c9967-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="c9967-107">Ten styl kodowania nie dostarcza wizualnie wiele informacji na temat struktury drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="c9967-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c9967-108">obsługuje to podejście do konstruowania drzewa XML, ale obsługuje również alternatywne podejście, *funkcjonalną konstrukcję.*</span><span class="sxs-lookup"><span data-stu-id="c9967-108">supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="c9967-109">Funkcjonalna konstrukcja <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> używa i konstruktorów do tworzenia drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="c9967-109">Functional construction uses the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors to build an XML tree.</span></span>  
  
 <span data-ttu-id="c9967-110">Oto jak można skonstruować to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] samo drzewo XML przy użyciu konstrukcji funkcjonalnej:</span><span class="sxs-lookup"><span data-stu-id="c9967-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="c9967-111">Należy zauważyć, że wcięcie kodu do konstruowania drzewa XML pokazuje strukturę podstawowego xml.</span><span class="sxs-lookup"><span data-stu-id="c9967-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="c9967-112">Aby uzyskać więcej informacji, zobacz [Tworzenie drzew XML (C#)](./linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c9967-112">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="c9967-113">Praca bezpośrednio z elementami XML</span><span class="sxs-lookup"><span data-stu-id="c9967-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="c9967-114">Podczas programowania z XML, głównym celem jest zwykle na elementy XML i być może na atrybuty.</span><span class="sxs-lookup"><span data-stu-id="c9967-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="c9967-115">W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]programie można pracować bezpośrednio z elementami i atrybutami XML.</span><span class="sxs-lookup"><span data-stu-id="c9967-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="c9967-116">Na przykład można wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="c9967-116">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="c9967-117">Tworzenie elementów XML bez używania obiektu dokumentu w ogóle.</span><span class="sxs-lookup"><span data-stu-id="c9967-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="c9967-118">Upraszcza to programowanie, gdy trzeba pracować z fragmentami drzew XML.</span><span class="sxs-lookup"><span data-stu-id="c9967-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="c9967-119">Załaduj `T:System.Xml.Linq.XElement` obiekty bezpośrednio z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="c9967-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="c9967-120">Serializowanie `T:System.Xml.Linq.XElement` obiektów do pliku lub strumienia.</span><span class="sxs-lookup"><span data-stu-id="c9967-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="c9967-121">Porównaj to z w3C DOM, w którym dokument XML jest używany jako kontener logiczny dla drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="c9967-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="c9967-122">W dom, węzły XML, w tym elementy i atrybuty, muszą być tworzone w kontekście dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="c9967-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="c9967-123">Oto fragment kodu, aby utworzyć element nazwy w DOM:</span><span class="sxs-lookup"><span data-stu-id="c9967-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 <span data-ttu-id="c9967-124">Jeśli chcesz użyć elementu w wielu dokumentach, należy zaimportować węzły między dokumentami.</span><span class="sxs-lookup"><span data-stu-id="c9967-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c9967-125">unika tej warstwy złożoności.</span><span class="sxs-lookup"><span data-stu-id="c9967-125">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="c9967-126">Korzystając z LINQ do XML, należy użyć <xref:System.Xml.Linq.XDocument> klasy tylko wtedy, gdy chcesz dodać komentarz lub instrukcję przetwarzania na poziomie głównym dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c9967-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="c9967-127">Uproszczona obsługa nazw i przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="c9967-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="c9967-128">Obsługa nazw, przestrzeni nazw i prefiksów obszaru nazw jest zazwyczaj złożoną częścią programowania XML.</span><span class="sxs-lookup"><span data-stu-id="c9967-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c9967-129">upraszcza nazwy i przestrzenie nazw, eliminując wymóg zajmowania się prefiksami obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="c9967-129">simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="c9967-130">Jeśli chcesz kontrolować prefiksy obszaru nazw, możesz.</span><span class="sxs-lookup"><span data-stu-id="c9967-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="c9967-131">Jeśli jednak zdecydujesz się nie jawnie sterować [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] prefiksami obszaru nazw, przypisze prefiksy obszaru nazw podczas serializacji, jeśli są wymagane, lub serializuje przy użyciu domyślnych przestrzeni nazw, jeśli nie są.</span><span class="sxs-lookup"><span data-stu-id="c9967-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="c9967-132">Jeśli używane są domyślne przestrzenie nazw, w dokumencie wynikowym nie będzie żadnych prefiksów obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="c9967-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="c9967-133">Aby uzyskać więcej informacji, zobacz [Omówienie przestrzeni nazw (LINQ do XML) (C#)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="c9967-133">For more information, see [Namespaces Overview (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="c9967-134">Innym problemem z DOM jest to, że nie pozwala zmienić nazwę węzła.</span><span class="sxs-lookup"><span data-stu-id="c9967-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="c9967-135">Zamiast tego należy utworzyć nowy węzeł i skopiować wszystkie węzły podrzędne do niego, tracąc oryginalną tożsamość węzła.</span><span class="sxs-lookup"><span data-stu-id="c9967-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c9967-136">unika tego problemu, umożliwiając ustawienie <xref:System.Xml.Linq.XName> właściwości w węźle.</span><span class="sxs-lookup"><span data-stu-id="c9967-136">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="c9967-137">Obsługa metod statycznych dla ładowania XML</span><span class="sxs-lookup"><span data-stu-id="c9967-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c9967-138">umożliwia ładowanie języka XML przy użyciu metod statycznych zamiast metod instancji.</span><span class="sxs-lookup"><span data-stu-id="c9967-138">lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="c9967-139">Upraszcza to ładowanie i analizowanie.</span><span class="sxs-lookup"><span data-stu-id="c9967-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="c9967-140">Aby uzyskać więcej informacji, zobacz [Jak załadować xml z pliku (C#)](./how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="c9967-140">For more information, see [How to load XML from a file (C#)](./how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="c9967-141">Usuwanie wsparcia konstrukcji DTD</span><span class="sxs-lookup"><span data-stu-id="c9967-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c9967-142">dodatkowo upraszcza programowanie XML poprzez usunięcie obsługi jednostek i odniesień do jednostek.</span><span class="sxs-lookup"><span data-stu-id="c9967-142">further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="c9967-143">Zarządzanie jednostkami jest złożone i jest rzadko używane.</span><span class="sxs-lookup"><span data-stu-id="c9967-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="c9967-144">Usunięcie ich obsługi zwiększa wydajność i upraszcza interfejs programowania.</span><span class="sxs-lookup"><span data-stu-id="c9967-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="c9967-145">Gdy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] drzewo jest wypełniane, wszystkie jednostki DTD są rozwinięte.</span><span class="sxs-lookup"><span data-stu-id="c9967-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="c9967-146">Obsługa fragmentów</span><span class="sxs-lookup"><span data-stu-id="c9967-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c9967-147">nie zapewnia odpowiednika `XmlDocumentFragment` dla klasy.</span><span class="sxs-lookup"><span data-stu-id="c9967-147">does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="c9967-148">W wielu przypadkach jednak `XmlDocumentFragment` pojęcie może być obsługiwane przez wynik kwerendy, <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XNode>która <xref:System.Collections.Generic.IEnumerable%601> jest <xref:System.Xml.Linq.XElement>wpisana jako , lub .</span><span class="sxs-lookup"><span data-stu-id="c9967-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="c9967-149">Obsługa xpathnavigator</span><span class="sxs-lookup"><span data-stu-id="c9967-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c9967-150">zapewnia obsługę za <xref:System.Xml.XPath.XPathNavigator> pośrednictwem <xref:System.Xml.XPath?displayProperty=nameWithType> metod rozszerzenia w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c9967-150">provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c9967-151">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c9967-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="c9967-152">Obsługa odstępów i wcięć</span><span class="sxs-lookup"><span data-stu-id="c9967-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c9967-153">obsługuje biały znak w prostszy sposób niż DOM.</span><span class="sxs-lookup"><span data-stu-id="c9967-153">handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="c9967-154">Typowym scenariuszem jest odczyt wciętego kodu XML, utworzenie drzewa XML w pamięci bez żadnych węzłów tekstu odstępu (czyli nie zachowanie odstępu), wykonanie niektórych operacji w pliku XML, a następnie zapisanie kodu XML z wcięciem.</span><span class="sxs-lookup"><span data-stu-id="c9967-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="c9967-155">Podczas serializacji XML z formatowaniem zachowano tylko znaczące odstępy w drzewie XML.</span><span class="sxs-lookup"><span data-stu-id="c9967-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="c9967-156">Jest to domyślne [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zachowanie dla .</span><span class="sxs-lookup"><span data-stu-id="c9967-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="c9967-157">Innym typowym scenariuszem jest odczytywanie i modyfikowanie języka XML, który został już celowo wcięty.</span><span class="sxs-lookup"><span data-stu-id="c9967-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="c9967-158">W jakikolwiek sposób możesz nie chcieć zmienić tego wcięcia.</span><span class="sxs-lookup"><span data-stu-id="c9967-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="c9967-159">W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]przypadku , można to zrobić, zachowując biały znak podczas ładowania lub analizowania XML i wyłączania formatowania podczas serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="c9967-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c9967-160">przechowuje biały znak <xref:System.Xml.Linq.XText> jako węzeł, zamiast <xref:System.Xml.XmlNodeType.Whitespace> mieć typ węzła specjalistycznego, tak jak dom.</span><span class="sxs-lookup"><span data-stu-id="c9967-160">stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="c9967-161">Obsługa adnotacji</span><span class="sxs-lookup"><span data-stu-id="c9967-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c9967-162">elementy obsługują rozszerzalny zestaw adnotacji.</span><span class="sxs-lookup"><span data-stu-id="c9967-162">elements support an extensible set of annotations.</span></span> <span data-ttu-id="c9967-163">Jest to przydatne do śledzenia różnych informacji o elemencie, takich jak informacje o schemacie, informacje o tym, czy element jest powiązany z interfejsem użytkownika, czy też inny rodzaj informacji specyficznych dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c9967-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="c9967-164">Aby uzyskać więcej informacji, zobacz [LINQ do XML Adnotacje](./linq-to-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="c9967-164">For more information, see [LINQ to XML Annotations](./linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="c9967-165">Obsługa informacji o schemacie</span><span class="sxs-lookup"><span data-stu-id="c9967-165">Support for Schema Information</span></span>  
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c9967-166">zapewnia obsługę sprawdzania poprawności XSD <xref:System.Xml.Schema?displayProperty=nameWithType> za pomocą metod rozszerzenia w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c9967-166">provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="c9967-167">Można sprawdzić, czy drzewo XML jest zgodne z XSD.</span><span class="sxs-lookup"><span data-stu-id="c9967-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="c9967-168">Drzewo XML można wypełnić zestawem informacji po weryfikacji schematu (PSVI).</span><span class="sxs-lookup"><span data-stu-id="c9967-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="c9967-169">Aby uzyskać więcej informacji, zobacz Jak <xref:System.Xml.Schema.Extensions>sprawdzić [poprawność przy użyciu XSD](./how-to-validate-using-xsd-linq-to-xml.md) i .</span><span class="sxs-lookup"><span data-stu-id="c9967-169">For more information, see [How to validate using XSD](./how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c9967-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c9967-170">See also</span></span>

- [<span data-ttu-id="c9967-171">Wprowadzenie (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c9967-171">Getting Started (LINQ to XML)</span></span>](./linq-to-xml-overview.md)
