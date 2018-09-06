---
title: 'Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: b53547e8e61e69834f262407de490422e6b6bb00
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748711"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel
<xref:System.Windows.Forms.FlowLayoutPanel> Kontrolować obsługuje <xref:System.Windows.Forms.Control.Anchor%2A> i <xref:System.Windows.Forms.Control.Dock%2A> właściwości w jego formantów podrzędnych.  
  
### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Aby zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel  
  
1.  Utwórz <xref:System.Windows.Forms.FlowLayoutPanel> kontrolkę w formularzu.  
  
2.  Ustaw <xref:System.Windows.Forms.Control.Width%2A> z <xref:System.Windows.Forms.FlowLayoutPanel> kontrolę **300**i ustaw jego <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> do <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
3.  Utworzyć dwa <xref:System.Windows.Forms.Button> kontroluje i umieść je w <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.  
  
4.  Ustaw <xref:System.Windows.Forms.Control.Width%2A> pierwszego przycisku, aby **200**.  
  
5.  Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość drugi przycisk, który <xref:System.Windows.Forms.DockStyle.Fill>.  
  
    > [!NOTE]
    >  Drugi przycisk zakłada taką samą szerokość jako pierwszy przycisk. Nie rozciągnąć na szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.  
  
6.  Ustaw <xref:System.Windows.Forms.Control.Dock%2A> właściwość drugi przycisk, który `None`. To powoduje, że przycisk założył, jego oryginalna szerokość.  
  
7.  Ustaw <xref:System.Windows.Forms.Control.Anchor%2A> właściwość drugi przycisk, który `Left, Right`.  
  
    > [!IMPORTANT]
    >  Drugi przycisk zakłada taką samą szerokość jako pierwszy przycisk. Nie rozciągnąć na szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontroli. To ogólne reguły dla Zakotwiczanie i dokowanie w <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki: w kierunkach pionowy przepływu <xref:System.Windows.Forms.FlowLayoutPanel> kontroli oblicza szerokość kolumny dorozumianych z najszerszej kontrolki podrzędnej w kolumnie. Wszystkie kontrolki w tej kolumnie, za pomocą <xref:System.Windows.Forms.Control.Anchor%2A> lub <xref:System.Windows.Forms.Control.Dock%2A> właściwości są wyrównane, czy rozciągnięte do mieści się w tej kolumnie dorozumianych. Zachowanie działa w podobny sposób jak w poziomie przepływu kierunkach. <xref:System.Windows.Forms.FlowLayoutPanel> Kontroli oblicza wysokość wiersza dorozumianych od najwyższego kontrolki podrzędnej w wierszu i wszystkich kontrolek podrzędnych zadokowany lub zakotwiczone w tym wierszu są wyrównane lub dopasowana dorozumianych wiersza.  
  
## <a name="example"></a>Przykład  
 Na poniższej ilustracji przedstawiono cztery przyciski, które są zakotwiczone zadokowane względem niebieski przycisk w <xref:System.Windows.Forms.FlowLayoutPanel>. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Jest <xref:System.Windows.Forms.FlowDirection.LeftToRight>.  
  
 ![Formantu FlowLayoutPanel](../../../../docs/framework/winforms/controls/media/net-flpanchorexp.gif "NET_FLPanchorExp")  
  
 Na poniższej ilustracji przedstawiono cztery przyciski, które są zakotwiczone zadokowane względem niebieski przycisk w <xref:System.Windows.Forms.FlowLayoutPanel>. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Jest <xref:System.Windows.Forms.FlowDirection.TopDown>.  
  
 ![Formantu FlowLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-flpanchor2.gif "VS_FLPanchor2")  
  
 Poniższy przykład kodu demonstruje różne <xref:System.Windows.Forms.Control.Anchor%2A> wartości właściwości <xref:System.Windows.Forms.Button> w kontrolce <xref:System.Windows.Forms.FlowLayoutPanel> kontroli.  
  
 [!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [FlowLayoutPanel, kontrolka — omówienie](../../../../docs/framework/winforms/controls/flowlayoutpanel-control-overview.md)
