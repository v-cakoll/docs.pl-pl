---
title: 'Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AnchorDock
helpviewer_keywords:
- layout [Windows Forms], child controls
- controls [Windows Forms], child
- child controls [Windows Forms], anchoring and docking
- TableLayoutPanel control [Windows Forms], child controls
ms.assetid: 0d267c35-25f1-49b8-8976-c64e8f0ddc0b
ms.openlocfilehash: 0e565b56c31d0776f6e89bbbe0b0681ae184758e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922821"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a>Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel
Kontrolka obsługuje właściwości <xref:System.Windows.Forms.Control.Dock%2A> i w jego kontrolkach podrzędnych. <xref:System.Windows.Forms.Control.Anchor%2A> <xref:System.Windows.Forms.TableLayoutPanel>  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a>Aby wyrównać formant podrzędny w komórce TableLayoutPanel  
  
1. <xref:System.Windows.Forms.TableLayoutPanel> Utwórz kontrolkę w formularzu.  
  
2. Ustaw wartość <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> kontrolki i właściwości na **1.** <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A>  
  
3. Utwórz kontrolkę w <xref:System.Windows.Forms.TableLayoutPanel>kontrolce. <xref:System.Windows.Forms.Button> W <xref:System.Windows.Forms.Button> lewym górnym rogu komórki.  
  
4. Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolki na `Left`. <xref:System.Windows.Forms.Button> Kontrolka przenosi się do obszaru Wyrównaj do lewej krawędzi komórki.  
  
    > [!NOTE]
    > To zachowanie różni się od zachowania innych kontrolek kontenera. W innych kontrolkach kontenera formant podrzędny nie jest przenoszony, gdy <xref:System.Windows.Forms.Control.Anchor%2A> właściwość jest ustawiona, a odległość między kontrolką zakotwiczoną a granicą kontenera nadrzędnego jest ustalana w <xref:System.Windows.Forms.Control.Anchor%2A> momencie ustawienia właściwości.  
  
5. Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolki na `Top, Left`. <xref:System.Windows.Forms.Button> Formant przesuwa się w celu założenia lewego górnego rogu komórki.  
  
6. Powtórz krok 5 z wartością `Top, Right` , aby <xref:System.Windows.Forms.Button> przenieść formant do prawego górnego rogu komórki. Powtarzaj wartości `Bottom, Left` i `Bottom, Right`.  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a>Aby rozciągnąć formant podrzędny w komórce TableLayoutPanel  
  
1. Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolki na `Left, Right`. Rozmiar <xref:System.Windows.Forms.Button> formantu zostanie zmieniony w celu rozciągnięcia w całej komórce.  
  
    > [!NOTE]
    > To zachowanie różni się od zachowania innych kontrolek kontenera. W innych kontrolkach kontenera nie zmienia się rozmiar kontrolki podrzędnej, gdy <xref:System.Windows.Forms.Control.Anchor%2A> właściwość jest ustawiona na `Left, Right` lub `Top, Bottom`.  
  
2. Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolki na `Top, Bottom`. Rozmiar <xref:System.Windows.Forms.Button> formantu zostanie zmieniony w celu rozciągnięcia od góry do dołu komórki.  
  
3. Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolki na `Top, Bottom, Left, Right`. Rozmiar <xref:System.Windows.Forms.Button> kontrolki zostanie zmieniony w celu wypełnienia komórki.  
  
4. Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Anchor%2A> właściwości kontrolki na `None`. Rozmiar <xref:System.Windows.Forms.Button> formantu został zmieniony i wyśrodkowany w komórce.  
  
5. Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Dock%2A> właściwości kontrolki na <xref:System.Windows.Forms.DockStyle.Left>. <xref:System.Windows.Forms.Button> Kontrolka przenosi się do obszaru Wyrównaj do lewej krawędzi komórki. <xref:System.Windows.Forms.Button> Kontrolka zachowuje swoją szerokość, ale jej wysokość jest zmieniana, aby wypełnić komórkę w pionie.  
  
    > [!NOTE]
    > Jest to takie samo zachowanie, jak w przypadku innych kontrolek kontenera.  
  
6. Zmień wartość <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.Control.Dock%2A> właściwości kontrolki na <xref:System.Windows.Forms.DockStyle.Fill>. Rozmiar <xref:System.Windows.Forms.Button> kontrolki zostanie zmieniony w celu wypełnienia komórki.  
  
## <a name="example"></a>Przykład  
 Na poniższej ilustracji przedstawiono pięć przycisków zakotwiczonych w pięciu oddzielnych <xref:System.Windows.Forms.TableLayoutPanel> komórkach.  
  
 ![Zakotwiczanie TableLayoutPanel](./media/vs-tlpanchor.gif "VS_TLPanchor")  
  
 Na poniższej ilustracji przedstawiono cztery przyciski zakotwiczone w rogach czterech oddzielnych <xref:System.Windows.Forms.TableLayoutPanel> komórek.  
  
 ![Zakotwiczanie TableLayoutPanel](./media/vs-tlpanchor2.gif "VS_TLPanchor2")  
  
 Poniższa ilustracja przedstawia trzy przyciski rozciągane przez zakotwiczenie w trzech oddzielnych <xref:System.Windows.Forms.TableLayoutPanel> komórkach.  
  
 ![Zakotwiczanie TableLayoutPanel](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")  
  
 Poniższy przykład kodu demonstruje wszystkie kombinacje <xref:System.Windows.Forms.Control.Anchor%2A> wartości <xref:System.Windows.Forms.Button> właściwości kontrolki <xref:System.Windows.Forms.TableLayoutPanel> formantu.  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TableLayoutPanel>
- [TableLayoutPanel, kontrolka](tablelayoutpanel-control-windows-forms.md)
