---
title: 'Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce FlowLayoutPanel'
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms], child controls
- FlowLayoutPanel control [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
ms.assetid: a2bcdfca-9b63-45e6-9c0e-3411015cba98
ms.openlocfilehash: 3e9a5be944e199254ddb9cee0772c4d55be8fb77
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046064"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce FlowLayoutPanel

Kontrolka obsługuje właściwości <xref:System.Windows.Forms.Control.Dock%2A> i w jego kontrolkach podrzędnych. <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.FlowLayoutPanel>

### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Aby zakotwiczyć i zadokować kontrolki podrzędne w kontrolce FlowLayoutPanel

1. <xref:System.Windows.Forms.FlowLayoutPanel> Utwórz kontrolkę w formularzu.

2. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> <xref:System.Windows.Forms.FlowDirection.TopDown>Ustaw wartość kontrolkina300,anastępnieustawjejwartośćna.<xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.Control.Width%2A>

3. Utwórz dwie <xref:System.Windows.Forms.Button> kontrolki i umieść je <xref:System.Windows.Forms.FlowLayoutPanel> w kontrolce.

4. Ustaw wartość pierwszego przycisku na 200. <xref:System.Windows.Forms.Control.Width%2A>

5. Ustaw właściwość drugiego przycisku na <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Control.Dock%2A>

    > [!NOTE]
    > Drugi przycisk przyjmuje taką samą szerokość jak pierwszy przycisk. Nie rozciąga się na szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki.

6. Ustaw właściwość drugiego przycisku na `None`. <xref:System.Windows.Forms.Control.Dock%2A> Spowoduje to, że przycisk przyjmie oryginalną szerokość.

7. Ustaw właściwość drugiego przycisku na `Left, Right`. <xref:System.Windows.Forms.Control.Anchor%2A>

    > [!IMPORTANT]
    > Drugi przycisk przyjmuje taką samą szerokość jak pierwszy przycisk. Nie rozciąga się na szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki. Jest to ogólna reguła zakotwiczenia i dokowania w <xref:System.Windows.Forms.FlowLayoutPanel> kontrolce: dla pionowych kierunków <xref:System.Windows.Forms.FlowLayoutPanel> przepływu kontrolka oblicza szerokość kolumny implikowanej z najszerszej kontrolki podrzędnej w kolumnie. Wszystkie inne kontrolki w tej kolumnie <xref:System.Windows.Forms.Control.Anchor%2A> z <xref:System.Windows.Forms.Control.Dock%2A> lub właściwości są wyrównane lub rozciągane w celu dopasowania do tej kolumny implikowanej. Zachowanie działa podobnie do poziomych kierunków przepływu. <xref:System.Windows.Forms.FlowLayoutPanel> Kontrolka oblicza wysokość implikowanego wiersza z najwyższego poziomu kontrolki podrzędnej w wierszu, a wszystkie kontrolki podrzędne zadokowane lub zakotwiczone w tym wierszu są wyrównane lub skalowane, aby dopasować implikowany wiersz.

## <a name="example"></a>Przykład

Na poniższej ilustracji przedstawiono cztery przyciski zakotwiczone i zadokowane względem niebieskiego przycisku w <xref:System.Windows.Forms.FlowLayoutPanel>. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Ma<xref:System.Windows.Forms.FlowDirection.LeftToRight>wartość.

![Zakotwiczenie FlowLayoutPanel](./media/net-flpanchorexp.gif "NET_FLPanchorExp")

Na poniższej ilustracji przedstawiono cztery przyciski zakotwiczone i zadokowane względem niebieskiego przycisku w <xref:System.Windows.Forms.FlowLayoutPanel>. <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> Ma<xref:System.Windows.Forms.FlowDirection.TopDown>wartość.

![Zakotwiczenie FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")

Poniższy przykład kodu demonstruje różne <xref:System.Windows.Forms.Control.Anchor%2A> wartości <xref:System.Windows.Forms.Button> właściwości kontrolki w <xref:System.Windows.Forms.FlowLayoutPanel> kontrolce.

[!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
[!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [FlowLayoutPanel, kontrolka — omówienie](flowlayoutpanel-control-overview.md)
