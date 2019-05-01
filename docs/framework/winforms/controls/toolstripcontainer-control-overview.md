---
title: ToolStripContainer — Informacje o formancie
ms.date: 03/30/2017
f1_keywords:
- ToolStripContainer
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], about ToolStripContainer control
ms.assetid: c7d63bff-64e2-4a63-bd89-d31bc96dacb8
ms.openlocfilehash: c279316c2a372a1498707b27ec8658813306304b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62009477"
---
# <a name="toolstripcontainer-control-overview"></a><span data-ttu-id="c0a3b-102">ToolStripContainer — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="c0a3b-102">ToolStripContainer Control Overview</span></span>
<span data-ttu-id="c0a3b-103">A <xref:System.Windows.Forms.ToolStripContainer> ma paneli w lewo, po prawej stronie, górnej i dolne krawędzie, pozycjonowanie i rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, i <xref:System.Windows.Forms.StatusStrip> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="c0a3b-103">A <xref:System.Windows.Forms.ToolStripContainer> has panels on its left, right, top, and bottom sides for positioning and rafting <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="c0a3b-104">Wiele <xref:System.Windows.Forms.ToolStrip> kontrolki w pionie stosu umieszczenie w lewo lub w prawo <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="c0a3b-104">Multiple <xref:System.Windows.Forms.ToolStrip> controls stack vertically if you put them in the left or right <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="c0a3b-105">One ułożone poziomo, jeśli umieść je w górę lub w dół <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="c0a3b-105">They stack horizontally if you put them in the top or bottom <xref:System.Windows.Forms.ToolStripContainer>.</span></span> <span data-ttu-id="c0a3b-106">Możesz użyć centralnej <xref:System.Windows.Forms.ToolStripContentPanel> z <xref:System.Windows.Forms.ToolStripContainer> do pozycji tradycyjne formanty formularza.</span><span class="sxs-lookup"><span data-stu-id="c0a3b-106">You can use the central <xref:System.Windows.Forms.ToolStripContentPanel> of the <xref:System.Windows.Forms.ToolStripContainer> to position traditional controls on the form.</span></span>  
  
 <span data-ttu-id="c0a3b-107">Any lub all <xref:System.Windows.Forms.ToolStripContainer> formanty są bezpośrednio można wybierać w czasie projektowania i można je usunąć.</span><span class="sxs-lookup"><span data-stu-id="c0a3b-107">Any or all <xref:System.Windows.Forms.ToolStripContainer> controls are directly selectable at design time and can be deleted.</span></span> <span data-ttu-id="c0a3b-108">Każdy zespół <xref:System.Windows.Forms.ToolStripContainer> jest rozwijane i zwijane i zmienia rozmiar z kontrolkami, które zawiera.</span><span class="sxs-lookup"><span data-stu-id="c0a3b-108">Each panel of a <xref:System.Windows.Forms.ToolStripContainer> is expandable and collapsible, and resizes with the controls that it contains.</span></span>  
  
### <a name="important-toolstripcontainer-members"></a><span data-ttu-id="c0a3b-109">ToolStripContainer ważne elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c0a3b-109">Important ToolStripContainer Members</span></span>  
  
|<span data-ttu-id="c0a3b-110">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c0a3b-110">Name</span></span>|<span data-ttu-id="c0a3b-111">Opis</span><span class="sxs-lookup"><span data-stu-id="c0a3b-111">Description</span></span>|  
|----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanel%2A>|<span data-ttu-id="c0a3b-112">Pobiera dolnego panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="c0a3b-112">Gets the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.BottomToolStripPanelVisible%2A>|<span data-ttu-id="c0a3b-113">Pobiera lub ustawia wartość wskazującą czy dolnego panelu <xref:System.Windows.Forms.ToolStripContainer> jest widoczna.</span><span class="sxs-lookup"><span data-stu-id="c0a3b-113">Gets or sets a value indicating whether the bottom panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanel%2A>|<span data-ttu-id="c0a3b-114">Pobiera lewego panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="c0a3b-114">Gets the left panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.LeftToolStripPanelVisible%2A>|<span data-ttu-id="c0a3b-115">Pobiera lub ustawia wartość wskazującą czy lewego panelu <xref:System.Windows.Forms.ToolStripContainer> jest widoczna.</span><span class="sxs-lookup"><span data-stu-id="c0a3b-115">Gets or sets a value indicating whether the left panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanel%2A>|<span data-ttu-id="c0a3b-116">Pobiera prawy panel <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="c0a3b-116">Gets the right panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.RightToolStripPanelVisible%2A>|<span data-ttu-id="c0a3b-117">Pobiera lub ustawia wartość wskazującą czy prawy panel <xref:System.Windows.Forms.ToolStripContainer> jest widoczna.</span><span class="sxs-lookup"><span data-stu-id="c0a3b-117">Gets or sets a value indicating whether the right panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A>|<span data-ttu-id="c0a3b-118">Pobiera górnego panelu <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="c0a3b-118">Gets the top panel of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanelVisible%2A>|<span data-ttu-id="c0a3b-119">Pobiera lub ustawia wartość wskazującą czy górnego panelu <xref:System.Windows.Forms.ToolStripContainer> jest widoczna.</span><span class="sxs-lookup"><span data-stu-id="c0a3b-119">Gets or sets a value indicating whether the top panel of the <xref:System.Windows.Forms.ToolStripContainer> is visible.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0a3b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0a3b-120">See also</span></span>

- <xref:System.Windows.Forms.ToolStripContainer>
- <xref:System.Windows.Forms.ToolStripContentPanel>
