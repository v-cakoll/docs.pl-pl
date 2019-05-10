---
title: 'Instrukcje: wyrównywanie kontrolki z krawędziami formularzy w czasie projektowania'
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], docking using designer
- Dock property [Windows Forms], aligning controls (using designer)
ms.assetid: 51f08998-5e3b-4330-be58-a4edd0eb60f4
ms.openlocfilehash: b08e01eb9adb984a32a8fc435cf1f3b93b159a14
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210382"
---
# <a name="how-to-align-a-control-to-the-edges-of-forms-at-design-time"></a><span data-ttu-id="ac0db-102">Instrukcje: wyrównywanie kontrolki z krawędziami formularzy w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="ac0db-102">How to: Align a Control to the Edges of Forms at Design Time</span></span>

<span data-ttu-id="ac0db-103">Umożliwia wyrównanie krawędzi formularzy, ustawiając wartość kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ac0db-103">You can make your control align to the edge of your forms by setting the value of the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span> <span data-ttu-id="ac0db-104">Ta właściwość wskazuje, której formant znajduje się w formularzu.</span><span class="sxs-lookup"><span data-stu-id="ac0db-104">This property designates where your control resides in the form.</span></span> <span data-ttu-id="ac0db-105"><xref:System.Windows.Forms.Control.Dock%2A> Właściwość można ustawić następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="ac0db-105">The <xref:System.Windows.Forms.Control.Dock%2A> property can be set to the following values:</span></span>

|<span data-ttu-id="ac0db-106">Ustawienie</span><span class="sxs-lookup"><span data-stu-id="ac0db-106">Setting</span></span>|<span data-ttu-id="ac0db-107">Wpływ na Twoją kontrolą</span><span class="sxs-lookup"><span data-stu-id="ac0db-107">Effect on your control</span></span>|
|-------------|----------------------------|
|<xref:System.Windows.Forms.DockStyle.Bottom>|<span data-ttu-id="ac0db-108">Doków do dolnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="ac0db-108">Docks to the bottom of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Fill>|<span data-ttu-id="ac0db-109">Wypełnia całe pozostałe miejsce w formularzu.</span><span class="sxs-lookup"><span data-stu-id="ac0db-109">Fills all remaining space in the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Left>|<span data-ttu-id="ac0db-110">Doków do lewej części formularza.</span><span class="sxs-lookup"><span data-stu-id="ac0db-110">Docks to the left side of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.None>|<span data-ttu-id="ac0db-111">Czy nie Zadokuj z dowolnego miejsca i pojawia się w lokalizacji określonej przez jego <xref:System.Windows.Forms.Control.Location%2A>.</span><span class="sxs-lookup"><span data-stu-id="ac0db-111">Does not dock anywhere, and it appears at the location specified by its <xref:System.Windows.Forms.Control.Location%2A>.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Right>|<span data-ttu-id="ac0db-112">Doków prawą stronę formularza.</span><span class="sxs-lookup"><span data-stu-id="ac0db-112">Docks to the right side of the form.</span></span>|
|<xref:System.Windows.Forms.DockStyle.Top>|<span data-ttu-id="ac0db-113">Doków do górnej części formularza.</span><span class="sxs-lookup"><span data-stu-id="ac0db-113">Docks to the top of the form.</span></span>|

<span data-ttu-id="ac0db-114">Wartości te można ustawić w taki sposób, w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ac0db-114">These values can also be set in code.</span></span> <span data-ttu-id="ac0db-115">Aby uzyskać więcej informacji, zobacz [jak: Wyrównywanie formantu z krawędziami formularzy](how-to-align-a-control-to-the-edges-of-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ac0db-115">For more information, see [How to: Align a Control to the Edges of Forms](how-to-align-a-control-to-the-edges-of-forms.md).</span></span>

## <a name="set-the-dock-property-for-your-control-at-design-time"></a><span data-ttu-id="ac0db-116">Ustaw właściwość dokowania dla formantu w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="ac0db-116">Set the Dock property for your control at design time</span></span>

1. <span data-ttu-id="ac0db-117">W Projektancie Windows Forms w programie Visual Studio wybierz formant.</span><span class="sxs-lookup"><span data-stu-id="ac0db-117">In the Windows Forms Designer in Visual Studio, select your control.</span></span>

2. <span data-ttu-id="ac0db-118">W **właściwości** , kliknij listę rozwijaną pola obok <xref:System.Windows.Forms.Control.Dock%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ac0db-118">In the **Properties** window, click the drop-down box next to the <xref:System.Windows.Forms.Control.Dock%2A> property.</span></span>

     <span data-ttu-id="ac0db-119">Graficzny interfejs reprezentujący sześć najbardziej <xref:System.Windows.Forms.Control.Dock%2A> wyświetlane ustawienia.</span><span class="sxs-lookup"><span data-stu-id="ac0db-119">A graphical interface representing the six possible <xref:System.Windows.Forms.Control.Dock%2A> settings is displayed.</span></span>

3. <span data-ttu-id="ac0db-120">Wybierz odpowiednie ustawienie.</span><span class="sxs-lookup"><span data-stu-id="ac0db-120">Choose the appropriate setting.</span></span>

4. <span data-ttu-id="ac0db-121">Formant teraz zostanie zadokowany w sposób określony w ustawieniu.</span><span class="sxs-lookup"><span data-stu-id="ac0db-121">Your control will now dock in the manner specified by the setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="ac0db-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ac0db-122">See also</span></span>

- <xref:System.Windows.Forms.Control.Dock%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.Anchor%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ac0db-123">Instrukcje: Wyrównywanie formantu z krawędziami formularzy</span><span class="sxs-lookup"><span data-stu-id="ac0db-123">How to: Align a Control to the Edges of Forms</span></span>](how-to-align-a-control-to-the-edges-of-forms.md)
- [<span data-ttu-id="ac0db-124">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania</span><span class="sxs-lookup"><span data-stu-id="ac0db-124">Walkthrough: Arranging Controls on Windows Forms Using Snaplines</span></span>](walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)
- [<span data-ttu-id="ac0db-125">Instrukcje: Zakotwiczenia formantów na formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ac0db-125">How to: Anchor Controls on Windows Forms</span></span>](how-to-anchor-controls-on-windows-forms.md)
- [<span data-ttu-id="ac0db-126">Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ac0db-126">How to: Anchor and Dock Child Controls in a TableLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [<span data-ttu-id="ac0db-127">Instrukcje: Zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ac0db-127">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>](how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control.md)
- [<span data-ttu-id="ac0db-128">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ac0db-128">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="ac0db-129">Przewodnik: Rozmieszczanie kontrolek na formularzach Windows Forms za pomocą FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="ac0db-129">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="ac0db-130">Opracowywanie kontrolek formularzy Windows Forms w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="ac0db-130">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
