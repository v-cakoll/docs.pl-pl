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
ms.openlocfilehash: a84b00e93354a9aaff074a570cee931591816161
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053066"
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a>Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel
<xref:System.Windows.Forms.TableLayoutPanel> Kontrolować obsługuje <xref:System.Windows.Forms.Control.Anchor%2A> i <xref:System.Windows.Forms.Control.Dock%2A> właściwości w jego formantów podrzędnych.  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a>Aby wyrównać kontrolki podrzędnej w komórce TableLayoutPanel  
  
1. Utwórz <xref:System.Windows.Forms.TableLayoutPanel> kontrolkę w formularzu.  
  
2. Ustaw wartość <xref:System.Windows.Forms.TableLayoutPanel> kontrolki <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> i <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> właściwości **1**.  
  
3. Tworzenie <xref:System.Windows.Forms.Button> w kontrolce <xref:System.Windows.Forms.TableLayoutPanel> kontroli. <xref:System.Windows.Forms.Button> Zajmuje lewego górnego rogu komórki.  
  
4. Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Left`. <xref:System.Windows.Forms.Button> Kontrola przechodzi do przy lewej krawędzi komórki.  
  
    > [!NOTE]
    >  To zachowanie różni się od zachowania inne kontrolki kontenera. W innych formantów kontenera kontrolki podrzędnej nie powoduje przeniesienia kiedy <xref:System.Windows.Forms.Control.Anchor%2A> właściwość jest ustawiona i odległość między zakotwiczonej sterowania granicy kontenera nadrzędnego jest ustalony na czas <xref:System.Windows.Forms.Control.Anchor%2A> właściwość jest ustawiona.  
  
5. Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Top, Left`. <xref:System.Windows.Forms.Button> Kontrola przechodzi do zajmować w lewym górnym rogu komórki.  
  
6. Powtórz krok 5 z wartością `Top, Right` przenieść <xref:System.Windows.Forms.Button> kontrolki w prawym górnym rogu komórki. Powtórz tę procedurę za pomocą wartości `Bottom, Left` i `Bottom, Right`.  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a>Do usługi stretch kontrolki podrzędnej w komórce TableLayoutPanel  
  
1. Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Left, Right`. <xref:System.Windows.Forms.Button> Zmieni się rozmiar kontrolki można rozciągnąć na komórki.  
  
    > [!NOTE]
    >  To zachowanie różni się od zachowania inne kontrolki kontenera. W innych formantów kontenera kontrolki podrzędnej nie jest ze zmienionym rozmiarem, kiedy <xref:System.Windows.Forms.Control.Anchor%2A> właściwość jest ustawiona na `Left, Right` lub `Top, Bottom`.  
  
2. Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Top, Bottom`. <xref:System.Windows.Forms.Button> Zmieni się rozmiar kontrolki do rozciągania od górnej do dolnej krawędzi komórki.  
  
3. Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Top, Bottom, Left, Right`. <xref:System.Windows.Forms.Button> Zmieni się rozmiar kontrolki do wypełnienia komórki.  
  
4. Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `None`. <xref:System.Windows.Forms.Button> Zmianie rozmiaru czy wyśrodkowany w komórce formantu.  
  
5. Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Left>. <xref:System.Windows.Forms.Button> Kontrola przechodzi do przy lewej krawędzi komórki. <xref:System.Windows.Forms.Button> Kontrolka zachowuje jego szerokość, ale jego wysokości rozmiaru do wypełnienia komórki w pionie.  
  
    > [!NOTE]
    >  To jest takie samo zachowanie, jak odbywa się w innych kontrolek w kontenerze.  
  
6. Zmień wartość właściwości <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Button> Zmieni się rozmiar kontrolki do wypełnienia komórki.  
  
## <a name="example"></a>Przykład  
 Na poniższej ilustracji przedstawiono pięciu przycisków zakotwiczone w pięć oddzielnych <xref:System.Windows.Forms.TableLayoutPanel> komórek.  
  
 ![Zakotwiczanie formantu TableLayoutPanel](./media/vs-tlpanchor.gif "VS_TLPanchor")  
  
 Na poniższej ilustracji przedstawiono cztery przyciski zakotwiczone w rogach cztery oddzielne <xref:System.Windows.Forms.TableLayoutPanel> komórek.  
  
 ![Zakotwiczanie formantu TableLayoutPanel](./media/vs-tlpanchor2.gif "VS_TLPanchor2")  
  
 Na poniższej ilustracji przedstawiono trzy przyciski rozciągnięte przez Zakotwiczanie w trzech oddzielnych <xref:System.Windows.Forms.TableLayoutPanel> komórek.  
  
 ![Zakotwiczanie formantu TableLayoutPanel](./media/vs-tlpanchor3.gif "VS_TLPAnchor3")  
  
 Poniższy przykład kodu pokazuje wszystkie kombinacje <xref:System.Windows.Forms.Control.Anchor%2A> wartości właściwości <xref:System.Windows.Forms.Button> w kontrolce <xref:System.Windows.Forms.TableLayoutPanel> kontroli.  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
- Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TableLayoutPanel>
- [TableLayoutPanel, kontrolka](tablelayoutpanel-control-windows-forms.md)
