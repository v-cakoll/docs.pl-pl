---
title: ToolStripContainer — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- ToolStripContainer
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], about ToolStripContainer control
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
ms.openlocfilehash: 59afb9de3a97545407fe96f5ded60faee9d9f725
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="toolstripcontainer-control-overview"></a><span data-ttu-id="0809c-102">ToolStripContainer — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="0809c-102">ToolStripContainer Control Overview</span></span>
<span data-ttu-id="0809c-103">A <xref:System.Windows.Forms.ToolStripContainer> ma panele w lewo, prawo, górnej i dolnej krawędzi pozycjonowanie i rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, i <xref:System.Windows.Forms.StatusStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="0809c-103">A <xref:System.Windows.Forms.ToolStripContainer> has panels on its left, right, top, and bottom sides for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="0809c-104">Wiele <xref:System.Windows.Forms.ToolStrip> formanty pionowo stosu umieszczenie w lewo lub w prawo <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="0809c-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically if you put them in the left or right <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="0809c-105">One poziomie stosu umieszczenie w górny lub dolny <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="0809c-105">They stack horizontally if you put them in the top or bottom <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="0809c-106">Można użyć centralną <xref:System.Windows.Forms.ToolStripContentPanel> z <xref:System.Windows.Forms.ToolStripContainer> do tradycyjnych formanty pozycji na formularzu.</span><span class="sxs-lookup"><span data-stu-id="0809c-106">You can use the central <xref:System.Windows.Forms.ToolStripContentPanel> of the <xref:System.Windows.Forms.ToolStripContainer> to position traditional controls on the form.</span></span>  
  
 <span data-ttu-id="0809c-107">Dowolnych lub wszystkich <xref:System.Windows.Forms.ToolStripContainer> formanty są bezpośrednio wybieranych w czasie projektowania i można go usunąć.</span><span class="sxs-lookup"><span data-stu-id="0809c-107">Any or all <xref:System.Windows.Forms.ToolStripContainer> controls are directly selectable at design time and can be deleted.</span></span> <span data-ttu-id="0809c-108">Każda <xref:System.Windows.Forms.ToolStripContainer> jest rozwijanej i zwijanej i zmienia rozmiar z formantami, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="0809c-108">Each panel of a <xref:System.Windows.Forms.ToolStripContainer> is expandable and collapsible, and resizes with the controls that it contains.</span></span>  
  
### <a name="important-toolstripcontainer-members"></a><span data-ttu-id="0809c-109">Elementy członkowskie ważne ToolStripContainer</span><span class="sxs-lookup"><span data-stu-id="0809c-109">Important ToolStripContainer Members</span></span>  
  
|<span data-ttu-id="0809c-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="0809c-110">Name</span></span>|<span data-ttu-id="0809c-111">Opis</span><span class="sxs-lookup"><span data-stu-id="0809c-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|<span data-ttu-id="0809c-112">Pobiera dolny panel elementu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="0809c-112">Gets the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|<span data-ttu-id="0809c-113">Pobiera lub ustawia wartość wskazującą czy dolny panel elementu <xref:System.Windows.Forms.ToolStripContainer> jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="0809c-113">Gets or sets a value indicating whether the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|<span data-ttu-id="0809c-114">Pobiera lewego panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="0809c-114">Gets the left panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|<span data-ttu-id="0809c-115">Pobiera lub ustawia wartość wskazującą czy lewego panelu <xref:System.Windows.Forms.ToolStripContainer> jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="0809c-115">Gets or sets a value indicating whether the left panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|<span data-ttu-id="0809c-116">Pobiera prawy panel elementu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="0809c-116">Gets the right panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|<span data-ttu-id="0809c-117">Pobiera lub ustawia wartość wskazującą czy prawy panel elementu <xref:System.Windows.Forms.ToolStripContainer> jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="0809c-117">Gets or sets a value indicating whether the right panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|<span data-ttu-id="0809c-118">Pobiera górny panel elementu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="0809c-118">Gets the top panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|<span data-ttu-id="0809c-119">Pobiera lub ustawia wartość wskazującą czy górny panel elementu <xref:System.Windows.Forms.ToolStripContainer> jest widoczny.</span><span class="sxs-lookup"><span data-stu-id="0809c-119">Gets or sets a value indicating whether the top panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0809c-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0809c-120">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 <xref:System.Windows.Forms.ToolStripContentPanel>
