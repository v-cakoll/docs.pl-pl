---
title: 'Instrukcje: Dokowanie formantów na formularzach Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: 4acda9149dd147a823eb42d3962a22b75df93802
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720278"
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="eda5a-102">Instrukcje: Dokowanie formantów na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eda5a-102">How to: Dock Controls on Windows Forms</span></span>
<span data-ttu-id="eda5a-103">Można dokowanie formantów do krawędzi formularza lub je wypełnić kontener formantu (formularza lub kontrolki kontenera).</span><span class="sxs-lookup"><span data-stu-id="eda5a-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="eda5a-104">Na przykład Windows Explorer dokowane jego <xref:System.Windows.Forms.TreeView> kontrolki do lewej części okna i jego <xref:System.Windows.Forms.ListView> kontrolki po prawej stronie okna.</span><span class="sxs-lookup"><span data-stu-id="eda5a-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="eda5a-105">Użyj <xref:System.Windows.Forms.Control.Dock%2A> właściwości dla wszystkich widocznych kontrolek Windows Forms do definiowania tryb dokowania.</span><span class="sxs-lookup"><span data-stu-id="eda5a-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eda5a-106">Formanty są zadokowane w odwrotnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="eda5a-106">Controls are docked in reverse z-order.</span></span>  
  
 <span data-ttu-id="eda5a-107"><xref:System.Windows.Forms.Control.Dock%2A> Właściwość wchodzi w interakcję z <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="eda5a-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="eda5a-108">Aby uzyskać więcej informacji, zobacz [AutoSize właściwość — omówienie](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="eda5a-108">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>  
  
### <a name="to-dock-a-control"></a><span data-ttu-id="eda5a-109">Aby zadokować kontrolki</span><span class="sxs-lookup"><span data-stu-id="eda5a-109">To dock a control</span></span>  
  
1.  <span data-ttu-id="eda5a-110">Wybierz formant, który chcesz zadokować.</span><span class="sxs-lookup"><span data-stu-id="eda5a-110">Select the control that you want to dock.</span></span>  
  
2.  <span data-ttu-id="eda5a-111">W oknie dialogowym właściwości kliknij strzałkę po prawej stronie <xref:System.Windows.Forms.Control.Dock%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="eda5a-111">In the Properties window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="eda5a-112">Zostanie wyświetlony Edytor, pokazujący szereg pola reprezentujące krawędzie i środek formularza.</span><span class="sxs-lookup"><span data-stu-id="eda5a-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>  
  
3.  <span data-ttu-id="eda5a-113">Kliknij przycisk, który reprezentuje krawędzi formularza, które chcesz zadokować formantu.</span><span class="sxs-lookup"><span data-stu-id="eda5a-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="eda5a-114">Aby wypełnić zawartość formularza kontrolki lub kontrolki kontenera, kliknij pole Centrum.</span><span class="sxs-lookup"><span data-stu-id="eda5a-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="eda5a-115">Kliknij przycisk **(Brak)** wyłączyć dokowania.</span><span class="sxs-lookup"><span data-stu-id="eda5a-115">Click **(none)** to disable docking.</span></span>  
  
     <span data-ttu-id="eda5a-116">Kontrolka jest automatycznie dopasowane granice zadokowany krawędzi.</span><span class="sxs-lookup"><span data-stu-id="eda5a-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eda5a-117">Musi być dziedziczone formantów `Protected` aby można było bez możliwości dokowania.</span><span class="sxs-lookup"><span data-stu-id="eda5a-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="eda5a-118">Aby zmienić poziom dostępu formantu, ustaw jego **modyfikator** właściwości w oknie dialogowym właściwości.</span><span class="sxs-lookup"><span data-stu-id="eda5a-118">To change the access level of a control, set its **Modifier** property in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eda5a-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eda5a-119">See also</span></span>
- [<span data-ttu-id="eda5a-120">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eda5a-120">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="eda5a-121">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eda5a-121">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="eda5a-122">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="eda5a-122">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="eda5a-123">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eda5a-123">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="eda5a-124">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="eda5a-124">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
- [<span data-ttu-id="eda5a-125">Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="eda5a-125">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="eda5a-126">Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="eda5a-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="eda5a-127">AutoSize, właściwość — omówienie</span><span class="sxs-lookup"><span data-stu-id="eda5a-127">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="eda5a-128">Instrukcje: Zakotwiczenia formantów na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eda5a-128">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
