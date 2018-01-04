---
title: "Porady: wyrównywanie formantu z krawędziami formularzy w czasie projektowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3ca5f32d95ddaa2dac03ad55e2599bafe5af502f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a><span data-ttu-id="19b5b-102">Porady: wyrównywanie formantu z krawędziami formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="19b5b-102">How to: Align a Control to the Edges of Forms at Design Time</span></span>
<span data-ttu-id="19b5b-103">Umożliwia wyrównanie z krawędzią formularzy przez ustawienie formantu <xref:System.Windows.Forms.Control.Dock%2A>.</span><span class="sxs-lookup"><span data-stu-id="19b5b-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A>.</span></span> <span data-ttu-id="19b5b-104">Ta właściwość określa, gdzie formantu znajduje się w formularzu.</span><span class="sxs-lookup"><span data-stu-id="19b5b-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="19b5b-105"><xref:System.Windows.Forms.Control.Dock%2A> Właściwość można ustawić następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="19b5b-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>  
  
|<span data-ttu-id="19b5b-106">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="19b5b-106">Setting</span></span>|<span data-ttu-id="19b5b-107">Wpływ na formantu</span><span class="sxs-lookup"><span data-stu-id="19b5b-107">Effect on your control</span></span>|  
|-------------|----------------------------|  
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="19b5b-108">Doków do dolnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="19b5b-108">Docks to the bottom of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="19b5b-109">Kopiuje wszystkie pozostałe miejsce w formularzu.</span><span class="sxs-lookup"><span data-stu-id="19b5b-109">Fills all remaining space in the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="19b5b-110">Doków po lewej stronie formularza.</span><span class="sxs-lookup"><span data-stu-id="19b5b-110">Docks to the left side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="19b5b-111">Czy nie dokowania z dowolnego miejsca i pojawia się w lokalizacji określonej przez jego <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="19b5b-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A>.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="19b5b-112">Doków z prawej strony formularza.</span><span class="sxs-lookup"><span data-stu-id="19b5b-112">Docks to the right side of the form.</span></span>|  
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="19b5b-113">Doków do górnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="19b5b-113">Docks to the top of the form.</span></span>|  
  
 <span data-ttu-id="19b5b-114">Te wartości można również ustawić w kodzie.</span><span class="sxs-lookup"><span data-stu-id="19b5b-114">These values can also be set in code.</span></span> <span data-ttu-id="19b5b-115">Aby uzyskać więcej informacji, zobacz [porady: wyrównywanie formantu z krawędziami formularzy](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md).</span><span class="sxs-lookup"><span data-stu-id="19b5b-115">For more information, see [How to: Align a Control to the Edges of Forms](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19b5b-116">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="19b5b-116">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="19b5b-117">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="19b5b-117">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="19b5b-118">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="19b5b-118">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-set-the-dock-property-for-your-control-at-design-time"></a><span data-ttu-id="19b5b-119">Aby ustawić właściwości Dock dla formantu w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="19b5b-119">To set the Dock property for your control at design time</span></span>  
  
1.  <span data-ttu-id="19b5b-120">W narzędziu Projektant dla formularzy systemu Windows wybierz formantu.</span><span class="sxs-lookup"><span data-stu-id="19b5b-120">In the Windows Forms Designer, select your control.</span></span>  
  
2.  <span data-ttu-id="19b5b-121">W **właściwości** , kliknij listę rozwijaną pola obok <xref:System.Windows.Forms.Control.Dock%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="19b5b-121">In the **Properties** window, click the drop-down box next to the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>  
  
     <span data-ttu-id="19b5b-122">Graficzny interfejs reprezentujący sześciu możliwe <xref:System.Windows.Forms.Control.Dock%2A> wyświetlane ustawienia.</span><span class="sxs-lookup"><span data-stu-id="19b5b-122">A graphical interface representing the six possible <xref:System.Windows.Forms.Control.Dock%2A> settings is displayed.</span></span>  
  
3.  <span data-ttu-id="19b5b-123">Wybierz odpowiednie ustawienie.</span><span class="sxs-lookup"><span data-stu-id="19b5b-123">Choose the appropriate setting.</span></span>  
  
4.  <span data-ttu-id="19b5b-124">Formant będzie teraz dock w sposób określony przez ustawienie.</span><span class="sxs-lookup"><span data-stu-id="19b5b-124">Your control will now dock in the manner specified by the setting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19b5b-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19b5b-125">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="19b5b-126">Instrukcje: wyrównywanie kontrolki z krawędziami formularzy</span><span class="sxs-lookup"><span data-stu-id="19b5b-126">How to: Align a Control to the Edges of Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms.md)  
 [<span data-ttu-id="19b5b-127">Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="19b5b-127">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [<span data-ttu-id="19b5b-128">Instrukcje: kotwiczenie kontrolek na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19b5b-128">How to: Anchor Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-controls-on-windows-forms.md)  
 [<span data-ttu-id="19b5b-129">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="19b5b-129">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [<span data-ttu-id="19b5b-130">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="19b5b-130">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)  
 [<span data-ttu-id="19b5b-131">Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="19b5b-131">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="19b5b-132">Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="19b5b-132">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="19b5b-133">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="19b5b-133">Developing Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)
