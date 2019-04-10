---
title: 'Instrukcje: dokowanie kontrolek w Formularzach systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: 61ccad615eec81eb1aa77e6a99d48ef29ecb5be2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59231529"
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="28029-102">Instrukcje: dokowanie kontrolek w Formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="28029-102">How to: Dock Controls on Windows Forms</span></span>
<span data-ttu-id="28029-103">Można dokowanie formantów do krawędzi formularza lub je wypełnić kontener formantu (formularza lub kontrolki kontenera).</span><span class="sxs-lookup"><span data-stu-id="28029-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="28029-104">Na przykład Windows Explorer dokowane jego <xref:System.Windows.Forms.TreeView> kontrolki do lewej części okna i jego <xref:System.Windows.Forms.ListView> kontrolki po prawej stronie okna.</span><span class="sxs-lookup"><span data-stu-id="28029-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="28029-105">Użyj <xref:System.Windows.Forms.Control.Dock%2A> właściwości dla wszystkich widocznych kontrolek Windows Forms do definiowania tryb dokowania.</span><span class="sxs-lookup"><span data-stu-id="28029-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28029-106">Formanty są zadokowane w odwrotnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="28029-106">Controls are docked in reverse z-order.</span></span>  
  
 <span data-ttu-id="28029-107"><xref:System.Windows.Forms.Control.Dock%2A> Właściwość wchodzi w interakcję z <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="28029-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="28029-108">Aby uzyskać więcej informacji, zobacz [AutoSize właściwość — omówienie](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="28029-108">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>  
  
### <a name="to-dock-a-control"></a><span data-ttu-id="28029-109">Aby zadokować kontrolki</span><span class="sxs-lookup"><span data-stu-id="28029-109">To dock a control</span></span>  
  
1.  <span data-ttu-id="28029-110">Wybierz formant, który chcesz zadokować.</span><span class="sxs-lookup"><span data-stu-id="28029-110">Select the control that you want to dock.</span></span>  
  
2.  <span data-ttu-id="28029-111">W oknie dialogowym właściwości kliknij strzałkę po prawej stronie <xref:System.Windows.Forms.Control.Dock%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="28029-111">In the Properties window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="28029-112">Zostanie wyświetlony Edytor, pokazujący szereg pola reprezentujące krawędzie i środek formularza.</span><span class="sxs-lookup"><span data-stu-id="28029-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>  
  
3.  <span data-ttu-id="28029-113">Kliknij przycisk, który reprezentuje krawędzi formularza, które chcesz zadokować formantu.</span><span class="sxs-lookup"><span data-stu-id="28029-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="28029-114">Aby wypełnić zawartość formularza kontrolki lub kontrolki kontenera, kliknij pole Centrum.</span><span class="sxs-lookup"><span data-stu-id="28029-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="28029-115">Kliknij przycisk **(Brak)** wyłączyć dokowania.</span><span class="sxs-lookup"><span data-stu-id="28029-115">Click **(none)** to disable docking.</span></span>  
  
     <span data-ttu-id="28029-116">Kontrolka jest automatycznie dopasowane granice zadokowany krawędzi.</span><span class="sxs-lookup"><span data-stu-id="28029-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="28029-117">Musi być dziedziczone formantów `Protected` aby można było bez możliwości dokowania.</span><span class="sxs-lookup"><span data-stu-id="28029-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="28029-118">Aby zmienić poziom dostępu formantu, ustaw jego **modyfikator** właściwości w oknie dialogowym właściwości.</span><span class="sxs-lookup"><span data-stu-id="28029-118">To change the access level of a control, set its **Modifier** property in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28029-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="28029-119">See also</span></span>

- [<span data-ttu-id="28029-120">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="28029-120">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="28029-121">Rozmieszczanie formantów na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="28029-121">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="28029-122">Etykietowanie pojedynczych formantów formularzy systemu Windows i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="28029-122">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="28029-123">Formanty do użycia w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="28029-123">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="28029-124">Formanty formularzy systemu Windows według funkcji</span><span class="sxs-lookup"><span data-stu-id="28029-124">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- [<span data-ttu-id="28029-125">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="28029-125">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="28029-126">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="28029-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="28029-127">AutoSize — Przegląd właściwości</span><span class="sxs-lookup"><span data-stu-id="28029-127">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="28029-128">Instrukcje: kotwiczenie kontrolek na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="28029-128">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
