---
title: 'Instrukcje: wyrównywanie i rozciąganie kontrolki w kontrolce TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.AlignStretchCtrl
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms], stretching controls
- controls [Windows Forms], stretching
- controls [Windows Forms], aligning
ms.assetid: 7dc1a157-6fee-4995-8ebc-b65bdc0909a8
ms.openlocfilehash: fd32593bcad9e3f3ef93edee8aa2659d423f9feb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210361"
---
# <a name="how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control"></a>Instrukcje: wyrównywanie i rozciąganie kontrolki w kontrolce TableLayoutPanel

Wyrównywanie i rozciąganie kontrolek w <xref:System.Windows.Forms.TableLayoutPanel> z <xref:System.Windows.Forms.Control.Anchor%2A> i <xref:System.Windows.Forms.Control.Dock%2A> właściwości.

## <a name="align-and-stretch-a-control"></a>Wyrównaj i rozciągnij kontrolki

1. W programie Visual Studio przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza.

2. Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do lewej górnej komórki <xref:System.Windows.Forms.TableLayoutPanel> kontroli. <xref:System.Windows.Forms.Button> Kontroli jest wyśrodkowywana w komórce.

3. Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Left,Right`. <xref:System.Windows.Forms.Button> Kontrolować odcinkach, aby dopasować szerokości krawędzi komórki.

4. Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Top,Bottom`. <xref:System.Windows.Forms.Button> Kontrolować odcinkach, aby dopasować wysokość komórki.

5. Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.Fill>. <xref:System.Windows.Forms.Button> Kontroli rozwija do wypełnienia komórki.

6. Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Dock%2A> właściwość <xref:System.Windows.Forms.DockStyle.None>. <xref:System.Windows.Forms.Button> Formant powraca do oryginalnego rozmiaru i przechodzi do lewego górnego rogu komórki. **Windows Forms Designer** ustawił <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Top, Left`.

7. Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość `Bottom,Right`. <xref:System.Windows.Forms.Button> Kontrola przechodzi do prawego dolnego rogu komórki.

8. Ustaw wartość <xref:System.Windows.Forms.Button> kontrolki <xref:System.Windows.Forms.Control.Anchor%2A> właściwość <xref:System.Windows.Forms.AnchorStyles.None>. <xref:System.Windows.Forms.Button> Sterowania przechodzi na środku komórki.

## <a name="see-also"></a>Zobacz także

- [TableLayoutPanel, kontrolka](tablelayoutpanel-control-windows-forms.md)
