---
title: 'Porady: wyrównywanie formantu z krawędziami formularzy'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
ms.openlocfilehash: a8571f668de2714511a8732772443a8897043cf2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a><span data-ttu-id="479ed-102">Porady: wyrównywanie formantu z krawędziami formularzy</span><span class="sxs-lookup"><span data-stu-id="479ed-102">How to: Align a Control to the Edges of Forms</span></span>
<span data-ttu-id="479ed-103">Umożliwia wyrównanie z krawędzią formularzy przez ustawienie formantu <xref:System.Windows.Forms.Control.Dock%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="479ed-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="479ed-104">Ta właściwość określa, gdzie formantu znajduje się w formularzu.</span><span class="sxs-lookup"><span data-stu-id="479ed-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="479ed-105"><xref:System.Windows.Forms.Control.Dock%2A> Właściwość można ustawić następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="479ed-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="479ed-106">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="479ed-106">Setting</span></span>|<span data-ttu-id="479ed-107">Wpływ na formantu</span><span class="sxs-lookup"><span data-stu-id="479ed-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="479ed-108">Doków do dolnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="479ed-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="479ed-109">Kopiuje wszystkie pozostałe miejsce w formularzu.</span><span class="sxs-lookup"><span data-stu-id="479ed-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="479ed-110">Doków po lewej stronie formularza.</span><span class="sxs-lookup"><span data-stu-id="479ed-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="479ed-111">Czy nie dokowania z dowolnego miejsca i pojawia się w lokalizacji określonej przez jego <xref:System.Windows.Forms.Control.Location%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="479ed-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="479ed-112">Doków z prawej strony formularza.</span><span class="sxs-lookup"><span data-stu-id="479ed-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="479ed-113">Doków do górnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="479ed-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="479ed-114">Brak obsługi tej funkcji w programie Visual Studio w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="479ed-114">There is design-time support for this feature in Visual Studio.</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-run-time"></a><span data-ttu-id="479ed-115">Aby ustawić właściwości Dock dla formantu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="479ed-115">To set the Dock property for your control at run time</span></span>  
  
1.  <span data-ttu-id="479ed-116">Ustaw <xref:System.Windows.Forms.Control.Dock%2A> na odpowiednią wartość w kodzie.</span><span class="sxs-lookup"><span data-stu-id="479ed-116">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to the appropriate value in code.</span></span>  
  
    ```vb  
    ' To set the Dock property internally.  
    Me.Dock = DockStyle.Top  
    ' To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top  
    ```  
  
    ```csharp  
    // To set the Dock property internally.  
    this.Dock = DockStyle.Top;  
    // To set the Dock property from another object.  
    UserControl1.Dock = DockStyle.Top;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="479ed-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="479ed-117">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="479ed-118">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="479ed-118">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="479ed-119">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="479ed-119">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="479ed-120">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="479ed-120">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="479ed-121">AutoSize, właściwość — omówienie</span><span class="sxs-lookup"><span data-stu-id="479ed-121">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)
