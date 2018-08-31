---
title: 'Porady: wyrównywanie i rozciąganie formantu w formancie TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
ms.openlocfilehash: 06e152058337955164bd526e20e023d759340f01
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254607"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a>Porady: wyrównywanie i rozciąganie formantu w formancie TableLayoutPanel
Wyrównywanie i rozciąganie kontrolek w <xref:System.Windows.Forms.TableLayoutPanel> z <xref:System.Windows.Forms.Control.Anchor%2A> i <xref:System.Windows.Forms.Control.Dock%2A> właściwości.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-align-and-stretch-a-control"></a>Aby wyrównać i stretch kontrolki  
  
1.  Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza.  
  
2.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do lewej górnej komórki <xref:System.Windows.Forms.TableLayoutPanel> kontroli. <xref:System.Windows.Forms.Button> Kontroli jest wyśrodkowywana w komórce.  
  
3.  Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Left,Right`. <xref:System.Windows.Forms.Button> Kontrolować odcinkach, aby dopasować szerokości krawędzi komórki.  
  
4.  Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Top,Bottom`. <xref:System.Windows.Forms.Button> Kontrolować odcinkach, aby dopasować wysokość komórki.  
  
5.  Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Button> Kontroli rozwija do wypełnienia komórki.  
  
6.  Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.None>. <xref:System.Windows.Forms.Button> Formant powraca do oryginalnego rozmiaru i przechodzi do lewego górnego rogu komórki. **Windows Forms Designer** ustawił <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Top, Left`.  
  
7.  Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Bottom,Right`. <xref:System.Windows.Forms.Button> Kontrola przechodzi do prawego dolnego rogu komórki.  
  
8.  Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość <xref:System.Windows.Forms.AnchorStyles.None>. <xref:System.Windows.Forms.Button> Sterowania przechodzi na środku komórki.  
  
## <a name="see-also"></a>Zobacz też  
 [TableLayoutPanel, kontrolka](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
