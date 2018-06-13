---
title: 'Porady: użycie elementu ToolTips w formantach ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 2b10b3fcf3930d5848f1d7a9602cfcc945bc8975
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534076"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>Porady: użycie elementu ToolTips w formantach ToolStrip
Można wyświetlić <xref:System.Windows.Forms.ToolTip> dla <xref:System.Windows.Forms.ToolStrip> formantu przez ustawienie formantu <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> właściwości `true`.  
  
### <a name="to-display-a-tooltip"></a>Aby wyświetlić etykietkę  
  
-   Ustaw <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> właściwości formantu `true`.  
  
     Wartość domyślna <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> jest `true`i wartość domyślną <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> i <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> jest `false`.  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>Aby użyć właściwości ToolTipText tekst etykietki narzędzia element ToolStripButton  
  
1.  Ustaw <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> właściwość przycisk, aby `true`.  
  
2.  Ustaw <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType> właściwość przycisk, aby `false`.  
  
     `AutoToolTip` Właściwość jest `true` domyślnie <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, i <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
     A <xref:System.Windows.Forms.ToolStripButton> używa jej `Text` właściwość <xref:System.Windows.Forms.ToolTip> tekst domyślnie. Ta procedura służy do wyświetlania tekstu niestandardowego w <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolTip>.  
  
> [!NOTE]
>  Jeśli ustawisz <xref:System.Windows.Forms.ToolStripItemDisplayStyle> do <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> lub <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, nie jest wyświetlany tekst przycisku, ale nadal jest wyświetlana etykietka narzędzia.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
 <xref:System.Windows.Forms.ToolStripButton>  
 <xref:System.Windows.Forms.ToolStripDropDownButton>  
 <xref:System.Windows.Forms.ToolStripSplitButton>  
 [ToolStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
