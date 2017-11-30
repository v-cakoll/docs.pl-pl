---
title: "ToolStripContainer — Informacje o formancie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolStripContainer
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], about ToolStripContainer control
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4abc783961177a55cdb81cefd21ed2d7aefb0620
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="toolstripcontainer-control-overview"></a><span data-ttu-id="d8f14-102">ToolStripContainer — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="d8f14-102">ToolStripContainer Control Overview</span></span>
<span data-ttu-id="d8f14-103">A <xref:System.Windows.Forms.ToolStripContainer> ma panele w lewo, prawo, górnej i dolnej krawędzi pozycjonowanie i rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, i <xref:System.Windows.Forms.StatusStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="d8f14-103">A <xref:System.Windows.Forms.ToolStripContainer> has panels on its left, right, top, and bottom sides for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="d8f14-104">Wiele <xref:System.Windows.Forms.ToolStrip> formanty pionowo stosu umieszczenie w lewo lub w prawo <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="d8f14-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically if you put them in the left or right <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="d8f14-105">One poziomie stosu umieszczenie w górny lub dolny <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="d8f14-105">They stack horizontally if you put them in the top or bottom <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="d8f14-106">Można użyć centralną <xref:System.Windows.Forms.ToolStripContentPanel> z <xref:System.Windows.Forms.ToolStripContainer> do tradycyjnych formanty pozycji na formularzu.</span><span class="sxs-lookup"><span data-stu-id="d8f14-106">You can use the central <xref:System.Windows.Forms.ToolStripContentPanel> of the <xref:System.Windows.Forms.ToolStripContainer> to position traditional controls on the form.</span></span>  
  
 <span data-ttu-id="d8f14-107">Dowolnych lub wszystkich <xref:System.Windows.Forms.ToolStripContainer> formanty są bezpośrednio wybieranych w czasie projektowania i można go usunąć.</span><span class="sxs-lookup"><span data-stu-id="d8f14-107">Any or all <xref:System.Windows.Forms.ToolStripContainer> controls are directly selectable at design time and can be deleted.</span></span> <span data-ttu-id="d8f14-108">Każda <xref:System.Windows.Forms.ToolStripContainer> jest rozwijanej i zwijanej i zmienia rozmiar z formantami, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="d8f14-108">Each panel of a <xref:System.Windows.Forms.ToolStripContainer> is expandable and collapsible, and resizes with the controls that it contains.</span></span>  
  
### <a name="important-toolstripcontainer-members"></a><span data-ttu-id="d8f14-109">Elementy członkowskie ważne ToolStripContainer</span><span class="sxs-lookup"><span data-stu-id="d8f14-109">Important ToolStripContainer Members</span></span>  
  
|<span data-ttu-id="d8f14-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d8f14-110">Name</span></span>|<span data-ttu-id="d8f14-111">Opis</span><span class="sxs-lookup"><span data-stu-id="d8f14-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|<span data-ttu-id="d8f14-112">Pobiera dolny panel elementu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="d8f14-112">Gets the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|<span data-ttu-id="d8f14-113">Pobiera lub ustawia wartość wskazującą czy dolny panel elementu <xref:System.Windows.Forms.ToolStripContainer> jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="d8f14-113">Gets or sets a value indicating whether the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|<span data-ttu-id="d8f14-114">Pobiera lewego panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="d8f14-114">Gets the left panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|<span data-ttu-id="d8f14-115">Pobiera lub ustawia wartość wskazującą czy lewego panelu <xref:System.Windows.Forms.ToolStripContainer> jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="d8f14-115">Gets or sets a value indicating whether the left panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|<span data-ttu-id="d8f14-116">Pobiera prawy panel elementu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="d8f14-116">Gets the right panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|<span data-ttu-id="d8f14-117">Pobiera lub ustawia wartość wskazującą czy prawy panel elementu <xref:System.Windows.Forms.ToolStripContainer> jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="d8f14-117">Gets or sets a value indicating whether the right panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|<span data-ttu-id="d8f14-118">Pobiera górny panel elementu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="d8f14-118">Gets the top panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|<span data-ttu-id="d8f14-119">Pobiera lub ustawia wartość wskazującą czy górny panel elementu <xref:System.Windows.Forms.ToolStripContainer> jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="d8f14-119">Gets or sets a value indicating whether the top panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8f14-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d8f14-120">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 <xref:System.Windows.Forms.ToolStripContentPanel>
