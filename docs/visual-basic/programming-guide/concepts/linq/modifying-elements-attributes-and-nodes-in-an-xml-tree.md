---
title: Modyfikowanie elementów, atrybutów i węzłów w Tree1 XML
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: 002e87d58ad1a3730889225bf4b3e50448431f2d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360933"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="910d4-102">Modyfikowanie elementów, atrybutów i węzłów w drzewie XML</span><span class="sxs-lookup"><span data-stu-id="910d4-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="910d4-103">Poniższa tabela zawiera podsumowanie metod i właściwości, których można użyć do modyfikacji elementu, jego elementów podrzędnych lub jego atrybutów.</span><span class="sxs-lookup"><span data-stu-id="910d4-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="910d4-104">Poniższe metody modyfikują <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="910d4-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="910d4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="910d4-105">Method</span></span>|<span data-ttu-id="910d4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="910d4-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="910d4-107">Zastępuje element przeanalizowanym kodem XML.</span><span class="sxs-lookup"><span data-stu-id="910d4-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="910d4-108">Usuwa całą zawartość (węzły podrzędne i atrybuty) elementu.</span><span class="sxs-lookup"><span data-stu-id="910d4-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="910d4-109">Usuwa atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="910d4-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="910d4-110">Zamienia całą zawartość (węzły podrzędne i atrybuty) elementu.</span><span class="sxs-lookup"><span data-stu-id="910d4-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="910d4-111">Zastępuje atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="910d4-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="910d4-112">Ustawia wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="910d4-112">Sets the value of an attribute.</span></span> <span data-ttu-id="910d4-113">Tworzy atrybut, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="910d4-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="910d4-114">Jeśli wartość jest ustawiona na `null` , program usuwa atrybut.</span><span class="sxs-lookup"><span data-stu-id="910d4-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="910d4-115">Ustawia wartość elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="910d4-115">Sets the value of a child element.</span></span> <span data-ttu-id="910d4-116">Tworzy element, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="910d4-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="910d4-117">Jeśli wartość jest ustawiona na `null` , powoduje usunięcie elementu.</span><span class="sxs-lookup"><span data-stu-id="910d4-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="910d4-118">Zamienia zawartość (węzły podrzędne) elementu na określony tekst.</span><span class="sxs-lookup"><span data-stu-id="910d4-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="910d4-119">Ustawia wartość elementu.</span><span class="sxs-lookup"><span data-stu-id="910d4-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="910d4-120">Poniższe metody modyfikują <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="910d4-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="910d4-121">Metoda</span><span class="sxs-lookup"><span data-stu-id="910d4-121">Method</span></span>|<span data-ttu-id="910d4-122">Opis</span><span class="sxs-lookup"><span data-stu-id="910d4-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="910d4-123">Ustawia wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="910d4-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="910d4-124">Ustawia wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="910d4-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="910d4-125">Następujące metody modyfikują <xref:System.Xml.Linq.XNode> (łącznie z <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> ).</span><span class="sxs-lookup"><span data-stu-id="910d4-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="910d4-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="910d4-126">Method</span></span>|<span data-ttu-id="910d4-127">Opis</span><span class="sxs-lookup"><span data-stu-id="910d4-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="910d4-128">Zamienia węzeł na nową zawartość.</span><span class="sxs-lookup"><span data-stu-id="910d4-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="910d4-129">Następujące metody modyfikują <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> a lub <xref:System.Xml.Linq.XDocument> ).</span><span class="sxs-lookup"><span data-stu-id="910d4-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="910d4-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="910d4-130">Method</span></span>|<span data-ttu-id="910d4-131">Opis</span><span class="sxs-lookup"><span data-stu-id="910d4-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="910d4-132">Zamienia węzły podrzędne na nową zawartość.</span><span class="sxs-lookup"><span data-stu-id="910d4-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="910d4-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="910d4-133">See also</span></span>

- [<span data-ttu-id="910d4-134">Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="910d4-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](modifying-xml-trees-linq-to-xml.md)
