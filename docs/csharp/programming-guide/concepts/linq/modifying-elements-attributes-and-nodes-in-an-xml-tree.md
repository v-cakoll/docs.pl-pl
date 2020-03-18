---
title: Modyfikowanie elementów, atrybutów i węzłów w drzewie XML3
ms.date: 07/20/2015
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
ms.openlocfilehash: 93a4d67129e22d0bbeef464c1d4d8758439edb7b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484233"
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a><span data-ttu-id="09540-102">Modyfikowanie elementów, atrybutów i węzłów w drzewie XML</span><span class="sxs-lookup"><span data-stu-id="09540-102">Modifying Elements, Attributes, and Nodes in an XML Tree</span></span>
<span data-ttu-id="09540-103">W poniższej tabeli podsumowano metody i właściwości, których można użyć do zmodyfikowania elementu, jego elementów podrzędnych lub jego atrybutów.</span><span class="sxs-lookup"><span data-stu-id="09540-103">The following table summarizes the methods and properties that you can use to modify an element, its child elements, or its attributes.</span></span>  
  
 <span data-ttu-id="09540-104">Następujące metody modyfikują plik <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="09540-104">The following methods modify an <xref:System.Xml.Linq.XElement>.</span></span>  
  
|<span data-ttu-id="09540-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="09540-105">Method</span></span>|<span data-ttu-id="09540-106">Opis</span><span class="sxs-lookup"><span data-stu-id="09540-106">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|<span data-ttu-id="09540-107">Zastępuje element przeanalizowanym kodem XML.</span><span class="sxs-lookup"><span data-stu-id="09540-107">Replaces an element with parsed XML.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|<span data-ttu-id="09540-108">Usuwa całą zawartość (węzły podrzędne i atrybuty) elementu.</span><span class="sxs-lookup"><span data-stu-id="09540-108">Removes all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="09540-109">Usuwa atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="09540-109">Removes the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|<span data-ttu-id="09540-110">Zastępuje całą zawartość (węzły podrzędne i atrybuty) elementu.</span><span class="sxs-lookup"><span data-stu-id="09540-110">Replaces all content (child nodes and attributes) of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|<span data-ttu-id="09540-111">Zastępuje atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="09540-111">Replaces the attributes of an element.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|<span data-ttu-id="09540-112">Ustawia wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="09540-112">Sets the value of an attribute.</span></span> <span data-ttu-id="09540-113">Tworzy atrybut, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="09540-113">Creates the attribute if it doesn't exist.</span></span> <span data-ttu-id="09540-114">Jeśli wartość jest `null`ustawiona na , usuwa atrybut.</span><span class="sxs-lookup"><span data-stu-id="09540-114">If the value is set to `null`, removes the attribute.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|<span data-ttu-id="09540-115">Ustawia wartość elementu podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="09540-115">Sets the value of a child element.</span></span> <span data-ttu-id="09540-116">Tworzy element, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="09540-116">Creates the element if it doesn't exist.</span></span> <span data-ttu-id="09540-117">Jeśli wartość jest `null`ustawiona na , usuwa element.</span><span class="sxs-lookup"><span data-stu-id="09540-117">If the value is set to `null`, removes the element.</span></span>|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="09540-118">Zastępuje zawartość (węzły podrzędne) elementu określonym tekstem.</span><span class="sxs-lookup"><span data-stu-id="09540-118">Replaces the content (child nodes) of an element with the specified text.</span></span>|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="09540-119">Ustawia wartość elementu.</span><span class="sxs-lookup"><span data-stu-id="09540-119">Sets the value of an element.</span></span>|  
  
 <span data-ttu-id="09540-120">Następujące metody modyfikują plik <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="09540-120">The following methods modify an <xref:System.Xml.Linq.XAttribute>.</span></span>  
  
|<span data-ttu-id="09540-121">Metoda</span><span class="sxs-lookup"><span data-stu-id="09540-121">Method</span></span>|<span data-ttu-id="09540-122">Opis</span><span class="sxs-lookup"><span data-stu-id="09540-122">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|<span data-ttu-id="09540-123">Ustawia wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="09540-123">Sets the value of an attribute.</span></span>|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|<span data-ttu-id="09540-124">Ustawia wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="09540-124">Sets the value of an attribute.</span></span>|  
  
 <span data-ttu-id="09540-125">Następujące metody modyfikują <xref:System.Xml.Linq.XNode> <xref:System.Xml.Linq.XElement> (w tym lub <xref:System.Xml.Linq.XDocument>).</span><span class="sxs-lookup"><span data-stu-id="09540-125">The following methods modify an <xref:System.Xml.Linq.XNode> (including an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="09540-126">Metoda</span><span class="sxs-lookup"><span data-stu-id="09540-126">Method</span></span>|<span data-ttu-id="09540-127">Opis</span><span class="sxs-lookup"><span data-stu-id="09540-127">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|<span data-ttu-id="09540-128">Zastępuje węzeł nową zawartością.</span><span class="sxs-lookup"><span data-stu-id="09540-128">Replaces a node with new content.</span></span>|  
  
 <span data-ttu-id="09540-129">Następujące metody modyfikują <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument>(an <xref:System.Xml.Linq.XContainer> lub ).</span><span class="sxs-lookup"><span data-stu-id="09540-129">The following methods modify an <xref:System.Xml.Linq.XContainer> (an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XDocument>).</span></span>  
  
|<span data-ttu-id="09540-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="09540-130">Method</span></span>|<span data-ttu-id="09540-131">Opis</span><span class="sxs-lookup"><span data-stu-id="09540-131">Description</span></span>|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|<span data-ttu-id="09540-132">Zastępuje węzły podrzędne nową zawartością.</span><span class="sxs-lookup"><span data-stu-id="09540-132">Replaces the children nodes with new content.</span></span>|  
