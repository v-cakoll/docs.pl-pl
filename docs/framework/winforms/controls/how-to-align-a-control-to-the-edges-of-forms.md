---
title: "Porady: wyrównywanie formantu z krawędziami formularzy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dock property [Windows Forms], aligning controls (using code)
- forms [Windows Forms], aligning controls
- controls [Windows Forms], aligning on forms
- custom controls [Windows Forms], docking using code
ms.assetid: 5994cb59-242b-4e75-bd0e-62879c34d702
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a55212ac4d770848355ace1b0ef3fff3cc50f871
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a><span data-ttu-id="b5436-102">Porady: wyrównywanie formantu z krawędziami formularzy</span><span class="sxs-lookup"><span data-stu-id="b5436-102">How to: Align a Control to the Edges of Forms</span></span>
<span data-ttu-id="b5436-103">Umożliwia wyrównanie z krawędzią formularzy przez ustawienie formantu <xref:System.Windows.Forms.Control.Dock%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b5436-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="b5436-104">Ta właściwość określa, gdzie formantu znajduje się w formularzu.</span><span class="sxs-lookup"><span data-stu-id="b5436-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="b5436-105"><xref:System.Windows.Forms.Control.Dock%2A> Właściwość można ustawić następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="b5436-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="b5436-106">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="b5436-106">Setting</span></span>|<span data-ttu-id="b5436-107">Wpływ na formantu</span><span class="sxs-lookup"><span data-stu-id="b5436-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="b5436-108">Doków do dolnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="b5436-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="b5436-109">Kopiuje wszystkie pozostałe miejsce w formularzu.</span><span class="sxs-lookup"><span data-stu-id="b5436-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="b5436-110">Doków po lewej stronie formularza.</span><span class="sxs-lookup"><span data-stu-id="b5436-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="b5436-111">Czy nie dokowania z dowolnego miejsca i pojawia się w lokalizacji określonej przez jego <xref:System.Windows.Forms.Control.Location%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b5436-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="b5436-112">Doków z prawej strony formularza.</span><span class="sxs-lookup"><span data-stu-id="b5436-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="b5436-113">Doków do górnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="b5436-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="b5436-114">Brak obsługi tej funkcji w programie Visual Studio w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="b5436-114">There is design-time support for this feature in Visual Studio.</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-run-time"></a><span data-ttu-id="b5436-115">Aby ustawić właściwości Dock dla formantu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="b5436-115">To set the Dock property for your control at run time</span></span>  
  
1.  <span data-ttu-id="b5436-116">Ustaw <xref:System.Windows.Forms.Control.Dock%2A> na odpowiednią wartość w kodzie.</span><span class="sxs-lookup"><span data-stu-id="b5436-116">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to the appropriate value in code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b5436-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b5436-117">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="b5436-118">Opracowywanie niestandardowych formularzy systemu Windows formantów za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b5436-118">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="b5436-119">Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="b5436-119">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="b5436-120">Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="b5436-120">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="b5436-121">AutoSize — Przegląd właściwości</span><span class="sxs-lookup"><span data-stu-id="b5436-121">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)
