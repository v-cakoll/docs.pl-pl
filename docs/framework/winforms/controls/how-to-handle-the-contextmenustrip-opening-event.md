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
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a><span data-ttu-id="dbb00-102">Instrukcje: Obsługa zdarzenia otwierania kontrolki ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="dbb00-102">How to: Handle the ContextMenuStrip Opening Event</span></span>
<span data-ttu-id="dbb00-103">Można dostosować zachowanie usługi <xref:System.Windows.Forms.ContextMenuStrip> kontroli obsługi <xref:System.Windows.Forms.ToolStripDropDown.Opening> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="dbb00-103">You can customize the behavior of your <xref:System.Windows.Forms.ContextMenuStrip> control by handling the <xref:System.Windows.Forms.ToolStripDropDown.Opening> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dbb00-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="dbb00-104">Example</span></span>  
 <span data-ttu-id="dbb00-105">Poniższy przykład kodu demonstruje sposób obsługi <xref:System.Windows.Forms.ToolStripDropDown.Opening> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="dbb00-105">The following code example demonstrates how to handle the <xref:System.Windows.Forms.ToolStripDropDown.Opening> event.</span></span> <span data-ttu-id="dbb00-106">Obsługa zdarzeń dodaje elementy dynamicznie do <xref:System.Windows.Forms.ContextMenuStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="dbb00-106">The event handler adds items dynamically to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="dbb00-107">Aby uzyskać pełny przykład kodu, zobacz [jak: Dynamiczne dodawanie elementów ToolStrip](how-to-add-toolstrip-items-dynamically.md).</span><span class="sxs-lookup"><span data-stu-id="dbb00-107">For the complete code example, see [How to: Add ToolStrip Items Dynamically](how-to-add-toolstrip-items-dynamically.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 <span data-ttu-id="dbb00-108">Ustaw <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> właściwość `true` zapobiegające otwarcia menu.</span><span class="sxs-lookup"><span data-stu-id="dbb00-108">Set the <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> property to `true` to prevent the menu from opening.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbb00-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dbb00-109">See also</span></span>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [<span data-ttu-id="dbb00-110">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="dbb00-110">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
