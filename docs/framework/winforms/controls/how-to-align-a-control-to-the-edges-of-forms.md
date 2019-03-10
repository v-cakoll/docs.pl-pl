---
title: 'Instrukcje: Wyrównywanie formantu z krawędziami formularzy'
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
ms.openlocfilehash: 33a3b2e996bdab280eb7a4cd8ad7c59ccb1a1bd2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713894"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a><span data-ttu-id="1c7bf-102">Instrukcje: Wyrównywanie formantu z krawędziami formularzy</span><span class="sxs-lookup"><span data-stu-id="1c7bf-102">How to: Align a Control to the Edges of Forms</span></span>
<span data-ttu-id="1c7bf-103">Ułatwia kontrolki wyrównane do krawędzi formularzy, ustawiając <xref:System.Windows.Forms.Control.Dock%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1c7bf-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="1c7bf-104">Ta właściwość wskazuje, której formant znajduje się w formularzu.</span><span class="sxs-lookup"><span data-stu-id="1c7bf-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="1c7bf-105"><xref:System.Windows.Forms.Control.Dock%2A> Właściwość można ustawić następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="1c7bf-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="1c7bf-106">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="1c7bf-106">Setting</span></span>|<span data-ttu-id="1c7bf-107">Wpływ na Twoją kontrolą</span><span class="sxs-lookup"><span data-stu-id="1c7bf-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="1c7bf-108">Doków do dolnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="1c7bf-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="1c7bf-109">Wypełnia całe pozostałe miejsce w formularzu.</span><span class="sxs-lookup"><span data-stu-id="1c7bf-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="1c7bf-110">Doków do lewej części formularza.</span><span class="sxs-lookup"><span data-stu-id="1c7bf-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="1c7bf-111">Czy nie Zadokuj z dowolnego miejsca i pojawia się w lokalizacji określonej przez jego <xref:System.Windows.Forms.Control.Location%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1c7bf-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="1c7bf-112">Doków prawą stronę formularza.</span><span class="sxs-lookup"><span data-stu-id="1c7bf-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="1c7bf-113">Doków do górnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="1c7bf-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="1c7bf-114">Brak obsługi w czasie projektowania dla tej funkcji w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1c7bf-114">There is design-time support for this feature in Visual Studio.</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-run-time"></a><span data-ttu-id="1c7bf-115">Aby ustawić właściwość dokowania dla formantu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="1c7bf-115">To set the Dock property for your control at run time</span></span>  
  
1.  <span data-ttu-id="1c7bf-116">Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość odpowiednią wartość w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1c7bf-116">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to the appropriate value in code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1c7bf-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c7bf-117">See also</span></span>
- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1c7bf-118">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1c7bf-118">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="1c7bf-119">Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1c7bf-119">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="1c7bf-120">Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1c7bf-120">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="1c7bf-121">AutoSize, właściwość — omówienie</span><span class="sxs-lookup"><span data-stu-id="1c7bf-121">AutoSize Property Overview</span></span>](autosize-property-overview.md)
