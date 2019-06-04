---
title: LINQ to XML a MODELU DOM (C#)
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 3cd6edf9e950611d4e0ed205b89c7c7b073955c8
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66484320"
---
# <a name="linq-to-xml-vs-dom-c"></a><span data-ttu-id="f4acd-102">LINQ to XML a MODELU DOM (C#)</span><span class="sxs-lookup"><span data-stu-id="f4acd-102">LINQ to XML vs. DOM (C#)</span></span>
<span data-ttu-id="f4acd-103">W tej sekcji opisano niektóre podstawowe różnice między [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] i bieżącej dominujący XML programowania interfejsu API, W3C Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="f4acd-103">This section describes some key differences between [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] and the current predominant XML programming API, the W3C Document Object Model (DOM).</span></span>  
  
## <a name="new-ways-to-construct-xml-trees"></a><span data-ttu-id="f4acd-104">Nowe sposoby tworzenia drzew XML</span><span class="sxs-lookup"><span data-stu-id="f4acd-104">New Ways to Construct XML Trees</span></span>  
 <span data-ttu-id="f4acd-105">W modelu DOM W3C tworzysz drzewa XML z dołu. oznacza to Utwórz dokument, tworzyć elementy, a następnie dodać elementy do dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f4acd-105">In the W3C DOM, you build an XML tree from the bottom up; that is, you create a document, you create elements, and then you add the elements to the document.</span></span>  
  
 <span data-ttu-id="f4acd-106">Na przykład, następujące byłoby typowym sposobem tworzenia drzewa XML przy użyciu implementacja firmy Microsoft w modelu DOM, <xref:System.Xml.XmlDocument>:</span><span class="sxs-lookup"><span data-stu-id="f4acd-106">For example, the following would be a typical way to create an XML tree using the Microsoft implementation of DOM, <xref:System.Xml.XmlDocument>:</span></span>  
  
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
  
 <span data-ttu-id="f4acd-107">Ten styl kodowania nie zapewnia wizualne dużej ilości informacji na temat struktury drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="f4acd-107">This style of coding does not visually provide much information about the structure of the XML tree.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="f4acd-108">obsługuje takie podejście do Konstruowanie drzewa XML, ale obsługuje także alternatywne podejście, *konstrukcja funkcjonalna*.</span><span class="sxs-lookup"><span data-stu-id="f4acd-108">supports this approach to constructing an XML tree, but also supports an alternative approach, *functional construction*.</span></span> <span data-ttu-id="f4acd-109">Konstrukcja funkcjonalna używa <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> konstruktorów do tworzenia drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="f4acd-109">Functional construction uses the <xref:System.Xml.Linq.XElement> and <xref:System.Xml.Linq.XAttribute> constructors to build an XML tree.</span></span>  
  
 <span data-ttu-id="f4acd-110">Oto jak będzie konstruowania tych samych drzewa XML przy użyciu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] konstrukcja funkcjonalna:</span><span class="sxs-lookup"><span data-stu-id="f4acd-110">Here is how you would construct the same XML tree by using [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] functional construction:</span></span>  
  
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
  
 <span data-ttu-id="f4acd-111">Należy zauważyć, że wcięć w kodzie do konstruowania drzewa XML pokazuje strukturę elementu bazowego XML.</span><span class="sxs-lookup"><span data-stu-id="f4acd-111">Notice that indenting the code to construct the XML tree shows the structure of the underlying XML.</span></span>  
  
 <span data-ttu-id="f4acd-112">Aby uzyskać więcej informacji, zobacz [tworzenie drzew XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f4acd-112">For more information, see [Creating XML Trees (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md).</span></span>  
  
## <a name="working-directly-with-xml-elements"></a><span data-ttu-id="f4acd-113">Praca bezpośrednio z elementów XML</span><span class="sxs-lookup"><span data-stu-id="f4acd-113">Working Directly with XML Elements</span></span>  
 <span data-ttu-id="f4acd-114">Gdy program za pomocą XML zespół podstawowego jest zazwyczaj na elementy XML, a być może w atrybutach.</span><span class="sxs-lookup"><span data-stu-id="f4acd-114">When you program with XML, your primary focus is usually on XML elements and perhaps on attributes.</span></span> <span data-ttu-id="f4acd-115">W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można pracować bezpośrednio z elementów XML oraz atrybuty.</span><span class="sxs-lookup"><span data-stu-id="f4acd-115">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can work directly with XML elements and attributes.</span></span> <span data-ttu-id="f4acd-116">Można na przykład, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="f4acd-116">For example, you can do the following:</span></span>  
  
- <span data-ttu-id="f4acd-117">Tworzenie elementów XML bez przy użyciu obiektu dokumentu w ogóle.</span><span class="sxs-lookup"><span data-stu-id="f4acd-117">Create XML elements without using a document object at all.</span></span> <span data-ttu-id="f4acd-118">Upraszcza to programowania, gdy trzeba pracować przy użyciu fragmentów drzew XML.</span><span class="sxs-lookup"><span data-stu-id="f4acd-118">This simplifies programming when you have to work with fragments of XML trees.</span></span>  
  
- <span data-ttu-id="f4acd-119">Obciążenia `T:System.Xml.Linq.XElement` obiektów bezpośrednio z pliku XML.</span><span class="sxs-lookup"><span data-stu-id="f4acd-119">Load `T:System.Xml.Linq.XElement` objects directly from an XML file.</span></span>  
  
- <span data-ttu-id="f4acd-120">Serializowanie `T:System.Xml.Linq.XElement` obiektów do pliku lub strumienia.</span><span class="sxs-lookup"><span data-stu-id="f4acd-120">Serialize `T:System.Xml.Linq.XElement` objects to a file or a stream.</span></span>  
  
 <span data-ttu-id="f4acd-121">To porównać do modelu DOM W3C, w którym dokument XML jest używany jako kontener logiczny dla drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="f4acd-121">Compare this to the W3C DOM, in which the XML document is used as a logical container for the XML tree.</span></span> <span data-ttu-id="f4acd-122">W modelu DOM węzłów XML, w tym elementów i atrybutów, należy utworzyć w kontekście dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="f4acd-122">In DOM, XML nodes, including elements and attributes, must be created in the context of an XML document.</span></span> <span data-ttu-id="f4acd-123">Poniżej przedstawiono fragment kodu, aby utworzyć element nazwy w modelu DOM:</span><span class="sxs-lookup"><span data-stu-id="f4acd-123">Here is a fragment of the code to create a name element in DOM:</span></span>  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 <span data-ttu-id="f4acd-124">Jeśli chcesz użyć elementu na wiele dokumentów, należy zaimportować węzłów, wszystkich dokumentów.</span><span class="sxs-lookup"><span data-stu-id="f4acd-124">If you want to use an element across multiple documents, you must import the nodes across documents.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="f4acd-125">pozwala uniknąć złożoności tej warstwy.</span><span class="sxs-lookup"><span data-stu-id="f4acd-125">avoids this layer of complexity.</span></span>  
  
 <span data-ttu-id="f4acd-126">Podczas korzystania z LINQ to XML, należy użyć <xref:System.Xml.Linq.XDocument> klasy tylko wtedy, gdy chcesz dodać instrukcję przetwarzania lub komentarz na poziomie głównym dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f4acd-126">When using LINQ to XML, you use the <xref:System.Xml.Linq.XDocument> class only if you want to add a comment or processing instruction at the root level of the document.</span></span>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a><span data-ttu-id="f4acd-127">Uproszczona obsługa nazw i przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="f4acd-127">Simplified Handling of Names and Namespaces</span></span>  
 <span data-ttu-id="f4acd-128">Obsługa nazw, przestrzenie nazw i prefiksy przestrzeni nazw jest zazwyczaj złożonych częścią programowania XML.</span><span class="sxs-lookup"><span data-stu-id="f4acd-128">Handling names, namespaces, and namespace prefixes is generally a complex part of XML programming.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="f4acd-129">upraszcza nazw i przestrzeni nazw pozwala pozbyć się konieczności radzenia sobie z prefiksy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f4acd-129">simplifies names and namespaces by eliminating the requirement to deal with namespace prefixes.</span></span> <span data-ttu-id="f4acd-130">Jeśli chcesz kontrolować prefiksy przestrzeni nazw, możesz.</span><span class="sxs-lookup"><span data-stu-id="f4acd-130">If you want to control namespace prefixes, you can.</span></span> <span data-ttu-id="f4acd-131">Jeśli zdecydujesz się nie zostały jawnie kontrolowanie prefiksów przestrzeni nazw, jednak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] spowoduje przypisanie prefiksy przestrzeni nazw podczas serializacji, jeśli wymagane są lub będą serializacji przy użyciu domyślnych przestrzeni nazw, jeśli nie są one.</span><span class="sxs-lookup"><span data-stu-id="f4acd-131">But if you decide to not explicitly control namespace prefixes, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] will assign namespace prefixes during serialization if they are required, or will serialize using default namespaces if they are not.</span></span> <span data-ttu-id="f4acd-132">Jeśli używane są domyślne obszary nazw, nie będzie żadnych prefiksów przestrzeni nazw w utworzonego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="f4acd-132">If default namespaces are used, there will be no namespace prefixes in the resulting document.</span></span> <span data-ttu-id="f4acd-133">Aby uzyskać więcej informacji, zobacz [Praca z przestrzeniami nazw XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="f4acd-133">For more information, see [Working with XML Namespaces (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="f4acd-134">Inny problem z modelu DOM jest, że nie zezwala Ci zmienić nazwę węzła.</span><span class="sxs-lookup"><span data-stu-id="f4acd-134">Another problem with the DOM is that it does not let you change the name of a node.</span></span> <span data-ttu-id="f4acd-135">Zamiast tego należy utworzyć nowy węzeł i skopiuj wszystkie węzły podrzędne, utraty oryginalną tożsamość węzła.</span><span class="sxs-lookup"><span data-stu-id="f4acd-135">Instead, you have to create a new node and copy all the child nodes to it, losing the original node identity.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="f4acd-136">pozwala uniknąć tego problemu, należy włączyć ustawienia <xref:System.Xml.Linq.XName> właściwość w węźle.</span><span class="sxs-lookup"><span data-stu-id="f4acd-136">avoids this problem by enabling you to set the <xref:System.Xml.Linq.XName> property on a node.</span></span>  
  
## <a name="static-method-support-for-loading-xml"></a><span data-ttu-id="f4acd-137">Obsługa statycznej metody ładowania danych XML</span><span class="sxs-lookup"><span data-stu-id="f4acd-137">Static Method Support for Loading XML</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="f4acd-138">Umożliwia ładowanie kodu XML przy użyciu metody statyczne, zamiast metody wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f4acd-138">lets you load XML by using static methods, instead of instance methods.</span></span> <span data-ttu-id="f4acd-139">Upraszcza to ładowania i analizowania.</span><span class="sxs-lookup"><span data-stu-id="f4acd-139">This simplifies loading and parsing.</span></span> <span data-ttu-id="f4acd-140">Aby uzyskać więcej informacji, zobacz [jak: Ładowanie kodu XML z pliku (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span><span class="sxs-lookup"><span data-stu-id="f4acd-140">For more information, see [How to: Load XML from a File (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).</span></span>  
  
## <a name="removal-of-support-for-dtd-constructs"></a><span data-ttu-id="f4acd-141">Usunięcie obsługi konstrukcji DTD</span><span class="sxs-lookup"><span data-stu-id="f4acd-141">Removal of Support for DTD Constructs</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="f4acd-142">dodatkowo upraszcza programowanie, usuwając obsługę jednostek i odwołań do jednostek XML.</span><span class="sxs-lookup"><span data-stu-id="f4acd-142">further simplifies XML programming by removing support for entities and entity references.</span></span> <span data-ttu-id="f4acd-143">Zarządzanie jednostkami jest złożona i jest rzadko używana.</span><span class="sxs-lookup"><span data-stu-id="f4acd-143">The management of entities is complex, and is rarely used.</span></span> <span data-ttu-id="f4acd-144">Usuwanie ich obsługi zwiększa wydajność i upraszcza interfejs programowania.</span><span class="sxs-lookup"><span data-stu-id="f4acd-144">Removing their support increases performance and simplifies the programming interface.</span></span> <span data-ttu-id="f4acd-145">Gdy [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] drzewa jest wypełniana, zostaną rozwinięte wszystkie jednostki DTD.</span><span class="sxs-lookup"><span data-stu-id="f4acd-145">When a [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tree is populated, all DTD entities are expanded.</span></span>  
  
## <a name="support-for-fragments"></a><span data-ttu-id="f4acd-146">Obsługa fragmentów</span><span class="sxs-lookup"><span data-stu-id="f4acd-146">Support for Fragments</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="f4acd-147">nie zapewnia odpowiedniego dla `XmlDocumentFragment` klasy.</span><span class="sxs-lookup"><span data-stu-id="f4acd-147">does not provide an equivalent for the `XmlDocumentFragment` class.</span></span> <span data-ttu-id="f4acd-148">W wielu przypadkach jednak `XmlDocumentFragment` pojęcia mogą być obsługiwane w wyniku zapytania, które jest <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XNode>, lub <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="f4acd-148">In many cases, however, the `XmlDocumentFragment` concept can be handled by the result of a query that is typed as <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XNode>, or <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="support-for-xpathnavigator"></a><span data-ttu-id="f4acd-149">Obsługa klasy XPathNavigator</span><span class="sxs-lookup"><span data-stu-id="f4acd-149">Support for XPathNavigator</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="f4acd-150">zapewnia obsługę <xref:System.Xml.XPath.XPathNavigator> za pośrednictwem metody rozszerzające w <xref:System.Xml.XPath?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f4acd-150">provides support for <xref:System.Xml.XPath.XPathNavigator> through extension methods in the <xref:System.Xml.XPath?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f4acd-151">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f4acd-151">For more information, see <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.</span></span>  
  
## <a name="support-for-white-space-and-indentation"></a><span data-ttu-id="f4acd-152">Obsługa białych znaków i wcięć</span><span class="sxs-lookup"><span data-stu-id="f4acd-152">Support for White Space and Indentation</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="f4acd-153">obsługuje biały znak, co jest prostsze niż DOM.</span><span class="sxs-lookup"><span data-stu-id="f4acd-153">handles white space more simply than the DOM.</span></span>  
  
 <span data-ttu-id="f4acd-154">Typowym scenariuszem jest Odczytaj dane XML z wcięciami, utworzyć drzewa XML w pamięci bez wszystkie węzły tekstowe białe miejsca (to znaczy nie zachowania biały), wykonywanie operacji na pliku XML, a następnie zapisz plik XML, z wcięciem.</span><span class="sxs-lookup"><span data-stu-id="f4acd-154">A common scenario is to read indented XML, create an in-memory XML tree without any white space text nodes (that is, not preserving white space), perform some operations on the XML, and then save the XML with indentation.</span></span> <span data-ttu-id="f4acd-155">Po użytkownik serializacji XML za pomocą formatowania, tylko istotne biały znak w drzewie XML są zachowywane.</span><span class="sxs-lookup"><span data-stu-id="f4acd-155">When you serialize the XML with formatting, only significant white space in the XML tree is preserved.</span></span> <span data-ttu-id="f4acd-156">Jest to domyślne zachowanie dla [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f4acd-156">This is the default behavior for [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span>  
  
 <span data-ttu-id="f4acd-157">Inny typowy scenariusz polega na odczytywanie i modyfikację XML, który już został celowo z wcięciami.</span><span class="sxs-lookup"><span data-stu-id="f4acd-157">Another common scenario is to read and modify XML that has already been intentionally indented.</span></span> <span data-ttu-id="f4acd-158">Nie można zmienić to wcięcie w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="f4acd-158">You might not want to change this indentation in any way.</span></span> <span data-ttu-id="f4acd-159">W [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można to zrobić przez zachowywanie białych znaków podczas ładowania lub nemohla analyzovat kód XML i wyłączanie formatowania podczas serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="f4acd-159">In [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can do this by preserving white space when you load or parse the XML and disabling formatting when you serialize the XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="f4acd-160">przechowuje biały znak jako <xref:System.Xml.Linq.XText> węzła zamiast wyspecjalizowanego <xref:System.Xml.XmlNodeType.Whitespace> typ węzła jako modelu DOM wykonuje.</span><span class="sxs-lookup"><span data-stu-id="f4acd-160">stores white space as an <xref:System.Xml.Linq.XText> node, instead of having a specialized <xref:System.Xml.XmlNodeType.Whitespace> node type, as the DOM does.</span></span>  
  
## <a name="support-for-annotations"></a><span data-ttu-id="f4acd-161">Obsługa adnotacji</span><span class="sxs-lookup"><span data-stu-id="f4acd-161">Support for Annotations</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="f4acd-162">elementy obsługuje extensible zbiór adnotacji.</span><span class="sxs-lookup"><span data-stu-id="f4acd-162">elements support an extensible set of annotations.</span></span> <span data-ttu-id="f4acd-163">Jest to przydatne do śledzenia dodatkowych informacji na temat elementu, np. informacji o schemacie, informacji na temat tego, czy element jest powiązany z interfejsu użytkownika lub inne informacje dotyczące rodzaju specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f4acd-163">This is useful for tracking miscellaneous information about an element, such as schema information, information about whether the element is bound to a UI, or any other kind of application-specific information.</span></span> <span data-ttu-id="f4acd-164">Aby uzyskać więcej informacji, zobacz [adnotacje LINQ to XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-annotations.md).</span><span class="sxs-lookup"><span data-stu-id="f4acd-164">For more information, see [LINQ to XML Annotations](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-annotations.md).</span></span>  
  
## <a name="support-for-schema-information"></a><span data-ttu-id="f4acd-165">Obsługa informacji o schemacie</span><span class="sxs-lookup"><span data-stu-id="f4acd-165">Support for Schema Information</span></span>  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="f4acd-166">zapewnia obsługę walidację XSD za pośrednictwem metody rozszerzające w <xref:System.Xml.Schema?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f4acd-166">provides support for XSD validation through extension methods in the <xref:System.Xml.Schema?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="f4acd-167">Aby zweryfikować, że drzewa XML jest zgodny z XSD.</span><span class="sxs-lookup"><span data-stu-id="f4acd-167">You can validate that an XML tree complies with an XSD.</span></span> <span data-ttu-id="f4acd-168">Możesz wypełnić drzewa XML z zestaw informacji po weryfikacji (PSVI).</span><span class="sxs-lookup"><span data-stu-id="f4acd-168">You can populate the XML tree with the post-schema-validation infoset (PSVI).</span></span> <span data-ttu-id="f4acd-169">Aby uzyskać więcej informacji, zobacz [jak: Weryfikowanie przy użyciu XSD](../../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) i <xref:System.Xml.Schema.Extensions>.</span><span class="sxs-lookup"><span data-stu-id="f4acd-169">For more information, see [How to: Validate Using XSD](../../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) and <xref:System.Xml.Schema.Extensions>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4acd-170">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f4acd-170">See also</span></span>

- [<span data-ttu-id="f4acd-171">Wprowadzenie (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="f4acd-171">Getting Started (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md)
