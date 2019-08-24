---
title: 'Instrukcje: wyrównywanie kontrolki z krawędziami formularzy'
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
ms.openlocfilehash: 5d662489b7e31f391bbd508409e69c091a25592c
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015948"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms"></a><span data-ttu-id="bfb23-102">Instrukcje: wyrównywanie kontrolki z krawędziami formularzy</span><span class="sxs-lookup"><span data-stu-id="bfb23-102">How to: Align a Control to the Edges of Forms</span></span>

<span data-ttu-id="bfb23-103">Formant można dostosować do krawędzi formularza przez ustawienie <xref:System.Windows.Forms.Control.Dock%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bfb23-103">You can make your control align to the edge of your forms by setting the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="bfb23-104">Ta właściwość określa, gdzie znajduje się kontrolka w formularzu.</span><span class="sxs-lookup"><span data-stu-id="bfb23-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="bfb23-105"><xref:System.Windows.Forms.Control.Dock%2A> Właściwość można ustawić na następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="bfb23-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>

|<span data-ttu-id="bfb23-106">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="bfb23-106">Setting</span></span>|<span data-ttu-id="bfb23-107">Wpływ na kontrolkę</span><span class="sxs-lookup"><span data-stu-id="bfb23-107">Effect on your control</span></span>|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="bfb23-108">Dokowanie w dolnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="bfb23-108">Docks to the bottom of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="bfb23-109">Wypełnia wszystkie pozostałe miejsca w formularzu.</span><span class="sxs-lookup"><span data-stu-id="bfb23-109">Fills all remaining space in the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="bfb23-110">Dokowanie po lewej stronie formularza.</span><span class="sxs-lookup"><span data-stu-id="bfb23-110">Docks to the left side of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="bfb23-111">Nie jest zadokowane w dowolnym miejscu i pojawia się w lokalizacji określonej przez <xref:System.Windows.Forms.Control.Location%2A> jej właściwość.</span><span class="sxs-lookup"><span data-stu-id="bfb23-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A> property.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="bfb23-112">Dokowanie po prawej stronie formularza.</span><span class="sxs-lookup"><span data-stu-id="bfb23-112">Docks to the right side of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="bfb23-113">Dockuje w górnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="bfb23-113">Docks to the top of the form.</span></span>|

<span data-ttu-id="bfb23-114">Dla tej funkcji w programie Visual Studio jest obsługiwana obsługa czasu projektowania.</span><span class="sxs-lookup"><span data-stu-id="bfb23-114">There is design-time support for this feature in Visual Studio.</span></span>

## <a name="set-the-dock-property-for-your-control-at-run-time"></a><span data-ttu-id="bfb23-115">Ustaw właściwość Dock dla kontrolki w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="bfb23-115">Set the Dock property for your control at run time</span></span>

<span data-ttu-id="bfb23-116"><xref:System.Windows.Forms.Control.Dock%2A> Ustaw właściwość na odpowiednią wartość w kodzie.</span><span class="sxs-lookup"><span data-stu-id="bfb23-116">Set the <xref:System.Windows.Forms.Control.Dock%2A> property to the appropriate value in code.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bfb23-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bfb23-117">See also</span></span>

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bfb23-118">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="bfb23-118">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="bfb23-119">Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w kontrolce FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="bfb23-119">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="bfb23-120">Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="bfb23-120">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="bfb23-121">AutoSize, właściwość — omówienie</span><span class="sxs-lookup"><span data-stu-id="bfb23-121">AutoSize Property Overview</span></span>](autosize-property-overview.md)
