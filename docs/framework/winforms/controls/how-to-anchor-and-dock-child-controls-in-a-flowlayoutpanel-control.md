---
title: 'Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce FlowLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: 9a00fcd53211dd126c0e9203d6d577959b971e70
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922907"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="2bd80-102">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2bd80-102">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>
<span data-ttu-id="2bd80-103">Kontrolka obsługuje właściwości <xref:System.Windows.Forms.Control.Dock%2A> i w jego kontrolkach podrzędnych. <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.FlowLayoutPanel></span><span class="sxs-lookup"><span data-stu-id="2bd80-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="2bd80-104">Aby zakotwiczyć i zadokować kontrolki podrzędne w kontrolce FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="2bd80-104">To anchor and dock child controls in a FlowLayoutPanel control</span></span>  
  
1. <span data-ttu-id="2bd80-105"><xref:System.Windows.Forms.FlowLayoutPanel> Utwórz kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="2bd80-105">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>  
  
2. <span data-ttu-id="2bd80-106"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> <xref:System.Windows.Forms.FlowDirection.TopDown>Ustaw wartość kontrolkina300,anastępnieustawjejwartośćna.<xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.Control.Width%2A></span><span class="sxs-lookup"><span data-stu-id="2bd80-106">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
3. <span data-ttu-id="2bd80-107">Utwórz dwie <xref:System.Windows.Forms.Button> kontrolki i umieść je <xref:System.Windows.Forms.FlowLayoutPanel> w kontrolce.</span><span class="sxs-lookup"><span data-stu-id="2bd80-107">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
4. <span data-ttu-id="2bd80-108">Ustaw wartość pierwszego przycisku na 200. <xref:System.Windows.Forms.Control.Width%2A></span><span class="sxs-lookup"><span data-stu-id="2bd80-108">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>  
  
5. <span data-ttu-id="2bd80-109">Ustaw właściwość drugiego przycisku na <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Control.Dock%2A></span><span class="sxs-lookup"><span data-stu-id="2bd80-109">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="2bd80-110">Drugi przycisk przyjmuje taką samą szerokość jak pierwszy przycisk.</span><span class="sxs-lookup"><span data-stu-id="2bd80-110">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="2bd80-111">Nie rozciąga się na szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="2bd80-111">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6. <span data-ttu-id="2bd80-112">Ustaw właściwość drugiego przycisku na `None`. <xref:System.Windows.Forms.Control.Dock%2A></span><span class="sxs-lookup"><span data-stu-id="2bd80-112">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="2bd80-113">Spowoduje to, że przycisk przyjmie oryginalną szerokość.</span><span class="sxs-lookup"><span data-stu-id="2bd80-113">This causes the button to assume its original width.</span></span>  
  
7. <span data-ttu-id="2bd80-114">Ustaw właściwość drugiego przycisku na `Left, Right`. <xref:System.Windows.Forms.Control.Anchor%2A></span><span class="sxs-lookup"><span data-stu-id="2bd80-114">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="2bd80-115">Drugi przycisk przyjmuje taką samą szerokość jak pierwszy przycisk.</span><span class="sxs-lookup"><span data-stu-id="2bd80-115">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="2bd80-116">Nie rozciąga się na szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki.</span><span class="sxs-lookup"><span data-stu-id="2bd80-116">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="2bd80-117">Jest to ogólna reguła zakotwiczenia i dokowania w <xref:System.Windows.Forms.FlowLayoutPanel> kontrolce: dla pionowych kierunków <xref:System.Windows.Forms.FlowLayoutPanel> przepływu kontrolka oblicza szerokość kolumny implikowanej z najszerszej kontrolki podrzędnej w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="2bd80-117">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="2bd80-118">Wszystkie inne kontrolki w tej kolumnie <xref:System.Windows.Forms.Control.Anchor%2A> z <xref:System.Windows.Forms.Control.Dock%2A> lub właściwości są wyrównane lub rozciągane w celu dopasowania do tej kolumny implikowanej.</span><span class="sxs-lookup"><span data-stu-id="2bd80-118">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="2bd80-119">Zachowanie działa podobnie do poziomych kierunków przepływu.</span><span class="sxs-lookup"><span data-stu-id="2bd80-119">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="2bd80-120"><xref:System.Windows.Forms.FlowLayoutPanel> Kontrolka oblicza wysokość implikowanego wiersza z najwyższego poziomu kontrolki podrzędnej w wierszu, a wszystkie kontrolki podrzędne zadokowane lub zakotwiczone w tym wierszu są wyrównane lub skalowane, aby dopasować implikowany wiersz.</span><span class="sxs-lookup"><span data-stu-id="2bd80-120">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2bd80-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="2bd80-121">Example</span></span>  
 <span data-ttu-id="2bd80-122">Na poniższej ilustracji przedstawiono cztery przyciski zakotwiczone i zadokowane względem niebieskiego przycisku w <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="2bd80-122">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="2bd80-123"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Ma<xref:System.Windows.Forms.FlowDirection.LeftToRight>wartość.</span><span class="sxs-lookup"><span data-stu-id="2bd80-123">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>  
  
 <span data-ttu-id="2bd80-124">![Zakotwiczenie FlowLayoutPanel](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="2bd80-124">![FlowLayoutPanel anchoring](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>  
  
 <span data-ttu-id="2bd80-125">Na poniższej ilustracji przedstawiono cztery przyciski zakotwiczone i zadokowane względem niebieskiego przycisku w <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="2bd80-125">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="2bd80-126"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Ma<xref:System.Windows.Forms.FlowDirection.TopDown>wartość.</span><span class="sxs-lookup"><span data-stu-id="2bd80-126">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
 <span data-ttu-id="2bd80-127">![Zakotwiczenie FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="2bd80-127">![FlowLayoutPanel anchoring](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>  
  
 <span data-ttu-id="2bd80-128">Poniższy przykład kodu demonstruje różne <xref:System.Windows.Forms.Control.Anchor%2A> wartości <xref:System.Windows.Forms.Button> właściwości kontrolki w <xref:System.Windows.Forms.FlowLayoutPanel> kontrolce.</span><span class="sxs-lookup"><span data-stu-id="2bd80-128">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2bd80-129">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2bd80-129">Compiling the Code</span></span>  
 <span data-ttu-id="2bd80-130">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="2bd80-130">This example requires:</span></span>  
  
- <span data-ttu-id="2bd80-131">Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="2bd80-131">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bd80-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2bd80-132">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="2bd80-133">FlowLayoutPanel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="2bd80-133">FlowLayoutPanel Control Overview</span></span>](flowlayoutpanel-control-overview.md)
