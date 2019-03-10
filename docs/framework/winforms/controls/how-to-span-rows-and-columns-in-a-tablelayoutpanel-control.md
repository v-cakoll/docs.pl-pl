---
title: 'Instrukcje: Obejmowanie rzędów i kolumn w formancie TableLayoutPanel'
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
ms.openlocfilehash: e4fc00c3966d44ba36a0c59b37ae2fa1cd431014
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703039"
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>Instrukcje: Obejmowanie rzędów i kolumn w formancie TableLayoutPanel
Kontrolki w <xref:System.Windows.Forms.TableLayoutPanel> kontrolki mogą znajdować się na sąsiadujących wierszy i kolumn.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-span-columns-and-rows"></a>Obejmować kolumnami i wierszami  
  
1.  Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> z kontrolować **przybornika** do formularza.  
  
2.  Przeciągnij <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do lewej górnej komórki <xref:System.Windows.Forms.TableLayoutPanel> kontroli.  
  
3.  Ustaw <xref:System.Windows.Forms.Button> kontrolki **ColumnSpan** właściwości **2**. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli obejmuje pierwsza i druga kolumna.  
  
4.  Ustaw <xref:System.Windows.Forms.Button> kontrolki **RowSpan** właściwości **2**. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli rozciąga się pierwszym i drugim wierszu.  
  
5.  Ustaw <xref:System.Windows.Forms.Button> kontrolki **ColumnSpan** właściwości **1**. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontrola przechodzi do pierwszej kolumny i obejmuje pierwszym i drugim wierszu.  
  
## <a name="see-also"></a>Zobacz także
- [TableLayoutPanel, kontrolka](tablelayoutpanel-control-windows-forms.md)
