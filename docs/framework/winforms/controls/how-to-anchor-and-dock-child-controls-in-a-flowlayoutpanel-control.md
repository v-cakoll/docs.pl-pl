---
title: 'Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel'
description: Dowiedz się, jak programowo zakotwiczać i dokować kontrolki podrzędne w Windows Forms formancie FlowLayoutPanel.
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: b4fb3bf6d148a526a75926bd67c1f967286332bf
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174539"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="70d93-103">Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="70d93-103">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>

<span data-ttu-id="70d93-104"><xref:System.Windows.Forms.FlowLayoutPanel>Kontrolka obsługuje <xref:System.Windows.Forms.Control.Anchor%2A> właściwości i <xref:System.Windows.Forms.Control.Dock%2A> w jego kontrolkach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="70d93-104">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>

### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="70d93-105">Aby zakotwiczyć i zadokować kontrolki podrzędne w kontrolce FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="70d93-105">To anchor and dock child controls in a FlowLayoutPanel control</span></span>

1. <span data-ttu-id="70d93-106">Utwórz <xref:System.Windows.Forms.FlowLayoutPanel> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="70d93-106">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>

2. <span data-ttu-id="70d93-107">Ustaw wartość <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki na **300**, a następnie ustaw jej wartość <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> na <xref:System.Windows.Forms.FlowDirection.TopDown> .</span><span class="sxs-lookup"><span data-stu-id="70d93-107">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>

3. <span data-ttu-id="70d93-108">Utwórz dwie <xref:System.Windows.Forms.Button> kontrolki i umieść je w <xref:System.Windows.Forms.FlowLayoutPanel> kontrolce.</span><span class="sxs-lookup"><span data-stu-id="70d93-108">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

4. <span data-ttu-id="70d93-109">Ustaw wartość <xref:System.Windows.Forms.Control.Width%2A> pierwszego przycisku na **200**.</span><span class="sxs-lookup"><span data-stu-id="70d93-109">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>

5. <span data-ttu-id="70d93-110">Ustaw <xref:System.Windows.Forms.Control.Dock%2A> Właściwość drugiego przycisku na <xref:System.Windows.Forms.DockStyle.Fill> .</span><span class="sxs-lookup"><span data-stu-id="70d93-110">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="70d93-111">Drugi przycisk przyjmuje taką samą szerokość jak pierwszy przycisk.</span><span class="sxs-lookup"><span data-stu-id="70d93-111">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="70d93-112">Nie rozciąga się na szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="70d93-112">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

6. <span data-ttu-id="70d93-113">Ustaw <xref:System.Windows.Forms.Control.Dock%2A> Właściwość drugiego przycisku na `None` .</span><span class="sxs-lookup"><span data-stu-id="70d93-113">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="70d93-114">Spowoduje to, że przycisk przyjmie oryginalną szerokość.</span><span class="sxs-lookup"><span data-stu-id="70d93-114">This causes the button to assume its original width.</span></span>

7. <span data-ttu-id="70d93-115">Ustaw <xref:System.Windows.Forms.Control.Anchor%2A> Właściwość drugiego przycisku na `Left, Right` .</span><span class="sxs-lookup"><span data-stu-id="70d93-115">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="70d93-116">Drugi przycisk przyjmuje taką samą szerokość jak pierwszy przycisk.</span><span class="sxs-lookup"><span data-stu-id="70d93-116">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="70d93-117">Nie rozciąga się na szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="70d93-117">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="70d93-118">Jest to ogólna reguła zakotwiczenia i dokowania w <xref:System.Windows.Forms.FlowLayoutPanel> kontrolce: dla pionowych kierunków przepływu <xref:System.Windows.Forms.FlowLayoutPanel> kontrolka oblicza szerokość kolumny implikowanej z najszerszej kontrolki podrzędnej w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="70d93-118">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="70d93-119">Wszystkie inne kontrolki w tej kolumnie z <xref:System.Windows.Forms.Control.Anchor%2A> lub <xref:System.Windows.Forms.Control.Dock%2A> właściwości są wyrównane lub rozciągane w celu dopasowania do tej kolumny implikowanej.</span><span class="sxs-lookup"><span data-stu-id="70d93-119">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="70d93-120">Zachowanie działa podobnie do poziomych kierunków przepływu.</span><span class="sxs-lookup"><span data-stu-id="70d93-120">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="70d93-121"><xref:System.Windows.Forms.FlowLayoutPanel>Kontrolka oblicza wysokość implikowanego wiersza z najwyższego poziomu kontrolki podrzędnej w wierszu, a wszystkie kontrolki podrzędne zadokowane lub zakotwiczone w tym wierszu są wyrównane lub skalowane, aby dopasować implikowany wiersz.</span><span class="sxs-lookup"><span data-stu-id="70d93-121">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>

## <a name="example"></a><span data-ttu-id="70d93-122">Przykład</span><span class="sxs-lookup"><span data-stu-id="70d93-122">Example</span></span>

<span data-ttu-id="70d93-123">Na poniższej ilustracji przedstawiono cztery przyciski zakotwiczone i zadokowane względem niebieskiego przycisku w <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="70d93-123">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="70d93-124"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>Ma wartość <xref:System.Windows.Forms.FlowDirection.LeftToRight> .</span><span class="sxs-lookup"><span data-stu-id="70d93-124">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>

<span data-ttu-id="70d93-125">![Zakotwiczenie FlowLayoutPanel](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="70d93-125">![FlowLayoutPanel anchoring](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>

<span data-ttu-id="70d93-126">Na poniższej ilustracji przedstawiono cztery przyciski zakotwiczone i zadokowane względem niebieskiego przycisku w <xref:System.Windows.Forms.FlowLayoutPanel> .</span><span class="sxs-lookup"><span data-stu-id="70d93-126">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="70d93-127"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>Ma wartość <xref:System.Windows.Forms.FlowDirection.TopDown> .</span><span class="sxs-lookup"><span data-stu-id="70d93-127">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>

<span data-ttu-id="70d93-128">![Zakotwiczenie FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="70d93-128">![FlowLayoutPanel anchoring](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>

<span data-ttu-id="70d93-129">Poniższy przykład kodu demonstruje różne <xref:System.Windows.Forms.Control.Anchor%2A> wartości właściwości <xref:System.Windows.Forms.Button> kontrolki w <xref:System.Windows.Forms.FlowLayoutPanel> kontrolce.</span><span class="sxs-lookup"><span data-stu-id="70d93-129">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>

[!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
[!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]

## <a name="compiling-the-code"></a><span data-ttu-id="70d93-130">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="70d93-130">Compiling the Code</span></span>

<span data-ttu-id="70d93-131">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="70d93-131">This example requires:</span></span>

- <span data-ttu-id="70d93-132">Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="70d93-132">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="70d93-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="70d93-133">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="70d93-134">FlowLayoutPanel — Informacje o formancie</span><span class="sxs-lookup"><span data-stu-id="70d93-134">FlowLayoutPanel Control Overview</span></span>](flowlayoutpanel-control-overview.md)
