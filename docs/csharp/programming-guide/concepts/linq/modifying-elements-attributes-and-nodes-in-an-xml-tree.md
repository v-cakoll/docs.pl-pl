---
title: "Modyfikowanie elementy, atrybuty i węzłów w Tree3 XML"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: da3b31456bc86b547c5174143620f464dc42f35b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="f29d6-102">Modyfikowanie elementy, atrybuty i węzłów w drzewie XML</span><span class="sxs-lookup"><span data-stu-id="f29d6-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="f29d6-103">W poniższej tabeli przedstawiono metody i właściwości, które można zmodyfikować elementu, jego elementy podrzędne lub jego atrybuty.</span><span class="sxs-lookup"><span data-stu-id="f29d6-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="f29d6-104">Zmodyfikuj następujące metody <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="f29d6-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="f29d6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f29d6-105">Method</span></span>|<span data-ttu-id="f29d6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f29d6-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="f29d6-107">Zamienia element XML przeanalizowany.</span><span class="sxs-lookup"><span data-stu-id="f29d6-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="f29d6-108">Usuwa wszystkie zawartości elementu (węzły podrzędne i atrybuty).</span><span class="sxs-lookup"><span data-stu-id="f29d6-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="f29d6-109">Usuwa atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="f29d6-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="f29d6-110">Zamienia wszystkie zawartości elementu (węzły podrzędne i atrybuty).</span><span class="sxs-lookup"><span data-stu-id="f29d6-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="f29d6-111">Zamienia atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="f29d6-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="f29d6-112">Ustawia wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f29d6-112">Sets the value of an attribute.</span></span> <span data-ttu-id="f29d6-113">Tworzy atrybut, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f29d6-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="f29d6-114">Jeśli wartość jest równa `null`, usuwa atrybut.</span><span class="sxs-lookup"><span data-stu-id="f29d6-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="f29d6-115">Ustawia wartość elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="f29d6-115">Sets the value of a child element.</span></span> <span data-ttu-id="f29d6-116">Tworzy element, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="f29d6-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="f29d6-117">Jeśli wartość jest równa `null`, usuwa element.</span><span class="sxs-lookup"><span data-stu-id="f29d6-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="f29d6-118">Zamienia określony tekst zawartości elementu (węzłów podrzędnych).</span><span class="sxs-lookup"><span data-stu-id="f29d6-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="f29d6-119">Ustawia wartość elementu.</span><span class="sxs-lookup"><span data-stu-id="f29d6-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="f29d6-120">Zmodyfikuj następujące metody <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f29d6-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="f29d6-121">Metoda</span><span class="sxs-lookup"><span data-stu-id="f29d6-121">Method</span></span>|<span data-ttu-id="f29d6-122">Opis</span><span class="sxs-lookup"><span data-stu-id="f29d6-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="f29d6-123">Ustawia wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f29d6-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="f29d6-124">Ustawia wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="f29d6-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="f29d6-125">Modyfikowanie następujących metod <xref:System.Xml.Linq.XNode> (łącznie z <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="f29d6-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="f29d6-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="f29d6-126">Method</span></span>|<span data-ttu-id="f29d6-127">Opis</span><span class="sxs-lookup"><span data-stu-id="f29d6-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="f29d6-128">Zamienia węzła nową zawartość.</span><span class="sxs-lookup"><span data-stu-id="f29d6-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="f29d6-129">Modyfikowanie następujących metod <xref:System.Xml.Linq.XContainer> ( <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="f29d6-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="f29d6-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="f29d6-130">Method</span></span>|<span data-ttu-id="f29d6-131">Opis</span><span class="sxs-lookup"><span data-stu-id="f29d6-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="f29d6-132">Węzły podrzędne są zastępowane nową zawartość.</span><span class="sxs-lookup"><span data-stu-id="f29d6-132">Replaces the children nodes with new content.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f29d6-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f29d6-133">See Also</span></span>  
 [<span data-ttu-id="f29d6-134">Modyfikowanie drzew XML (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f29d6-134">Modifying XML Trees (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
