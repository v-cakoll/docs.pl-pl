---
title: Omówienie klas LINQ do klas XML (C#)
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 55be666fc0db0becb12ec8b525e7fc443536e1df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591885"
---
# <a name="linq-to-xml-classes-overview-c"></a><span data-ttu-id="04194-102">Omówienie klas LINQ do klas XML (C#)</span><span class="sxs-lookup"><span data-stu-id="04194-102">LINQ to XML Classes Overview (C#)</span></span>
<span data-ttu-id="04194-103">W tym temacie znajduje [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] się <xref:System.Xml.Linq> lista klas w obszarze nazw i krótki opis każdego z nich.</span><span class="sxs-lookup"><span data-stu-id="04194-103">This topic provides a list of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="04194-104">LINQ do klas XML</span><span class="sxs-lookup"><span data-stu-id="04194-104">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="04194-105">Klasa XAttribute</span><span class="sxs-lookup"><span data-stu-id="04194-105">XAttribute Class</span></span>  
 <span data-ttu-id="04194-106"><xref:System.Xml.Linq.XAttribute>reprezentuje atrybut XML.</span><span class="sxs-lookup"><span data-stu-id="04194-106"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="04194-107">Aby uzyskać szczegółowe informacje i przykłady, zobacz [Przegląd klasy XAttribute (C#)](./xattribute-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="04194-107">For detailed information and examples, see [XAttribute Class Overview (C#)](./xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="04194-108">Klasa XCData</span><span class="sxs-lookup"><span data-stu-id="04194-108">XCData Class</span></span>  
 <span data-ttu-id="04194-109"><xref:System.Xml.Linq.XCData>reprezentuje węzeł tekstowy CDATA.</span><span class="sxs-lookup"><span data-stu-id="04194-109"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="04194-110">Klasa XComment</span><span class="sxs-lookup"><span data-stu-id="04194-110">XComment Class</span></span>  
 <span data-ttu-id="04194-111"><xref:System.Xml.Linq.XComment>reprezentuje komentarz XML.</span><span class="sxs-lookup"><span data-stu-id="04194-111"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="04194-112">Klasa XContainer</span><span class="sxs-lookup"><span data-stu-id="04194-112">XContainer Class</span></span>  
 <span data-ttu-id="04194-113"><xref:System.Xml.Linq.XContainer>jest abstrakcyjną klasą podstawową dla wszystkich węzłów, które mogą mieć węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="04194-113"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="04194-114">Następujące klasy pochodzą od <xref:System.Xml.Linq.XContainer> klasy:</span><span class="sxs-lookup"><span data-stu-id="04194-114">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="04194-115">Klasa XDeclaration</span><span class="sxs-lookup"><span data-stu-id="04194-115">XDeclaration Class</span></span>  
 <span data-ttu-id="04194-116"><xref:System.Xml.Linq.XDeclaration>reprezentuje deklarację XML.</span><span class="sxs-lookup"><span data-stu-id="04194-116"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="04194-117">Deklaracja XML służy do deklarowania wersji XML i kodowania dokumentu.</span><span class="sxs-lookup"><span data-stu-id="04194-117">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="04194-118">Ponadto deklaracja XML określa, czy dokument XML jest autonomiczny.</span><span class="sxs-lookup"><span data-stu-id="04194-118">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="04194-119">Jeśli dokument jest autonomiczny, nie ma żadnych deklaracji zewnętrznych znaczników, w zewnętrznym DTD lub w jednostce parametru zewnętrznego, do której odwołuje się wewnętrzny podzbiór.</span><span class="sxs-lookup"><span data-stu-id="04194-119">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="04194-120">Klasa XDocument</span><span class="sxs-lookup"><span data-stu-id="04194-120">XDocument Class</span></span>  
 <span data-ttu-id="04194-121"><xref:System.Xml.Linq.XDocument>reprezentuje dokument XML.</span><span class="sxs-lookup"><span data-stu-id="04194-121"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="04194-122">Aby uzyskać szczegółowe informacje i przykłady, zobacz [Przegląd klasy XDocument (C#)](./xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="04194-122">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="04194-123">Klasa XDocumentType</span><span class="sxs-lookup"><span data-stu-id="04194-123">XDocumentType Class</span></span>  
 <span data-ttu-id="04194-124"><xref:System.Xml.Linq.XDocumentType>reprezentuje definicję typu dokumentu XML (DTD).</span><span class="sxs-lookup"><span data-stu-id="04194-124"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="04194-125">Klasa XElement</span><span class="sxs-lookup"><span data-stu-id="04194-125">XElement Class</span></span>  
 <span data-ttu-id="04194-126"><xref:System.Xml.Linq.XElement>reprezentuje element XML.</span><span class="sxs-lookup"><span data-stu-id="04194-126"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="04194-127">Aby uzyskać szczegółowe informacje i przykłady, zobacz [Przegląd klasy XElement (C#)](./xelement-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="04194-127">For detailed information and examples, see [XElement Class Overview (C#)](./xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="04194-128">Klasa XName</span><span class="sxs-lookup"><span data-stu-id="04194-128">XName Class</span></span>  
 <span data-ttu-id="04194-129"><xref:System.Xml.Linq.XName>reprezentuje nazwy elementów<xref:System.Xml.Linq.XElement>( ) i<xref:System.Xml.Linq.XAttribute>atrybutów ( ).</span><span class="sxs-lookup"><span data-stu-id="04194-129"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="04194-130">Aby uzyskać szczegółowe informacje i przykłady, zobacz [Przegląd klasy XDocument (C#)](./xdocument-class-overview.md).</span><span class="sxs-lookup"><span data-stu-id="04194-130">For detailed information and examples, see [XDocument Class Overview (C#)](./xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="04194-131">został zaprojektowany tak, aby nazwy XML były tak proste, jak to tylko możliwe.</span><span class="sxs-lookup"><span data-stu-id="04194-131">is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="04194-132">Ze względu na ich złożoność nazwy XML są często uważane za zaawansowany temat w XML.</span><span class="sxs-lookup"><span data-stu-id="04194-132">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="04194-133">Prawdopodobnie ta złożoność nie pochodzi z przestrzeni nazw, które deweloperzy używają regularnie w programowaniu, ale z prefiksów obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="04194-133">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="04194-134">Prefiksy obszaru nazw mogą być przydatne do zmniejszenia naciśnięć klawiszy wymaganych podczas wprowadzania kodu XML lub do ułatwienia odczytu języka XML.</span><span class="sxs-lookup"><span data-stu-id="04194-134">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="04194-135">Jednak prefiksy są często tylko skrót emitują pełny obszar nazw XML i nie są wymagane w większości przypadków.</span><span class="sxs-lookup"><span data-stu-id="04194-135">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="04194-136">upraszcza nazwy XML, rozwiązując wszystkie prefiksy do odpowiadającej im przestrzeni nazw XML.</span><span class="sxs-lookup"><span data-stu-id="04194-136">simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="04194-137">Prefiksy są dostępne, jeśli są <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> wymagane, za pośrednictwem metody.</span><span class="sxs-lookup"><span data-stu-id="04194-137">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="04194-138">W razie potrzeby można kontrolować prefiksy obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="04194-138">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="04194-139">W pewnych okolicznościach podczas pracy z innymi systemami XML, takimi jak XSLT lub XAML, należy sterować prefiksami obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="04194-139">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="04194-140">Na przykład jeśli masz wyrażenie XPath, które używa prefiksów obszaru nazw i jest osadzone w arkuszu stylów XSLT, należy upewnić się, że dokument XML jest seryjny z prefiksami obszaru nazw, które pasują do tych używanych w wyrażeniu XPath.</span><span class="sxs-lookup"><span data-stu-id="04194-140">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="04194-141">Klasa XNamespace</span><span class="sxs-lookup"><span data-stu-id="04194-141">XNamespace Class</span></span>  
 <span data-ttu-id="04194-142"><xref:System.Xml.Linq.XNamespace>reprezentuje obszar nazw dla <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute>lub .</span><span class="sxs-lookup"><span data-stu-id="04194-142"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="04194-143">Obszary nazw są składnikiem pliku <xref:System.Xml.Linq.XName>.</span><span class="sxs-lookup"><span data-stu-id="04194-143">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="04194-144">Klasa XNode</span><span class="sxs-lookup"><span data-stu-id="04194-144">XNode Class</span></span>  
 <span data-ttu-id="04194-145"><xref:System.Xml.Linq.XNode>jest klasą abstrakcyjną, która reprezentuje węzły drzewa XML.</span><span class="sxs-lookup"><span data-stu-id="04194-145"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="04194-146">Następujące klasy pochodzą od <xref:System.Xml.Linq.XNode> klasy:</span><span class="sxs-lookup"><span data-stu-id="04194-146">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="04194-147">Klasa XNodeDocumentOrderComparer</span><span class="sxs-lookup"><span data-stu-id="04194-147">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="04194-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer>udostępnia funkcje do porównywania węzłów dla ich zamówienia dokumentu.</span><span class="sxs-lookup"><span data-stu-id="04194-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="04194-149">Klasa XNodeEqualityComparer</span><span class="sxs-lookup"><span data-stu-id="04194-149">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="04194-150"><xref:System.Xml.Linq.XNodeEqualityComparer>udostępnia funkcje do porównywania węzłów dla równości wartości.</span><span class="sxs-lookup"><span data-stu-id="04194-150"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="04194-151">Klasa XObject</span><span class="sxs-lookup"><span data-stu-id="04194-151">XObject Class</span></span>  
 <span data-ttu-id="04194-152"><xref:System.Xml.Linq.XObject>jest abstrakcyjną klasą podstawową <xref:System.Xml.Linq.XNode> i <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="04194-152"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="04194-153">Zapewnia adnotacje i funkcje zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="04194-153">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="04194-154">Klasa XObjectChange</span><span class="sxs-lookup"><span data-stu-id="04194-154">XObjectChange Class</span></span>  
 <span data-ttu-id="04194-155"><xref:System.Xml.Linq.XObjectChange>określa typ zdarzenia, gdy zdarzenie jest <xref:System.Xml.Linq.XObject>wywoływane dla .</span><span class="sxs-lookup"><span data-stu-id="04194-155"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="04194-156">Klasa XObjectChangeEventArgs</span><span class="sxs-lookup"><span data-stu-id="04194-156">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="04194-157"><xref:System.Xml.Linq.XObjectChangeEventArgs>dostarcza danych <xref:System.Xml.Linq.XObject.Changing> dotyczących <xref:System.Xml.Linq.XObject.Changed> i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="04194-157"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="04194-158">XProcessingInstruction Klasa</span><span class="sxs-lookup"><span data-stu-id="04194-158">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="04194-159"><xref:System.Xml.Linq.XProcessingInstruction>reprezentuje instrukcję przetwarzania XML.</span><span class="sxs-lookup"><span data-stu-id="04194-159"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="04194-160">Instrukcja przetwarzania przekazuje informacje do aplikacji, która przetwarza XML.</span><span class="sxs-lookup"><span data-stu-id="04194-160">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="04194-161">Klasa XText</span><span class="sxs-lookup"><span data-stu-id="04194-161">XText Class</span></span>  
 <span data-ttu-id="04194-162"><xref:System.Xml.Linq.XText>reprezentuje węzeł tekstowy.</span><span class="sxs-lookup"><span data-stu-id="04194-162"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="04194-163">W większości przypadków nie trzeba używać tej klasy.</span><span class="sxs-lookup"><span data-stu-id="04194-163">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="04194-164">Ta klasa jest używana głównie dla zawartości mieszanej.</span><span class="sxs-lookup"><span data-stu-id="04194-164">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04194-165">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04194-165">See also</span></span>

- [<span data-ttu-id="04194-166">Omówienie programowania LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="04194-166">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)
