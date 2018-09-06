---
title: 'Porady: obejmowanie rzędów i kolumn w formancie TableLayoutPanel'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
ms.openlocfilehash: 5363e7a7def8d2593d3ac474deb9d3d7b77d3912
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43797608"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>Porady: obejmowanie rzędów i kolumn w formancie TableLayoutPanel
Kontrolki w <xref:System.Windows.Forms.TableLayoutPanel> kontrolki mogą znajdować się na sąsiadujących wierszy i kolumn.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-span-columns-and-rows"></a>Obejmować kolumnami i wierszami  
  
1.  Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza.  
  
2.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do lewej górnej komórki <xref:System.Windows.Forms.TableLayoutPanel> kontroli.  
  
3.  Ustaw <xref:System.Windows.Forms.Button> kontrolki **ColumnSpan** właściwości **2**. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli obejmuje pierwsza i druga kolumna.  
  
4.  Ustaw <xref:System.Windows.Forms.Button> kontrolki **RowSpan** właściwości **2**. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli rozciąga się pierwszym i drugim wierszu.  
  
5.  Ustaw <xref:System.Windows.Forms.Button> kontrolki **ColumnSpan** właściwości **1**. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontrola przechodzi do pierwszej kolumny i obejmuje pierwszym i drugim wierszu.  
  
## <a name="see-also"></a>Zobacz też  
 [TableLayoutPanel, kontrolka](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
