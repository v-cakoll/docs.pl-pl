---
title: Tworzenie nowych węzłów w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
ms.openlocfilehash: f48990286405baee347becef87d0511cd42e9e77
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711002"
---
# <a name="create-new-nodes-in-the-dom"></a><span data-ttu-id="1c35c-102">Tworzenie nowych węzłów w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="1c35c-102">Create New Nodes in the DOM</span></span>
<span data-ttu-id="1c35c-103"><xref:System.Xml.XmlDocument> Ma metodę Create dla wszystkich typów węzłów.</span><span class="sxs-lookup"><span data-stu-id="1c35c-103">The <xref:System.Xml.XmlDocument> has a create method for all of the node types.</span></span> <span data-ttu-id="1c35c-104">Podaj metodę o nazwie, gdy jest to wymagane, oraz zawartość lub inne parametry dla tych węzłów, które mają zawartość (na przykład węzeł tekstowy) i węzeł jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="1c35c-104">Supply the method with a name when required, and content or other parameters for those nodes that have content (for example, a text node), and the node is created.</span></span> <span data-ttu-id="1c35c-105">Poniższe metody to te, które wymagają nazwy i kilku innych parametrów wypełnionych w celu utworzenia odpowiedniego węzła.</span><span class="sxs-lookup"><span data-stu-id="1c35c-105">The following methods are ones that need a name and a few other parameters filled to create an appropriate node.</span></span>  
  
- <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
- <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
- <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
- <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
- <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
- <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
- <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
- <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
- <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
- <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
- <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 <span data-ttu-id="1c35c-106">Inne typy węzłów mają więcej wymagań niż tylko dostarczanie danych do parametrów.</span><span class="sxs-lookup"><span data-stu-id="1c35c-106">Other node types have more requirements than just providing data to parameters.</span></span>  
  
 <span data-ttu-id="1c35c-107">Aby uzyskać informacje na temat atrybutów, zobacz [Tworzenie nowych atrybutów dla elementów w modelu dom](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="1c35c-107">For information on attributes, see [Creating New Attributes for Elements in the DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span></span> <span data-ttu-id="1c35c-108">Aby uzyskać informacje na temat walidacji nazw elementów i atrybutów, zobacz [Weryfikacja nazwy elementu i atrybutu XML podczas tworzenia nowych węzłów](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="1c35c-108">For information on element and attribute name validation, see [XML Element and Attribute Name Verification when Creating New Nodes](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span></span> <span data-ttu-id="1c35c-109">Aby uzyskać informacje na temat tworzenia odwołań do jednostek, zobacz [Tworzenie nowych odwołań do jednostek](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span><span class="sxs-lookup"><span data-stu-id="1c35c-109">For creating entity references, see [Creating New Entity References](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span></span> <span data-ttu-id="1c35c-110">Aby uzyskać informacje na temat sposobu, w jaki przestrzenie nazw wpływają na rozszerzanie odwołań do jednostek, zobacz [przestrzeń nazw ma wpływ na rozszerzanie odwołania do jednostek dla nowych węzłów zawierających elementy i atrybuty](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="1c35c-110">For information on how namespaces affect the expansion of entity references, see [Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span></span>  
  
 <span data-ttu-id="1c35c-111">Po utworzeniu nowych węzłów dostępne są kilka metod wstawienia ich do drzewa.</span><span class="sxs-lookup"><span data-stu-id="1c35c-111">Once new nodes are created, there are several methods available to insert them into the tree.</span></span> <span data-ttu-id="1c35c-112">W tabeli wymieniono metody z opisem, gdzie nowy węzeł pojawia się w Document Object Model XML (DOM).</span><span class="sxs-lookup"><span data-stu-id="1c35c-112">The table lists the methods with a description of where the new node appears in the XML Document Object Model (DOM).</span></span>  
  
|<span data-ttu-id="1c35c-113">Metoda</span><span class="sxs-lookup"><span data-stu-id="1c35c-113">Method</span></span>|<span data-ttu-id="1c35c-114">Położenie węzła</span><span class="sxs-lookup"><span data-stu-id="1c35c-114">Node placement</span></span>|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|<span data-ttu-id="1c35c-115">Wstawiono przed węzłem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="1c35c-115">Inserted before the reference node.</span></span> <span data-ttu-id="1c35c-116">Na przykład, aby wstawić nowy węzeł w pozycji 5:</span><span class="sxs-lookup"><span data-stu-id="1c35c-116">For example, to insert the new node in position 5:</span></span><br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> <span data-ttu-id="1c35c-117">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.InsertBefore%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="1c35c-117">For more information, see the <xref:System.Xml.XmlNode.InsertBefore%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|<span data-ttu-id="1c35c-118">Wstawiono po węźle odwołania.</span><span class="sxs-lookup"><span data-stu-id="1c35c-118">Inserted after the reference node.</span></span> <span data-ttu-id="1c35c-119">Przykład:</span><span class="sxs-lookup"><span data-stu-id="1c35c-119">For example:</span></span><br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> <span data-ttu-id="1c35c-120">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.InsertAfter%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="1c35c-120">For more information, see the <xref:System.Xml.XmlNode.InsertAfter%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|<span data-ttu-id="1c35c-121">Dodaje węzeł na końcu listy węzłów podrzędnych dla danego węzła.</span><span class="sxs-lookup"><span data-stu-id="1c35c-121">Adds the node to the end of the list of child nodes for the given node.</span></span> <span data-ttu-id="1c35c-122">Jeśli dodawany węzeł to <xref:System.Xml.XmlDocumentFragment>, cała zawartość fragmentu dokumentu zostanie przeniesiona na listę podrzędną tego węzła.</span><span class="sxs-lookup"><span data-stu-id="1c35c-122">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="1c35c-123">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.AppendChild%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="1c35c-123">For more information, see the <xref:System.Xml.XmlNode.AppendChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|<span data-ttu-id="1c35c-124">Dodaje węzeł na początku listy węzłów podrzędnych danego węzła.</span><span class="sxs-lookup"><span data-stu-id="1c35c-124">Adds the node to the beginning of the list of child nodes of the given node.</span></span> <span data-ttu-id="1c35c-125">Jeśli dodawany węzeł to <xref:System.Xml.XmlDocumentFragment>, cała zawartość fragmentu dokumentu zostanie przeniesiona na listę podrzędną tego węzła.</span><span class="sxs-lookup"><span data-stu-id="1c35c-125">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="1c35c-126">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.PrependChild%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="1c35c-126">For more information, see the <xref:System.Xml.XmlNode.PrependChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|<span data-ttu-id="1c35c-127">Dołącza <xref:System.Xml.XmlAttribute> węzeł do końca kolekcji atrybutów skojarzonej z elementem.</span><span class="sxs-lookup"><span data-stu-id="1c35c-127">Appends an <xref:System.Xml.XmlAttribute> node to the end of the attribute collection associated with an element.</span></span> <span data-ttu-id="1c35c-128">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlAttributeCollection.Append%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="1c35c-128">For more information, see the <xref:System.Xml.XmlAttributeCollection.Append%2A> method.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1c35c-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1c35c-129">See also</span></span>

- [<span data-ttu-id="1c35c-130">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="1c35c-130">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
