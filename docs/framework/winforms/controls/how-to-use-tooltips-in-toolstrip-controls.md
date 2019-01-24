---
title: 'Instrukcje: Użycie elementu ToolTips w formantach ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 60d024dcb023b3d6cfafb68263291acefb38e14a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519174"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>Instrukcje: Użycie elementu ToolTips w formantach ToolStrip
Możesz wyświetlić <xref:System.Windows.Forms.ToolTip> dla <xref:System.Windows.Forms.ToolStrip> kontrolkę, która przez ustawienie jego <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> właściwość `true`.  
  
### <a name="to-display-a-tooltip"></a>Aby wyświetlić etykietkę narzędzia  
  
-   Ustaw <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> właściwości formantu, aby `true`.  
  
     Wartość domyślna <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> jest `true`i wartość domyślną <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> jest `false`.  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>Aby użyć właściwości ToolTipText element ToolStripButton tekst etykietki narzędzia  
  
1.  Ustaw <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> właściwości przycisku `true`.  
  
2.  Ustaw <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> właściwości przycisku `false`.  
  
     `AutoToolTip` Właściwość `true` domyślnie <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, i <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
     A <xref:System.Windows.Forms.ToolStripButton> używa jej `Text` właściwość <xref:System.Windows.Forms.ToolTip> tekst domyślnie. Użyj tej procedury, aby wyświetlić niestandardowy tekst w <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>.  
  
> [!NOTE]
>  Jeśli ustawisz <xref:System.Windows.Forms.ToolStripItemDisplayStyle> do <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> lub <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, nie jest wyświetlany tekst na przycisku, ale nadal pojawi się etykietka narzędzia.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [ToolStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
