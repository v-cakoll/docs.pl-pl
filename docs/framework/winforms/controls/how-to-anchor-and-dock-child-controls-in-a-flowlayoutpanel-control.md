---
title: 'Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce FlowLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: 255ac50ae79d6931c9b82b50677c450c0834fdea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011196"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="21bda-102">Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="21bda-102">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>
<span data-ttu-id="21bda-103"><xref:System.Windows.Forms.FlowLayoutPanel> Kontrolować obsługuje <xref:System.Windows.Forms.Control.Anchor%2A> i <xref:System.Windows.Forms.Control.Dock%2A> właściwości w jego formantów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="21bda-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="21bda-104">Aby zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="21bda-104">To anchor and dock child controls in a FlowLayoutPanel control</span></span>  
  
1. <span data-ttu-id="21bda-105">Utwórz <xref:System.Windows.Forms.FlowLayoutPanel> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="21bda-105">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>  
  
2. <span data-ttu-id="21bda-106">Ustaw <xref:System.Windows.Forms.Control.Width%2A> z <xref:System.Windows.Forms.FlowLayoutPanel> kontrolę **300**i ustaw jego <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> do <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="21bda-106">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
3. <span data-ttu-id="21bda-107">Utworzyć dwa <xref:System.Windows.Forms.Button> kontroluje i umieść je w <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="21bda-107">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
4. <span data-ttu-id="21bda-108">Ustaw <xref:System.Windows.Forms.Control.Width%2A> pierwszego przycisku, aby **200**.</span><span class="sxs-lookup"><span data-stu-id="21bda-108">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>  
  
5. <span data-ttu-id="21bda-109">Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość drugi przycisk, który <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="21bda-109">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="21bda-110">Drugi przycisk zakłada taką samą szerokość jako pierwszy przycisk.</span><span class="sxs-lookup"><span data-stu-id="21bda-110">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="21bda-111">Nie rozciągnąć na szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="21bda-111">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6. <span data-ttu-id="21bda-112">Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość drugi przycisk, który `None`.</span><span class="sxs-lookup"><span data-stu-id="21bda-112">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="21bda-113">To powoduje, że przycisk założył, jego oryginalna szerokość.</span><span class="sxs-lookup"><span data-stu-id="21bda-113">This causes the button to assume its original width.</span></span>  
  
7. <span data-ttu-id="21bda-114">Ustaw <xref:System.Windows.Forms.Control.Anchor%2A> właściwość drugi przycisk, który `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="21bda-114">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="21bda-115">Drugi przycisk zakłada taką samą szerokość jako pierwszy przycisk.</span><span class="sxs-lookup"><span data-stu-id="21bda-115">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="21bda-116">Nie rozciągnąć na szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="21bda-116">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="21bda-117">To ogólne reguły dla Zakotwiczanie i dokowanie w <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki: w kierunkach pionowy przepływu <xref:System.Windows.Forms.FlowLayoutPanel> kontroli oblicza szerokość kolumny dorozumianych z najszerszej kontrolki podrzędnej w kolumnie.</span><span class="sxs-lookup"><span data-stu-id="21bda-117">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="21bda-118">Wszystkie kontrolki w tej kolumnie, za pomocą <xref:System.Windows.Forms.Control.Anchor%2A> lub <xref:System.Windows.Forms.Control.Dock%2A> właściwości są wyrównane, czy rozciągnięte do mieści się w tej kolumnie dorozumianych.</span><span class="sxs-lookup"><span data-stu-id="21bda-118">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="21bda-119">Zachowanie działa w podobny sposób jak w poziomie przepływu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="21bda-119">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="21bda-120"><xref:System.Windows.Forms.FlowLayoutPanel> Kontroli oblicza wysokość wiersza dorozumianych od najwyższego kontrolki podrzędnej w wierszu i wszystkich kontrolek podrzędnych zadokowany lub zakotwiczone w tym wierszu są wyrównane lub dopasowana dorozumianych wiersza.</span><span class="sxs-lookup"><span data-stu-id="21bda-120">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="21bda-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="21bda-121">Example</span></span>  
 <span data-ttu-id="21bda-122">Na poniższej ilustracji przedstawiono cztery przyciski, które są zakotwiczone zadokowane względem niebieski przycisk w <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="21bda-122">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="21bda-123"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Jest <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span><span class="sxs-lookup"><span data-stu-id="21bda-123">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>  
  
 <span data-ttu-id="21bda-124">![FlowLayoutPanel anchoring](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="21bda-124">![FlowLayoutPanel anchoring](./media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>  
  
 <span data-ttu-id="21bda-125">Na poniższej ilustracji przedstawiono cztery przyciski, które są zakotwiczone zadokowane względem niebieski przycisk w <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="21bda-125">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="21bda-126"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Jest <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="21bda-126">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
 <span data-ttu-id="21bda-127">![Formantu FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="21bda-127">![FlowLayoutPanel anchoring](./media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>  
  
 <span data-ttu-id="21bda-128">Poniższy przykład kodu demonstruje różne <xref:System.Windows.Forms.Control.Anchor%2A> wartości właściwości <xref:System.Windows.Forms.Button> w kontrolce <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.</span><span class="sxs-lookup"><span data-stu-id="21bda-128">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="21bda-129">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="21bda-129">Compiling the Code</span></span>  
 <span data-ttu-id="21bda-130">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="21bda-130">This example requires:</span></span>  
  
- <span data-ttu-id="21bda-131">Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="21bda-131">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="21bda-132">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="21bda-132">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="21bda-133">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="21bda-133">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21bda-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21bda-134">See also</span></span>

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [<span data-ttu-id="21bda-135">FlowLayoutPanel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="21bda-135">FlowLayoutPanel Control Overview</span></span>](flowlayoutpanel-control-overview.md)
