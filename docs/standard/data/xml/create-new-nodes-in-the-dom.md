---
title: Tworzenie nowych węzłów w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 390ffa1dd9f2e76372b0e4fcbf2916918b64d748
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44260100"
---
# <a name="create-new-nodes-in-the-dom"></a><span data-ttu-id="ba13d-102">Tworzenie nowych węzłów w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="ba13d-102">Create New Nodes in the DOM</span></span>
<span data-ttu-id="ba13d-103"><xref:System.Xml.XmlDocument> Ma metody create, dla wszystkich typów węzłów.</span><span class="sxs-lookup"><span data-stu-id="ba13d-103">The <xref:System.Xml.XmlDocument> has a create method for all of the node types.</span></span> <span data-ttu-id="ba13d-104">Podaj metody o nazwie, gdy jest to wymagane, a zawartość lub inne parametry te węzły, które mają zawartość (na przykład węzeł tekstowy) i węzeł jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="ba13d-104">Supply the method with a name when required, and content or other parameters for those nodes that have content (for example, a text node), and the node is created.</span></span> <span data-ttu-id="ba13d-105">Dostępne są następujące metody: te, które wymagają nazwy i kilka innych parametrów, wprowadzić, aby utworzyć odpowiedni węzeł.</span><span class="sxs-lookup"><span data-stu-id="ba13d-105">The following methods are ones that need a name and a few other parameters filled to create an appropriate node.</span></span>  
  
-   <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 <span data-ttu-id="ba13d-106">Inne typy węzłów mają wymagania więcej niż tylko dostarczanie danych do parametrów.</span><span class="sxs-lookup"><span data-stu-id="ba13d-106">Other node types have more requirements than just providing data to parameters.</span></span>  
  
 <span data-ttu-id="ba13d-107">Aby uzyskać informacji na temat atrybutów, zobacz [tworzenie nowych atrybutów dla elementów w modelu DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="ba13d-107">For information on attributes, see [Creating New Attributes for Elements in the DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span></span> <span data-ttu-id="ba13d-108">Aby uzyskać informacji na temat sprawdzania poprawności nazwy elementów i atrybutów, zobacz [— Element XML i weryfikacja nazwy atrybutu podczas tworzenia nowych węzłów](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="ba13d-108">For information on element and attribute name validation, see [XML Element and Attribute Name Verification when Creating New Nodes](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span></span> <span data-ttu-id="ba13d-109">W celu tworzenia odwołań do jednostek, zobacz [odwołania do tworzenia nowych jednostek](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span><span class="sxs-lookup"><span data-stu-id="ba13d-109">For creating entity references, see [Creating New Entity References](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span></span> <span data-ttu-id="ba13d-110">Aby uzyskać informacji na temat skutków rozszerzenie odwołań do jednostek w przestrzeni nazw, zobacz [Namespace wpływ na rozwijanie odwołań do jednostek dla nowych węzłów zawierających elementy i atrybuty](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="ba13d-110">For information on how namespaces affect the expansion of entity references, see [Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span></span>  
  
 <span data-ttu-id="ba13d-111">Po utworzeniu nowych węzłów, istnieje kilka różnych metod wstawić je do drzewa.</span><span class="sxs-lookup"><span data-stu-id="ba13d-111">Once new nodes are created, there are several methods available to insert them into the tree.</span></span> <span data-ttu-id="ba13d-112">W tabeli wymieniono metody, gdzie nowy węzeł jest widoczny w XML Document Object Model (DOM) opis.</span><span class="sxs-lookup"><span data-stu-id="ba13d-112">The table lists the methods with a description of where the new node appears in the XML Document Object Model (DOM).</span></span>  
  
|<span data-ttu-id="ba13d-113">Metoda</span><span class="sxs-lookup"><span data-stu-id="ba13d-113">Method</span></span>|<span data-ttu-id="ba13d-114">Położenie węzłów</span><span class="sxs-lookup"><span data-stu-id="ba13d-114">Node placement</span></span>|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|<span data-ttu-id="ba13d-115">Wstawione przed węzłem odniesienia.</span><span class="sxs-lookup"><span data-stu-id="ba13d-115">Inserted before the reference node.</span></span> <span data-ttu-id="ba13d-116">Na przykład, aby wstawić nowy węzeł w pozycji 5:</span><span class="sxs-lookup"><span data-stu-id="ba13d-116">For example, to insert the new node in position 5:</span></span><br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> <span data-ttu-id="ba13d-117">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.InsertBefore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ba13d-117">For more information, see the <xref:System.Xml.XmlNode.InsertBefore%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|<span data-ttu-id="ba13d-118">Wstawiona po węzła odniesienia.</span><span class="sxs-lookup"><span data-stu-id="ba13d-118">Inserted after the reference node.</span></span> <span data-ttu-id="ba13d-119">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ba13d-119">For example:</span></span><br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> <span data-ttu-id="ba13d-120">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.InsertAfter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ba13d-120">For more information, see the <xref:System.Xml.XmlNode.InsertAfter%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|<span data-ttu-id="ba13d-121">Dodaje węzeł do końca listy węzłów podrzędnych dla danego węzła.</span><span class="sxs-lookup"><span data-stu-id="ba13d-121">Adds the node to the end of the list of child nodes for the given node.</span></span> <span data-ttu-id="ba13d-122">Jeśli węzeł dodawany jest <xref:System.Xml.XmlDocumentFragment>, cała zawartość fragment dokumentu zostaną przeniesione do listy podrzędny tego węzła.</span><span class="sxs-lookup"><span data-stu-id="ba13d-122">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="ba13d-123">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.AppendChild%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ba13d-123">For more information, see the <xref:System.Xml.XmlNode.AppendChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|<span data-ttu-id="ba13d-124">Dodaje węzeł na początku listy węzłów podrzędnych danego węzła.</span><span class="sxs-lookup"><span data-stu-id="ba13d-124">Adds the node to the beginning of the list of child nodes of the given node.</span></span> <span data-ttu-id="ba13d-125">Jeśli węzeł dodawany jest <xref:System.Xml.XmlDocumentFragment>, cała zawartość fragment dokumentu zostaną przeniesione do listy podrzędny tego węzła.</span><span class="sxs-lookup"><span data-stu-id="ba13d-125">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="ba13d-126">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.PrependChild%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ba13d-126">For more information, see the <xref:System.Xml.XmlNode.PrependChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|<span data-ttu-id="ba13d-127">Dołącza <xref:System.Xml.XmlAttribute> węzła w końcu Kolekcja atrybutów skojarzona z elementem.</span><span class="sxs-lookup"><span data-stu-id="ba13d-127">Appends an <xref:System.Xml.XmlAttribute> node to the end of the attribute collection associated with an element.</span></span> <span data-ttu-id="ba13d-128">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlAttributeCollection.Append%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ba13d-128">For more information, see the <xref:System.Xml.XmlAttributeCollection.Append%2A> method.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba13d-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba13d-129">See also</span></span>

- [<span data-ttu-id="ba13d-130">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="ba13d-130">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
