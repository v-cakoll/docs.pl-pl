---
title: 'Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bb7984bf36ad05550845bb31374d696d631899d2
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="1a2a5-102">Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1a2a5-102">How to: Anchor and Dock Child Controls in a FlowLayoutPanel Control</span></span>
<span data-ttu-id="1a2a5-103"><xref:System.Windows.Forms.FlowLayoutPanel> Sterowanie obsługuje <xref:System.Windows.Forms.Control.Anchor%2A> i <xref:System.Windows.Forms.Control.Dock%2A> właściwości w jej kontrolkach podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-103">The <xref:System.Windows.Forms.FlowLayoutPanel> control supports the <xref:System.Windows.Forms.Control.Anchor%2A> and <xref:System.Windows.Forms.Control.Dock%2A> properties in its child controls.</span></span>  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a><span data-ttu-id="1a2a5-104">Aby zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="1a2a5-104">To anchor and dock child controls in a FlowLayoutPanel control</span></span>  
  
1.  <span data-ttu-id="1a2a5-105">Utwórz <xref:System.Windows.Forms.FlowLayoutPanel> kontrolkę w formularzu.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-105">Create a <xref:System.Windows.Forms.FlowLayoutPanel> control on your form.</span></span>  
  
2.  <span data-ttu-id="1a2a5-106">Ustaw <xref:System.Windows.Forms.Control.Width%2A> z <xref:System.Windows.Forms.FlowLayoutPanel> formant **300**i ustaw jej <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> do <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-106">Set the <xref:System.Windows.Forms.Control.Width%2A> of the <xref:System.Windows.Forms.FlowLayoutPanel> control to **300**, and set its <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> to <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
3.  <span data-ttu-id="1a2a5-107">Utwórz dwa <xref:System.Windows.Forms.Button> steruje i umieść je w <xref:System.Windows.Forms.FlowLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-107">Create two <xref:System.Windows.Forms.Button> controls, and place them in the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
4.  <span data-ttu-id="1a2a5-108">Ustaw <xref:System.Windows.Forms.Control.Width%2A> pierwszego przycisku, aby **200**.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-108">Set the <xref:System.Windows.Forms.Control.Width%2A> of the first button to **200**.</span></span>  
  
5.  <span data-ttu-id="1a2a5-109">Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwości drugiego przycisku <xref:System.Windows.Forms.DockStyle.Fill>.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-109">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to <xref:System.Windows.Forms.DockStyle.Fill>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1a2a5-110">Drugi przycisk zakłada szerokość przycisku pierwszej.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-110">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="1a2a5-111">Nie stretch poprzek <xref:System.Windows.Forms.FlowLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-111">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
6.  <span data-ttu-id="1a2a5-112">Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwości drugiego przycisku `None`.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-112">Set the <xref:System.Windows.Forms.Control.Dock%2A> property of the second button to `None`.</span></span> <span data-ttu-id="1a2a5-113">Powoduje to, że przycisk założenie oryginalną szerokość.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-113">This causes the button to assume its original width.</span></span>  
  
7.  <span data-ttu-id="1a2a5-114">Ustaw <xref:System.Windows.Forms.Control.Anchor%2A> właściwości drugiego przycisku `Left, Right`.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-114">Set the <xref:System.Windows.Forms.Control.Anchor%2A> property of the second button to `Left, Right`.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="1a2a5-115">Drugi przycisk zakłada szerokość przycisku pierwszej.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-115">The second button assumes the same width as the first button.</span></span> <span data-ttu-id="1a2a5-116">Nie stretch poprzek <xref:System.Windows.Forms.FlowLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-116">It does not stretch across the width of the <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span> <span data-ttu-id="1a2a5-117">To ogólna reguła Zakotwiczanie i dokowanie w <xref:System.Windows.Forms.FlowLayoutPanel> kontroli: dla pionowego przepływu kierunków, <xref:System.Windows.Forms.FlowLayoutPanel> kontroli oblicza szerokość domniemanych kolumny z najszerszych formant podrzędny w tej kolumnie.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-117">This is the general rule for anchoring and docking in the <xref:System.Windows.Forms.FlowLayoutPanel> control: for vertical flow directions, the <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the width of an implied column from the widest child control in the column.</span></span> <span data-ttu-id="1a2a5-118">Wszystkie inne formanty w tej kolumnie z <xref:System.Windows.Forms.Control.Anchor%2A> lub <xref:System.Windows.Forms.Control.Dock%2A> właściwości są wyrównane lub rozciągany tak, aby zmieścić ją w tej kolumnie domyślnych.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-118">All other controls in this column with <xref:System.Windows.Forms.Control.Anchor%2A> or <xref:System.Windows.Forms.Control.Dock%2A> properties are aligned or stretched to fit this implied column.</span></span> <span data-ttu-id="1a2a5-119">Zachowanie działa w podobny sposób jak dla kierunków przepływu poziomej.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-119">The behavior works in a similar way for horizontal flow directions.</span></span> <span data-ttu-id="1a2a5-120"><xref:System.Windows.Forms.FlowLayoutPanel> Kontroli oblicza wysokość wiersza domyślnych z najwyższego formantu podrzędnego w wierszu, a wszystkie formanty podrzędne zadokowanych lub zakotwiczonych w tym wierszu są wyrównane lub dopasowana domniemanych wiersza.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-120">The <xref:System.Windows.Forms.FlowLayoutPanel> control calculates the height of an implied row from the tallest child control in the row, and all docked or anchored child controls in this row are aligned or sized to fit the implied row.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a2a5-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="1a2a5-121">Example</span></span>  
 <span data-ttu-id="1a2a5-122">Na poniższej ilustracji przedstawiono cztery przyciski, które zakotwiczona i zadokowane względem niebieski przycisk w <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-122">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="1a2a5-123"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Jest <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-123">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.LeftToRight>.</span></span>  
  
 <span data-ttu-id="1a2a5-124">![Formantu FlowLayoutPanel](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.gif "NET_FLPanchorExp")</span><span class="sxs-lookup"><span data-stu-id="1a2a5-124">![FlowLayoutPanel anchoring](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.gif "NET_FLPanchorExp")</span></span>  
  
 <span data-ttu-id="1a2a5-125">Na poniższej ilustracji przedstawiono cztery przyciski, które zakotwiczona i zadokowane względem niebieski przycisk w <xref:System.Windows.Forms.FlowLayoutPanel>.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-125">The following illustration shows four buttons that are anchored and docked relative to the blue button in a <xref:System.Windows.Forms.FlowLayoutPanel>.</span></span> <span data-ttu-id="1a2a5-126"><xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Jest <xref:System.Windows.Forms.FlowDirection.TopDown>.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-126">The <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> is <xref:System.Windows.Forms.FlowDirection.TopDown>.</span></span>  
  
 <span data-ttu-id="1a2a5-127">![Formantu FlowLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.gif "VS_FLPanchor2")</span><span class="sxs-lookup"><span data-stu-id="1a2a5-127">![FlowLayoutPanel anchoring](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.gif "VS_FLPanchor2")</span></span>  
  
 <span data-ttu-id="1a2a5-128">Poniższy przykład kodu pokazuje różnych <xref:System.Windows.Forms.Control.Anchor%2A> wartości właściwości <xref:System.Windows.Forms.Button> kontroli w <xref:System.Windows.Forms.FlowLayoutPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-128">The following code example demonstrates various <xref:System.Windows.Forms.Control.Anchor%2A> property values for a <xref:System.Windows.Forms.Button> control in a <xref:System.Windows.Forms.FlowLayoutPanel> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1a2a5-129">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1a2a5-129">Compiling the Code</span></span>  
 <span data-ttu-id="1a2a5-130">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="1a2a5-130">This example requires:</span></span>  
  
-   <span data-ttu-id="1a2a5-131">Odwołania do zestawów systemu, dane systemowe, System.Drawing i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-131">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="1a2a5-132">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="1a2a5-132">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="1a2a5-133">Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="1a2a5-133">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="1a2a5-134">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="1a2a5-134">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a2a5-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1a2a5-135">See Also</span></span>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [<span data-ttu-id="1a2a5-136">FlowLayoutPanel, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="1a2a5-136">FlowLayoutPanel Control Overview</span></span>](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-overview.md)
