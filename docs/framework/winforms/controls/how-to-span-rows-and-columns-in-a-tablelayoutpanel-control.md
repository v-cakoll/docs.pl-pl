---
title: "Porady: obejmowanie rzędów i kolumn w formancie TableLayoutPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: net.ComponentModel.StyleCollectionEditor.TLP.SpanRowsColumns
helpviewer_keywords:
- columns [Windows Forms], spanning
- merging cells
- TableLayoutPanel control [Windows Forms], spanning rows and columns
- rows [Windows Forms], spanning
- cells [Windows Forms], merging
ms.assetid: a8a2fdd3-a848-48b0-a4cd-4e85ebded87e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0380e63925dcbd27a7ee6262ddbfb2706455c2a9
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-span-rows-and-columns-in-a-tablelayoutpanel-control"></a>Porady: obejmowanie rzędów i kolumn w formancie TableLayoutPanel
Formanty w <xref:System.Windows.Forms.TableLayoutPanel> formant może obejmować sąsiadujących wierszy i kolumn.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-span-columns-and-rows"></a>Zakresu kolumn i wierszy  
  
1.  Przeciągnij <xref:System.Windows.Forms.TableLayoutPanel> kontrolować z **przybornika** na formularzu.  
  
2.  Przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** do lewej górnej komórki <xref:System.Windows.Forms.TableLayoutPanel> formantu.  
  
3.  Ustaw <xref:System.Windows.Forms.Button> formantu **ColumnSpan** właściwości **2**. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli obejmuje w pierwszej i drugiej kolumnie.  
  
4.  Ustaw <xref:System.Windows.Forms.Button> formantu **RowSpan** właściwości **2**. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli obejmuje pierwszym i drugim wierszu.  
  
5.  Ustaw <xref:System.Windows.Forms.Button> formantu **ColumnSpan** właściwości **1**. Należy pamiętać, że <xref:System.Windows.Forms.Button> kontroli przenosi do pierwszej kolumny i obejmuje pierwszym i drugim wierszu.  
  
## <a name="see-also"></a>Zobacz też  
 [TableLayoutPanel — formant](../../../../docs/framework/winforms/controls/tablelayoutpanel-control-windows-forms.md)
