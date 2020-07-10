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
# <a name="how-to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie FlowLayoutPanel

<xref:System.Windows.Forms.FlowLayoutPanel>Kontrolka obsługuje <xref:System.Windows.Forms.Control.Anchor%2A> właściwości i <xref:System.Windows.Forms.Control.Dock%2A> w jego kontrolkach podrzędnych.

### <a name="to-anchor-and-dock-child-controls-in-a-flowlayoutpanel-control"></a>Aby zakotwiczyć i zadokować kontrolki podrzędne w kontrolce FlowLayoutPanel

1. Utwórz <xref:System.Windows.Forms.FlowLayoutPanel> kontrolkę w formularzu.

2. Ustaw wartość <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki na **300**, a następnie ustaw jej wartość <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A> na <xref:System.Windows.Forms.FlowDirection.TopDown> .

3. Utwórz dwie <xref:System.Windows.Forms.Button> kontrolki i umieść je w <xref:System.Windows.Forms.FlowLayoutPanel> kontrolce.

4. Ustaw wartość <xref:System.Windows.Forms.Control.Width%2A> pierwszego przycisku na **200**.

5. Ustaw <xref:System.Windows.Forms.Control.Dock%2A> Właściwość drugiego przycisku na <xref:System.Windows.Forms.DockStyle.Fill> .

    > [!NOTE]
    > Drugi przycisk przyjmuje taką samą szerokość jak pierwszy przycisk. Nie rozciąga się na szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki.

6. Ustaw <xref:System.Windows.Forms.Control.Dock%2A> Właściwość drugiego przycisku na `None` . Spowoduje to, że przycisk przyjmie oryginalną szerokość.

7. Ustaw <xref:System.Windows.Forms.Control.Anchor%2A> Właściwość drugiego przycisku na `Left, Right` .

    > [!IMPORTANT]
    > Drugi przycisk przyjmuje taką samą szerokość jak pierwszy przycisk. Nie rozciąga się na szerokość <xref:System.Windows.Forms.FlowLayoutPanel> kontrolki. Jest to ogólna reguła zakotwiczenia i dokowania w <xref:System.Windows.Forms.FlowLayoutPanel> kontrolce: dla pionowych kierunków przepływu <xref:System.Windows.Forms.FlowLayoutPanel> kontrolka oblicza szerokość kolumny implikowanej z najszerszej kontrolki podrzędnej w kolumnie. Wszystkie inne kontrolki w tej kolumnie z <xref:System.Windows.Forms.Control.Anchor%2A> lub <xref:System.Windows.Forms.Control.Dock%2A> właściwości są wyrównane lub rozciągane w celu dopasowania do tej kolumny implikowanej. Zachowanie działa podobnie do poziomych kierunków przepływu. <xref:System.Windows.Forms.FlowLayoutPanel>Kontrolka oblicza wysokość implikowanego wiersza z najwyższego poziomu kontrolki podrzędnej w wierszu, a wszystkie kontrolki podrzędne zadokowane lub zakotwiczone w tym wierszu są wyrównane lub skalowane, aby dopasować implikowany wiersz.

## <a name="example"></a>Przykład

Na poniższej ilustracji przedstawiono cztery przyciski zakotwiczone i zadokowane względem niebieskiego przycisku w <xref:System.Windows.Forms.FlowLayoutPanel> . <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>Ma wartość <xref:System.Windows.Forms.FlowDirection.LeftToRight> .

![Zakotwiczenie FlowLayoutPanel](./media/net-flpanchorexp.gif "NET_FLPanchorExp")

Na poniższej ilustracji przedstawiono cztery przyciski zakotwiczone i zadokowane względem niebieskiego przycisku w <xref:System.Windows.Forms.FlowLayoutPanel> . <xref:System.Windows.Forms.FlowLayoutPanel.FlowDirection%2A>Ma wartość <xref:System.Windows.Forms.FlowDirection.TopDown> .

![Zakotwiczenie FlowLayoutPanel](./media/vs-flpanchor2.gif "VS_FLPanchor2")

Poniższy przykład kodu demonstruje różne <xref:System.Windows.Forms.Control.Anchor%2A> wartości właściwości <xref:System.Windows.Forms.Button> kontrolki w <xref:System.Windows.Forms.FlowLayoutPanel> kontrolce.

[!code-csharp[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/CS/FlpAnchorExampleForm.cs#1)]
[!code-vb[System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlowLayoutPanel.AnchorExampleForm/VB/FlpAnchorExampleForm.vb#1)]

## <a name="compiling-the-code"></a>Kompilowanie kodu

Ten przykład wymaga:

- Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.FlowLayoutPanel>
- [FlowLayoutPanel — Informacje o formancie](flowlayoutpanel-control-overview.md)
