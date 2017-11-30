---
title: "Porady: użycie elementu ToolTips w formantach ToolStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStrip control [Windows Forms], adding tooltips
- toolbars [Windows Forms], adding tooltips
- tooltips [Windows Forms], adding
ms.assetid: c5d86024-a7c5-44ee-8b3f-2daf53d80d3e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bc52dd1b629829564532fd93650737f51e5d7f24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Informacje o formancie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
