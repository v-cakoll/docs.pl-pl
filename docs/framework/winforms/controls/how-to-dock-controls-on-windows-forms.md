---
title: 'Instrukcje: dokowanie kontrolek w Formularzach systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: dc514fd8b9b7a17bf07a878e42729db4187d2b82
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963628"
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="2429a-102">Instrukcje: dokowanie kontrolek w Formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2429a-102">How to: Dock Controls on Windows Forms</span></span>
<span data-ttu-id="2429a-103">Możesz zadokować kontrolki do krawędzi formularza lub popełniać kontener formantu (formularz lub kontrolka kontenera).</span><span class="sxs-lookup"><span data-stu-id="2429a-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="2429a-104">Na przykład Eksplorator Windows dockuje swój <xref:System.Windows.Forms.TreeView> formant po lewej stronie okna i jego <xref:System.Windows.Forms.ListView> kontrolkę po prawej stronie okna.</span><span class="sxs-lookup"><span data-stu-id="2429a-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="2429a-105"><xref:System.Windows.Forms.Control.Dock%2A> Użyj właściwości dla wszystkich widocznych kontrolek Windows Forms, aby zdefiniować tryb dokowania.</span><span class="sxs-lookup"><span data-stu-id="2429a-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2429a-106">Kontrolki są zadokowane w odwrotnej kolejności z.</span><span class="sxs-lookup"><span data-stu-id="2429a-106">Controls are docked in reverse z-order.</span></span>  
  
 <span data-ttu-id="2429a-107"><xref:System.Windows.Forms.Control.Dock%2A> Właściwość współdziała zwłaściwością<xref:System.Windows.Forms.Control.AutoSize%2A> .</span><span class="sxs-lookup"><span data-stu-id="2429a-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="2429a-108">Aby uzyskać więcej informacji, zobacz [Omówienie właściwości AutoSize](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2429a-108">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>  
  
### <a name="to-dock-a-control"></a><span data-ttu-id="2429a-109">Aby zadokować formant</span><span class="sxs-lookup"><span data-stu-id="2429a-109">To dock a control</span></span>  
  
1. <span data-ttu-id="2429a-110">Wybierz kontrolkę, która ma zostać zadokowany.</span><span class="sxs-lookup"><span data-stu-id="2429a-110">Select the control that you want to dock.</span></span>  
  
2. <span data-ttu-id="2429a-111">W okno właściwości kliknij strzałkę znajdującą się po prawej stronie <xref:System.Windows.Forms.Control.Dock%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2429a-111">In the Properties window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="2429a-112">Wyświetlany jest Edytor, który pokazuje serię pól reprezentujących krawędzie i orodek formularza.</span><span class="sxs-lookup"><span data-stu-id="2429a-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>  
  
3. <span data-ttu-id="2429a-113">Kliknij przycisk, który reprezentuje krawędź formularza, w której chcesz zadokować formant.</span><span class="sxs-lookup"><span data-stu-id="2429a-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="2429a-114">Aby wypełnić zawartość formularza kontrolki lub kontrolki kontenera, kliknij pole środkowe.</span><span class="sxs-lookup"><span data-stu-id="2429a-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="2429a-115">Kliknij pozycję **(brak)** , aby wyłączyć dokowanie.</span><span class="sxs-lookup"><span data-stu-id="2429a-115">Click **(none)** to disable docking.</span></span>  
  
     <span data-ttu-id="2429a-116">Rozmiar formantu jest automatycznie zmieniany w celu dopasowania do granic zadokowanej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="2429a-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2429a-117">Dziedziczone kontrolki muszą `Protected` mieć możliwość zadokowania.</span><span class="sxs-lookup"><span data-stu-id="2429a-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="2429a-118">Aby zmienić poziom dostępu kontrolki, ustaw jej właściwość **modyfikującą** w okno właściwości.</span><span class="sxs-lookup"><span data-stu-id="2429a-118">To change the access level of a control, set its **Modifier** property in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2429a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2429a-119">See also</span></span>

- [<span data-ttu-id="2429a-120">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2429a-120">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="2429a-121">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2429a-121">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="2429a-122">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="2429a-122">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="2429a-123">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2429a-123">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="2429a-124">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="2429a-124">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- [<span data-ttu-id="2429a-125">Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w kontrolce FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2429a-125">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="2429a-126">Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2429a-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="2429a-127">AutoSize, właściwość — omówienie</span><span class="sxs-lookup"><span data-stu-id="2429a-127">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="2429a-128">Instrukcje: Kontrolki kotwicowe na Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2429a-128">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
