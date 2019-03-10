---
title: 'Instrukcje: Obsługa zdarzenia otwierania kontrolki ContextMenuStrip'
ms.date: 03/30/2017
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
ms.openlocfilehash: 179411da96362fd9ba42e2b97682f335beb894c1
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715454"
---
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a>Instrukcje: Obsługa zdarzenia otwierania kontrolki ContextMenuStrip
Można dostosować zachowanie usługi <xref:System.Windows.Forms.ContextMenuStrip> kontroli obsługi <xref:System.Windows.Forms.ToolStripDropDown.Opening> zdarzeń.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu demonstruje sposób obsługi <xref:System.Windows.Forms.ToolStripDropDown.Opening> zdarzeń. Obsługa zdarzeń dodaje elementy dynamicznie do <xref:System.Windows.Forms.ContextMenuStrip> kontroli. Aby uzyskać pełny przykład kodu, zobacz [jak: Dynamiczne dodawanie elementów ToolStrip](how-to-add-toolstrip-items-dynamically.md).  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 Ustaw <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> właściwość `true` zapobiegające otwarcia menu.  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [ToolStrip, kontrolka](toolstrip-control-windows-forms.md)
