---
title: 'Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: cb27454582dd4f3b299893c13b1202b33d9cacb9
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control"></a>Porady: zakotwiczenie i dokowanie formantów podrzędnych w formancie TableLayoutPanel
<xref:System.Windows.Forms.TableLayoutPanel> Sterowanie obsługuje <xref:System.Windows.Forms.Control.Anchor%2A> i <xref:System.Windows.Forms.Control.Dock%2A> właściwości w jej kontrolkach podrzędnych.  
  
### <a name="to-align-a-child-control-in-a-tablelayoutpanel-cell"></a>Aby wyrównać kontrolki podrzędnej w komórce formantu TableLayoutPanel  
  
1.  Utwórz <xref:System.Windows.Forms.TableLayoutPanel> kontrolkę w formularzu.  
  
2.  Ustaw wartość <xref:System.Windows.Forms.TableLayoutPanel> formantu <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> i <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> właściwości **1**.  
  
3.  Utwórz <xref:System.Windows.Forms.Button> kontroli w <xref:System.Windows.Forms.TableLayoutPanel> formantu. <xref:System.Windows.Forms.Button> Zajmuje lewego górnego rogu komórki.  
  
4.  Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości `Left`. <xref:System.Windows.Forms.Button> Kontroli przenosi do zapewnienia zgodności z lewej krawędzi komórki.  
  
    > [!NOTE]
    >  To zachowanie różni się od zachowania inne formanty kontenera. W innych kontrolek kontenera formant podrzędny nie przenosi kiedy <xref:System.Windows.Forms.Control.Anchor%2A> właściwość jest ustawiona, a odległość między zakotwiczonej kontroli i granic kontenera nadrzędnego jest ustalone w czasie <xref:System.Windows.Forms.Control.Anchor%2A> właściwość jest ustawiona.  
  
5.  Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości `Top, Left`. <xref:System.Windows.Forms.Button> Kontroli przenosi zajmować lewego górnego rogu komórki.  
  
6.  Powtórz krok 5 z wartością `Top, Right` można przenieść <xref:System.Windows.Forms.Button> formantu prawym górnym rogu komórki. Powtarzania z wartościami `Bottom, Left` i `Bottom, Right`.  
  
### <a name="to-stretch-a-child-control-in-a-tablelayoutpanel-cell"></a>Aby rozciągnąć formant podrzędny w komórce formantu TableLayoutPanel  
  
1.  Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości `Left, Right`. <xref:System.Windows.Forms.Button> Do rozciągania między komórki zostanie zmieniony rozmiar formantu.  
  
    > [!NOTE]
    >  To zachowanie różni się od zachowania inne formanty kontenera. W innych kontrolek kontenera formant podrzędny nie jest zmiany rozmiaru, kiedy <xref:System.Windows.Forms.Control.Anchor%2A> właściwość jest ustawiona na `Left, Right` lub `Top, Bottom`.  
  
2.  Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości `Top, Bottom`. <xref:System.Windows.Forms.Button> Do rozciągania od góry do dołu komórki zostanie zmieniony rozmiar formantu.  
  
3.  Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości `Top, Bottom, Left, Right`. <xref:System.Windows.Forms.Button> Do wypełnienia komórki zostanie zmieniony rozmiar formantu.  
  
4.  Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Anchor%2A> właściwości `None`. <xref:System.Windows.Forms.Button> Zmiany rozmiaru i wyśrodkowany w komórce kontroli.  
  
5.  Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Left>. <xref:System.Windows.Forms.Button> Kontroli przenosi do zapewnienia zgodności z lewej krawędzi komórki. <xref:System.Windows.Forms.Button> Formant zachowuje szerokości, ale jego wysokości rozmiaru do wypełnienia komórki w pionie.  
  
    > [!NOTE]
    >  To samo występujący w innych kontrolek w kontenerze.  
  
6.  Zmień wartość <xref:System.Windows.Forms.Button> formantu <xref:System.Windows.Forms.Control.Dock%2A> właściwości <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Button> Do wypełnienia komórki zostanie zmieniony rozmiar formantu.  
  
## <a name="example"></a>Przykład  
 Na poniższej ilustracji przedstawiono pięciu przycisków zakotwiczonych w oddzielnych pięć <xref:System.Windows.Forms.TableLayoutPanel> komórek.  
  
 ![Zakotwiczanie formantu TableLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-tlpanchor.gif "VS_TLPanchor")  
  
 Na poniższej ilustracji przedstawiono cztery przyciski zakotwiczonych w narożnikach cztery oddzielne <xref:System.Windows.Forms.TableLayoutPanel> komórek.  
  
 ![Zakotwiczanie formantu TableLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-tlpanchor2.gif "VS_TLPanchor2")  
  
 Na poniższej ilustracji przedstawiono trzy przyciski rozciągnięty przez Zakotwiczanie w trzech osobnych <xref:System.Windows.Forms.TableLayoutPanel> komórek.  
  
 ![Zakotwiczanie formantu TableLayoutPanel](../../../../docs/framework/winforms/controls/media/vs-tlpanchor3.gif "VS_TLPAnchor3")  
  
 Poniższy przykład kodu pokazuje wszystkie kombinacje <xref:System.Windows.Forms.Control.Anchor%2A> wartości właściwości <xref:System.Windows.Forms.Button> kontroli w <xref:System.Windows.Forms.TableLayoutPanel> formantu.  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/CS/TlpAnchorExampleForm.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.AnchorExampleForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.AnchorExampleForm/VB/TlpAnchorExampleForm.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe, System.Drawing i System.Windows.Forms.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [TableLayoutPanel, kontrolka](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
