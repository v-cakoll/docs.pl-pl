---
title: Modyfikowanie elementów, atrybutów i węzłów w Tree1 XML
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: d548e6f5912437e5c5df27f55fcdb28990e92c8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666147"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="901ee-102">Modyfikowanie elementów, atrybutów i węzłów w drzewie XML</span><span class="sxs-lookup"><span data-stu-id="901ee-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="901ee-103">W poniższej tabeli podsumowano, metody i właściwości, których można zmodyfikować elementu, jego elementów podrzędnych lub jego atrybuty.</span><span class="sxs-lookup"><span data-stu-id="901ee-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="901ee-104">Zmodyfikuj następujące metody <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="901ee-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="901ee-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="901ee-105">Method</span></span>|<span data-ttu-id="901ee-106">Opis</span><span class="sxs-lookup"><span data-stu-id="901ee-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="901ee-107">Zamienia element przeanalizowany plik XML.</span><span class="sxs-lookup"><span data-stu-id="901ee-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="901ee-108">Usuwa wszystkie zawartości elementu (węzły podrzędne i atrybuty).</span><span class="sxs-lookup"><span data-stu-id="901ee-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="901ee-109">Usuwa atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="901ee-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="901ee-110">Zastępuje całą zawartość elementu (węzły podrzędne i atrybuty).</span><span class="sxs-lookup"><span data-stu-id="901ee-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="901ee-111">Zastępuje atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="901ee-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="901ee-112">Ustawia wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="901ee-112">Sets the value of an attribute.</span></span> <span data-ttu-id="901ee-113">Tworzy atrybut, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="901ee-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="901ee-114">Jeśli wartość jest równa `null`, usuwa atrybut.</span><span class="sxs-lookup"><span data-stu-id="901ee-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="901ee-115">Ustawia wartość elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="901ee-115">Sets the value of a child element.</span></span> <span data-ttu-id="901ee-116">Tworzy element, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="901ee-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="901ee-117">Jeśli wartość jest równa `null`, usuwa element.</span><span class="sxs-lookup"><span data-stu-id="901ee-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="901ee-118">Zamienia określony tekst zawartości elementu (węzły podrzędne).</span><span class="sxs-lookup"><span data-stu-id="901ee-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="901ee-119">Ustawia wartość elementu.</span><span class="sxs-lookup"><span data-stu-id="901ee-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="901ee-120">Zmodyfikuj następujące metody <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="901ee-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="901ee-121">Metoda</span><span class="sxs-lookup"><span data-stu-id="901ee-121">Method</span></span>|<span data-ttu-id="901ee-122">Opis</span><span class="sxs-lookup"><span data-stu-id="901ee-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="901ee-123">Ustawia wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="901ee-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="901ee-124">Ustawia wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="901ee-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="901ee-125">Zmodyfikuj następujące metody <xref:System.Xml.Linq.XNode> (w tym <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="901ee-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="901ee-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="901ee-126">Method</span></span>|<span data-ttu-id="901ee-127">Opis</span><span class="sxs-lookup"><span data-stu-id="901ee-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="901ee-128">Zamienia węzeł nowej zawartości.</span><span class="sxs-lookup"><span data-stu-id="901ee-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="901ee-129">Zmodyfikuj następujące metody <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="901ee-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="901ee-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="901ee-130">Method</span></span>|<span data-ttu-id="901ee-131">Opis</span><span class="sxs-lookup"><span data-stu-id="901ee-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="901ee-132">Zamienia węzłów podrzędnych nowej zawartości.</span><span class="sxs-lookup"><span data-stu-id="901ee-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="901ee-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="901ee-133">See also</span></span>

- [<span data-ttu-id="901ee-134">Modyfikowanie drzew XML (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="901ee-134">Modifying XML Trees (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
