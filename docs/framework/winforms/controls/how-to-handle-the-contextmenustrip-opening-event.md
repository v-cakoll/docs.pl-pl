---
title: "Porady: obsługa zdarzenia otwierania formantu ContextMenuStrip"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- context menus [Windows Forms], event handling
- ToolStrip control [Windows Forms]
- event handling [Windows Forms], context menus
- shortcut menus [Windows Forms], event handling
ms.assetid: b661b3dd-7815-4cc2-a1aa-a9a391ab3427
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 354631e514d9e2ece39d16bf7f259c36e4f90c32
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a>Porady: obsługa zdarzenia otwierania formantu ContextMenuStrip
Można dostosować zachowanie programu <xref:System.Windows.Forms.ContextMenuStrip> kontroli Obsługa <xref:System.Windows.Forms.ToolStripDropDown.Opening> zdarzeń.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu pokazuje sposób obsługi <xref:System.Windows.Forms.ToolStripDropDown.Opening> zdarzeń. Dodaje elementy programu obsługi zdarzeń dynamicznie do <xref:System.Windows.Forms.ContextMenuStrip> formantu. Na przykład kompletny kod, zobacz [porady: Dodawanie elementów ToolStrip dynamicznie](../../../../docs/framework/winforms/controls/how-to-add-toolstrip-items-dynamically.md).  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 Ustaw <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> właściwości `true` zapobiegające otwarcia menu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>  
 <xref:System.Windows.Forms.ToolStripDropDown>  
 [ToolStrip — formant](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
