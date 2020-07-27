---
title: Przegląd klas LINQ to XML (C#)
description: Ten artykuł zawiera podsumowanie klas LINQ to XML w języku C# w System.Xml. Przestrzeń nazw LINQ z krótkimi opisami każdego z nich.
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 34508f86792cdc7589569b8f12584ffc4379a5fb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165434"
---
# <a name="linq-to-xml-classes-overview-c"></a><span data-ttu-id="c9653-103">Przegląd klas LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c9653-103">LINQ to XML Classes Overview (C#)</span></span>
<span data-ttu-id="c9653-104">Ten temat zawiera listę [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] klas w <xref:System.Xml.Linq> przestrzeni nazw oraz Krótki opis każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="c9653-104">This topic provides a list of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="c9653-105">Klasy LINQ to XML</span><span class="sxs-lookup"><span data-stu-id="c9653-105">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="c9653-106">Klasa XAttribute</span><span class="sxs-lookup"><span data-stu-id="c9653-106">XAttribute Class</span></span>  
 <span data-ttu-id="c9653-107"><xref:System.Xml.Linq.XAttribute>reprezentuje atrybut XML.</span><span class="sxs-lookup"><span data-stu-id="c9653-107"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="c9653-108">Aby uzyskać szczegółowe informacje i przykłady, zobacz [XAttribute Class Overview (C#)](./xattribute-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c9653-108">For detailed information and examples, see [XAttribute Class Overview (C#)](./xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="c9653-109">Klasa XCData</span><span class="sxs-lookup"><span data-stu-id="c9653-109">XCData Class</span></span>  
 <span data-ttu-id="c9653-110"><xref:System.Xml.Linq.XCData>reprezentuje węzeł tekstu CDATA.</span><span class="sxs-lookup"><span data-stu-id="c9653-110"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="c9653-111">Klasa XComment</span><span class="sxs-lookup"><span data-stu-id="c9653-111">XComment Class</span></span>  
 <span data-ttu-id="c9653-112"><xref:System.Xml.Linq.XComment>Reprezentuje komentarz XML.</span><span class="sxs-lookup"><span data-stu-id="c9653-112"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="c9653-113">Klasa XContainer</span><span class="sxs-lookup"><span data-stu-id="c9653-113">XContainer Class</span></span>  
 <span data-ttu-id="c9653-114"><xref:System.Xml.Linq.XContainer>jest abstrakcyjną klasą bazową dla wszystkich węzłów, które mogą mieć węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="c9653-114"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="c9653-115">Następujące klasy pochodzą od <xref:System.Xml.Linq.XContainer> klasy:</span><span class="sxs-lookup"><span data-stu-id="c9653-115">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="c9653-116">Klasa XDeclaration</span><span class="sxs-lookup"><span data-stu-id="c9653-116">XDeclaration Class</span></span>  
 <span data-ttu-id="c9653-117"><xref:System.Xml.Linq.XDeclaration>reprezentuje deklarację XML.</span><span class="sxs-lookup"><span data-stu-id="c9653-117"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="c9653-118">Deklaracja XML jest używana do deklarowania wersji XML i kodowania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="c9653-118">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="c9653-119">Ponadto deklaracja XML określa, czy dokument XML jest autonomiczny.</span><span class="sxs-lookup"><span data-stu-id="c9653-119">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="c9653-120">Jeśli dokument jest autonomiczny, nie ma żadnych deklaracji znaczników zewnętrznych, w zewnętrznym DTD lub w jednostce parametru zewnętrznego, do której odwołuje się podzbiór wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="c9653-120">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="c9653-121">Klasa XDocument</span><span class="sxs-lookup"><span data-stu-id="c9653-121">XDocument Class</span></span>  
 <span data-ttu-id="c9653-122"><xref:System.Xml.Linq.XDocument>reprezentuje dokument XML.</span><span class="sxs-lookup"><span data-stu-id="c9653-122"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="c9653-123">Aby uzyskać szczegółowe informacje i przykłady, zobacz [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c9653-123">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="c9653-124">XDocumenttype — Klasa</span><span class="sxs-lookup"><span data-stu-id="c9653-124">XDocumentType Class</span></span>  
 <span data-ttu-id="c9653-125"><xref:System.Xml.Linq.XDocumentType>reprezentuje definicję typu dokumentu XML (DTD).</span><span class="sxs-lookup"><span data-stu-id="c9653-125"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="c9653-126">Klasa XElement</span><span class="sxs-lookup"><span data-stu-id="c9653-126">XElement Class</span></span>  
 <span data-ttu-id="c9653-127"><xref:System.Xml.Linq.XElement>reprezentuje element XML.</span><span class="sxs-lookup"><span data-stu-id="c9653-127"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="c9653-128">Aby uzyskać szczegółowe informacje i przykłady, zobacz [XElement Class Overview (C#)](./xelement-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c9653-128">For detailed information and examples, see [XElement Class Overview (C#)](./xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="c9653-129">Klasa XName</span><span class="sxs-lookup"><span data-stu-id="c9653-129">XName Class</span></span>  
 <span data-ttu-id="c9653-130"><xref:System.Xml.Linq.XName>reprezentuje nazwy elementów ( <xref:System.Xml.Linq.XElement> ) i atrybutów ( <xref:System.Xml.Linq.XAttribute> ).</span><span class="sxs-lookup"><span data-stu-id="c9653-130"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="c9653-131">Aby uzyskać szczegółowe informacje i przykłady, zobacz [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c9653-131">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c9653-132">został zaprojektowany tak, aby nazwy XML były tak proste, jak to możliwe.</span><span class="sxs-lookup"><span data-stu-id="c9653-132">is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="c9653-133">Ze względu na złożoność nazwy XML często są uważane za zaawansowaną temat w języku XML.</span><span class="sxs-lookup"><span data-stu-id="c9653-133">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="c9653-134">Raczej, ta złożoność nie pochodzi z przestrzeni nazw, które deweloperzy wykorzystują regularnie w programowaniu, ale z prefiksów przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c9653-134">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="c9653-135">Prefiksy przestrzeni nazw mogą być przydatne, aby zmniejszyć liczbę naciśnięć klawiszy wymaganych podczas wprowadzania danych XML lub ułatwić odczytywanie kodu XML.</span><span class="sxs-lookup"><span data-stu-id="c9653-135">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="c9653-136">Jednak prefiksy są często tylko skrótem do używania pełnej przestrzeni nazw XML i nie są wymagane w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="c9653-136">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="c9653-137">upraszcza nazwy XML, rozwiązując wszystkie prefiksy do odpowiednich nazw XML.</span><span class="sxs-lookup"><span data-stu-id="c9653-137">simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="c9653-138">Prefiksy są dostępne, jeśli są wymagane przez <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="c9653-138">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="c9653-139">W razie potrzeby można kontrolować prefiksy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c9653-139">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="c9653-140">W niektórych sytuacjach, jeśli pracujesz z innymi systemami XML, takimi jak XSLT lub XAML, musisz kontrolować prefiksy przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c9653-140">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="c9653-141">Na przykład jeśli masz wyrażenie XPath używające prefiksów przestrzeni nazw i osadzone w arkuszu stylów XSLT, musisz upewnić się, że dokument XML jest serializowany z prefiksami przestrzeni nazw, które pasują do tych używanych w wyrażeniu XPath.</span><span class="sxs-lookup"><span data-stu-id="c9653-141">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="c9653-142">Klasa XNamespace</span><span class="sxs-lookup"><span data-stu-id="c9653-142">XNamespace Class</span></span>  
 <span data-ttu-id="c9653-143"><xref:System.Xml.Linq.XNamespace>reprezentuje przestrzeń nazw dla <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="c9653-143"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="c9653-144">Przestrzenie nazw są składnikiem <xref:System.Xml.Linq.XName> .</span><span class="sxs-lookup"><span data-stu-id="c9653-144">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="c9653-145">Klasa XNode</span><span class="sxs-lookup"><span data-stu-id="c9653-145">XNode Class</span></span>  
 <span data-ttu-id="c9653-146"><xref:System.Xml.Linq.XNode>jest klasą abstrakcyjną, która reprezentuje węzły drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="c9653-146"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="c9653-147">Następujące klasy pochodzą od <xref:System.Xml.Linq.XNode> klasy:</span><span class="sxs-lookup"><span data-stu-id="c9653-147">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="c9653-148">Klasa XNodeDocumentOrderComparer</span><span class="sxs-lookup"><span data-stu-id="c9653-148">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="c9653-149"><xref:System.Xml.Linq.XNodeDocumentOrderComparer>oferuje funkcje do porównywania węzłów dla ich kolejności dokumentów.</span><span class="sxs-lookup"><span data-stu-id="c9653-149"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="c9653-150">Klasa XNodeEqualityComparer</span><span class="sxs-lookup"><span data-stu-id="c9653-150">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="c9653-151"><xref:System.Xml.Linq.XNodeEqualityComparer>oferuje funkcje do porównywania węzłów pod kątem równości wartości.</span><span class="sxs-lookup"><span data-stu-id="c9653-151"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="c9653-152">Klasa XObject</span><span class="sxs-lookup"><span data-stu-id="c9653-152">XObject Class</span></span>  
 <span data-ttu-id="c9653-153"><xref:System.Xml.Linq.XObject>jest abstrakcyjną klasą bazową <xref:System.Xml.Linq.XNode> i <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="c9653-153"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="c9653-154">Zapewnia funkcję adnotacji i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c9653-154">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="c9653-155">Klasa XObjectChange</span><span class="sxs-lookup"><span data-stu-id="c9653-155">XObjectChange Class</span></span>  
 <span data-ttu-id="c9653-156"><xref:System.Xml.Linq.XObjectChange>Określa typ zdarzenia, gdy zdarzenie jest zgłaszane dla elementu <xref:System.Xml.Linq.XObject> .</span><span class="sxs-lookup"><span data-stu-id="c9653-156"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="c9653-157">Klasa XObjectChangeEventArgs</span><span class="sxs-lookup"><span data-stu-id="c9653-157">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="c9653-158"><xref:System.Xml.Linq.XObjectChangeEventArgs>dostarcza dane dla <xref:System.Xml.Linq.XObject.Changing> zdarzeń i <xref:System.Xml.Linq.XObject.Changed> .</span><span class="sxs-lookup"><span data-stu-id="c9653-158"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="c9653-159">Klasa XProcessingInstruction</span><span class="sxs-lookup"><span data-stu-id="c9653-159">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="c9653-160"><xref:System.Xml.Linq.XProcessingInstruction>reprezentuje instrukcję przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="c9653-160"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="c9653-161">Instrukcja przetwarzania komunikuje informacje z aplikacją, która przetwarza kod XML.</span><span class="sxs-lookup"><span data-stu-id="c9653-161">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="c9653-162">Klasa XText</span><span class="sxs-lookup"><span data-stu-id="c9653-162">XText Class</span></span>  
 <span data-ttu-id="c9653-163"><xref:System.Xml.Linq.XText>reprezentuje węzeł tekstowy.</span><span class="sxs-lookup"><span data-stu-id="c9653-163"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="c9653-164">W większości przypadków nie trzeba używać tej klasy.</span><span class="sxs-lookup"><span data-stu-id="c9653-164">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="c9653-165">Ta klasa jest używana głównie do zawartości mieszanej.</span><span class="sxs-lookup"><span data-stu-id="c9653-165">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9653-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9653-166">See also</span></span>

- [<span data-ttu-id="c9653-167">Omówienie programowania LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="c9653-167">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
