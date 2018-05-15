---
title: 'Porady: dokowanie formantów na formularzach systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], docking
- Explorer-style applications [Windows Forms], creating
- Windows Forms controls, filling client area
ms.assetid: bc11f2e4-e90a-4830-b0e2-f43b6e2b8bec
ms.openlocfilehash: 6cb4c982cb4c9e2df8d0335738ca087733209bdc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-dock-controls-on-windows-forms"></a><span data-ttu-id="f9d71-102">Porady: dokowanie formantów na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f9d71-102">How to: Dock Controls on Windows Forms</span></span>
<span data-ttu-id="f9d71-103">Możesz dokowanie formantów na krawędziach formularza lub je wypełnienia formantu kontenera (formularza lub kontrolki kontenera).</span><span class="sxs-lookup"><span data-stu-id="f9d71-103">You can dock controls to the edges of your form or have them fill the control's container (either a form or a container control).</span></span> <span data-ttu-id="f9d71-104">Na przykład stacje dokujące Eksploratora Windows jego <xref:System.Windows.Forms.TreeView> kontrolki do lewej strony okna i jego <xref:System.Windows.Forms.ListView> formantu do prawej krawędzi okna.</span><span class="sxs-lookup"><span data-stu-id="f9d71-104">For example, Windows Explorer docks its <xref:System.Windows.Forms.TreeView> control to the left side of the window and its <xref:System.Windows.Forms.ListView> control to the right side of the window.</span></span> <span data-ttu-id="f9d71-105">Użyj <xref:System.Windows.Forms.Control.Dock%2A> właściwości dla wszystkich widoczne formantów formularzy systemu Windows do definiowania trybu dokowania.</span><span class="sxs-lookup"><span data-stu-id="f9d71-105">Use the <xref:System.Windows.Forms.Control.Dock%2A> property for all visible Windows Forms controls to define the docking mode.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9d71-106">Formanty są zadokowane w odwrotnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="f9d71-106">Controls are docked in reverse z-order.</span></span>  
  
 <span data-ttu-id="f9d71-107"><xref:System.Windows.Forms.Control.Dock%2A> Właściwości współdziała z <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f9d71-107">The <xref:System.Windows.Forms.Control.Dock%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="f9d71-108">Aby uzyskać więcej informacji, zobacz [AutoSize — Przegląd właściwości](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f9d71-108">For more information, see [AutoSize Property Overview](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span></span>  
  
### <a name="to-dock-a-control"></a><span data-ttu-id="f9d71-109">Aby dock — formant</span><span class="sxs-lookup"><span data-stu-id="f9d71-109">To dock a control</span></span>  
  
1.  <span data-ttu-id="f9d71-110">Wybierz kontrolkę, która ma być dokowania.</span><span class="sxs-lookup"><span data-stu-id="f9d71-110">Select the control that you want to dock.</span></span>  
  
2.  <span data-ttu-id="f9d71-111">W oknie właściwości, kliknij strzałkę po prawej stronie <xref:System.Windows.Forms.Control.Dock%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f9d71-111">In the Properties window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="f9d71-112">Edytor wyświetlany jest przedstawia serię pól reprezentujący krawędzie i środek formularza.</span><span class="sxs-lookup"><span data-stu-id="f9d71-112">An editor is displayed that shows a series of boxes representing the edges and the center of the form.</span></span>  
  
3.  <span data-ttu-id="f9d71-113">Kliknij przycisk, który reprezentuje krawędzi formularz miejsce dock formantu.</span><span class="sxs-lookup"><span data-stu-id="f9d71-113">Click the button that represents the edge of the form where you want to dock the control.</span></span> <span data-ttu-id="f9d71-114">Aby wypełnić zawartość formantu formularza lub kontrolki kontenera, kliknij pole center.</span><span class="sxs-lookup"><span data-stu-id="f9d71-114">To fill the contents of the control's form or container control, click the center box.</span></span> <span data-ttu-id="f9d71-115">Kliknij przycisk **(Brak)** wyłączyć dokowania.</span><span class="sxs-lookup"><span data-stu-id="f9d71-115">Click **(none)** to disable docking.</span></span>  
  
     <span data-ttu-id="f9d71-116">Kontrolka jest automatycznie dopasowane granice zadokowane graniczny.</span><span class="sxs-lookup"><span data-stu-id="f9d71-116">The control is automatically resized to fit the boundaries of the docked edge.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f9d71-117">Formanty dziedziczone muszą być `Protected` mógł być zadokowany.</span><span class="sxs-lookup"><span data-stu-id="f9d71-117">Inherited controls must be `Protected` to be able to be docked.</span></span> <span data-ttu-id="f9d71-118">Aby zmienić poziom dostępu do formantu, ustaw jej **modyfikator** właściwości w oknie właściwości.</span><span class="sxs-lookup"><span data-stu-id="f9d71-118">To change the access level of a control, set its **Modifier** property in the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9d71-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9d71-119">See Also</span></span>  
 [<span data-ttu-id="f9d71-120">Kontrolki formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9d71-120">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="f9d71-121">Rozmieszczanie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9d71-121">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="f9d71-122">Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich</span><span class="sxs-lookup"><span data-stu-id="f9d71-122">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="f9d71-123">Kontrolki do użycia w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9d71-123">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="f9d71-124">Kontrolki formularzy Windows Forms według funkcji</span><span class="sxs-lookup"><span data-stu-id="f9d71-124">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [<span data-ttu-id="f9d71-125">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f9d71-125">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="f9d71-126">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f9d71-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="f9d71-127">AutoSize, właściwość — omówienie</span><span class="sxs-lookup"><span data-stu-id="f9d71-127">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [<span data-ttu-id="f9d71-128">Instrukcje: kotwiczenie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f9d71-128">How to: Anchor Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)
