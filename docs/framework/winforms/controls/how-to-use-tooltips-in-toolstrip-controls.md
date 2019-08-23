---
title: 'Instrukcje: użycie elementu ToolTips w kontrolkach ToolStrip'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
ms.openlocfilehash: 3f383b6cccba7825637ea65a0e13280b91b406c9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939732"
---
# <a name="how-to-use-tooltips-in-toolstrip-controls"></a>Instrukcje: użycie elementu ToolTips w kontrolkach ToolStrip
Możesz <xref:System.Windows.Forms.ToolTip> wyświetlić odpowiedni <xref:System.Windows.Forms.ToolStrip> formant, ustawiając <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A> właściwość kontrolki na `true`.  
  
### <a name="to-display-a-tooltip"></a>Aby wyświetlić etykietkę narzędzia  
  
- Ustaw właściwość formantu na `true`. <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
  
     Wartość <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A?displayProperty=nameWithType> domyślna to `true`, <xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A?displayProperty=nameWithType> a wartość <xref:System.Windows.Forms.StatusStrip.ShowItemToolTips%2A?displayProperty=nameWithType> domyślna to .`false`  
  
### <a name="to-use-the-tooltiptext-property-for-the-tooltip-text-of-a-toolstripbutton"></a>Aby użyć właściwości ToolTipText dla tekstu etykietki narzędzia element ToolStripButton  
  
1. Ustaw właściwość przycisku na `true`. <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>  
  
2. Ustaw właściwość przycisku na `false`. <xref:System.Windows.Forms.ToolStripButton.AutoToolTip%2A?displayProperty=nameWithType>  
  
     `AutoToolTip` Właściwość jest `true` domyślnie dla <xref:System.Windows.Forms.ToolStripButton>, i<xref:System.Windows.Forms.ToolStripDropDownButton>. <xref:System.Windows.Forms.ToolStripSplitButton>  
  
     A <xref:System.Windows.Forms.ToolStripButton> domyślnie używa `Text` swojej właściwości dla <xref:System.Windows.Forms.ToolTip> tekstu. Użyj tej procedury, aby wyświetlić niestandardowy tekst w <xref:System.Windows.Forms.ToolStripButton>. <xref:System.Windows.Forms.ToolTip>  
  
> [!NOTE]
> Jeśli ustawisz <xref:System.Windows.Forms.ToolStripItemDisplayStyle> <xref:System.Windows.Forms.ToolStripItemDisplayStyle.None> opcję lub <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Image>, na przycisku nie będzie wyświetlany tekst, ale etykietka narzędzia nadal pojawia się.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ToolStrip.ShowItemToolTips%2A>
- <xref:System.Windows.Forms.ToolStripButton>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- <xref:System.Windows.Forms.ToolStripSplitButton>
- [ToolStrip, kontrolka — omówienie](toolstrip-control-overview-windows-forms.md)
