---
title: "Utwórz nowe węzły w modelu DOM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 195c0f8184bbbd84826def87ce74daa49965cb93
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="create-new-nodes-in-the-dom"></a><span data-ttu-id="06954-102">Utwórz nowe węzły w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="06954-102">Create New Nodes in the DOM</span></span>
<span data-ttu-id="06954-103"><xref:System.Xml.XmlDocument> Ma metody create dla wszystkich typów węzłów.</span><span class="sxs-lookup"><span data-stu-id="06954-103">The <xref:System.Xml.XmlDocument> has a create method for all of the node types.</span></span> <span data-ttu-id="06954-104">Podaj metodę o nazwie, gdy jest to wymagane, a zawartości lub inne parametry dla tych węzłów, które ma zawartość (na przykład węzeł tekstowy) i węzłem, jest tworzona.</span><span class="sxs-lookup"><span data-stu-id="06954-104">Supply the method with a name when required, and content or other parameters for those nodes that have content (for example, a text node), and the node is created.</span></span> <span data-ttu-id="06954-105">Dostępne są następujące metody: te, które wymagają nazwy i kilka innych parametrów wprowadzić, aby utworzyć odpowiedni węzeł.</span><span class="sxs-lookup"><span data-stu-id="06954-105">The following methods are ones that need a name and a few other parameters filled to create an appropriate node.</span></span>  
  
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
  
 <span data-ttu-id="06954-106">Inne typy węzłów mają wymagania więcej niż tylko dostarczania danych do parametrów.</span><span class="sxs-lookup"><span data-stu-id="06954-106">Other node types have more requirements than just providing data to parameters.</span></span>  
  
 <span data-ttu-id="06954-107">Aby uzyskać informacje o atrybutach, zobacz [tworzenie nowych atrybutów elementów w modelu DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="06954-107">For information on attributes, see [Creating New Attributes for Elements in the DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md).</span></span> <span data-ttu-id="06954-108">Aby uzyskać informacji o weryfikacji nazwy elementów i atrybutów, zobacz [— Element XML i weryfikacja nazwy atrybutu podczas tworzenia nowych węzłów](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="06954-108">For information on element and attribute name validation, see [XML Element and Attribute Name Verification when Creating New Nodes](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md).</span></span> <span data-ttu-id="06954-109">Do tworzenia odwołań do jednostek, zobacz [odwołania do tworzenia nowych jednostek](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span><span class="sxs-lookup"><span data-stu-id="06954-109">For creating entity references, see [Creating New Entity References](../../../../docs/standard/data/xml/creating-new-entity-references.md).</span></span> <span data-ttu-id="06954-110">Aby uzyskać informacji na temat wpływu rozszerzenie odwołań do jednostek w przestrzeni nazw, zobacz [Namespace ma to wpływu na jednostki odwołanie do rozszerzenia dla nowych węzłów zawierających elementy i atrybuty](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="06954-110">For information on how namespaces affect the expansion of entity references, see [Namespace Affect on Entity Reference Expansion for New Nodes Containing Elements and Attributes](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).</span></span>  
  
 <span data-ttu-id="06954-111">Po utworzeniu nowych węzłów, dostępnych jest kilka metod wstawić je do drzewa.</span><span class="sxs-lookup"><span data-stu-id="06954-111">Once new nodes are created, there are several methods available to insert them into the tree.</span></span> <span data-ttu-id="06954-112">W tabeli przedstawiono metody opis gdy nowy węzeł jest dostępny w XML modelu DOM (Document Object).</span><span class="sxs-lookup"><span data-stu-id="06954-112">The table lists the methods with a description of where the new node appears in the XML Document Object Model (DOM).</span></span>  
  
|<span data-ttu-id="06954-113">Metoda</span><span class="sxs-lookup"><span data-stu-id="06954-113">Method</span></span>|<span data-ttu-id="06954-114">Rozmieszczenie</span><span class="sxs-lookup"><span data-stu-id="06954-114">Node placement</span></span>|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|<span data-ttu-id="06954-115">Dodaje przed węzła odniesienia.</span><span class="sxs-lookup"><span data-stu-id="06954-115">Inserted before the reference node.</span></span> <span data-ttu-id="06954-116">Na przykład, aby wstawić nowy węzeł w położeniu 5:</span><span class="sxs-lookup"><span data-stu-id="06954-116">For example, to insert the new node in position 5:</span></span><br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> <span data-ttu-id="06954-117">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.InsertBefore%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="06954-117">For more information, see the <xref:System.Xml.XmlNode.InsertBefore%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|<span data-ttu-id="06954-118">Dodaje po węzła odniesienia.</span><span class="sxs-lookup"><span data-stu-id="06954-118">Inserted after the reference node.</span></span> <span data-ttu-id="06954-119">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="06954-119">For example:</span></span><br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> <span data-ttu-id="06954-120">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.InsertAfter%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="06954-120">For more information, see the <xref:System.Xml.XmlNode.InsertAfter%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|<span data-ttu-id="06954-121">Dodaje węzeł na końcu listy węzłów podrzędnych dla danego węzła.</span><span class="sxs-lookup"><span data-stu-id="06954-121">Adds the node to the end of the list of child nodes for the given node.</span></span> <span data-ttu-id="06954-122">Jeśli węzeł dodawany jest <xref:System.Xml.XmlDocumentFragment>, cała zawartość fragment dokumentu zostaną przeniesione do listy podrzędny tego węzła.</span><span class="sxs-lookup"><span data-stu-id="06954-122">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="06954-123">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.AppendChild%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="06954-123">For more information, see the <xref:System.Xml.XmlNode.AppendChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|<span data-ttu-id="06954-124">Dodaje węzeł na początku listy węzłów podrzędnych danego węzła.</span><span class="sxs-lookup"><span data-stu-id="06954-124">Adds the node to the beginning of the list of child nodes of the given node.</span></span> <span data-ttu-id="06954-125">Jeśli węzeł dodawany jest <xref:System.Xml.XmlDocumentFragment>, cała zawartość fragment dokumentu zostaną przeniesione do listy podrzędny tego węzła.</span><span class="sxs-lookup"><span data-stu-id="06954-125">If the node being added is an <xref:System.Xml.XmlDocumentFragment>, the entire contents of the document fragment are moved into the child list of this node.</span></span> <span data-ttu-id="06954-126">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.PrependChild%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="06954-126">For more information, see the <xref:System.Xml.XmlNode.PrependChild%2A> method.</span></span>|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|<span data-ttu-id="06954-127">Dołącza <xref:System.Xml.XmlAttribute> węzła do końca kolekcji atrybutów skojarzona z elementem.</span><span class="sxs-lookup"><span data-stu-id="06954-127">Appends an <xref:System.Xml.XmlAttribute> node to the end of the attribute collection associated with an element.</span></span> <span data-ttu-id="06954-128">Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlAttributeCollection.Append%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="06954-128">For more information, see the <xref:System.Xml.XmlAttributeCollection.Append%2A> method.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06954-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06954-129">See Also</span></span>  
 [<span data-ttu-id="06954-130">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="06954-130">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
