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
# <a name="how-to-handle-the-contextmenustrip-opening-event"></a><span data-ttu-id="b923c-102">Porady: obsługa zdarzenia otwierania formantu ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="b923c-102">How to: Handle the ContextMenuStrip Opening Event</span></span>
<span data-ttu-id="b923c-103">Można dostosować zachowanie programu <xref:System.Windows.Forms.ContextMenuStrip> kontroli Obsługa <xref:System.Windows.Forms.ToolStripDropDown.Opening> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b923c-103">You can customize the behavior of your <xref:System.Windows.Forms.ContextMenuStrip> control by handling the <xref:System.Windows.Forms.ToolStripDropDown.Opening> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b923c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="b923c-104">Example</span></span>  
 <span data-ttu-id="b923c-105">Poniższy przykład kodu pokazuje sposób obsługi <xref:System.Windows.Forms.ToolStripDropDown.Opening> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b923c-105">The following code example demonstrates how to handle the <xref:System.Windows.Forms.ToolStripDropDown.Opening> event.</span></span> <span data-ttu-id="b923c-106">Dodaje elementy programu obsługi zdarzeń dynamicznie do <xref:System.Windows.Forms.ContextMenuStrip> formantu.</span><span class="sxs-lookup"><span data-stu-id="b923c-106">The event handler adds items dynamically to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="b923c-107">Na przykład kompletny kod, zobacz [porady: Dodawanie elementów ToolStrip dynamicznie](../../../../docs/framework/winforms/controls/how-to-add-toolstrip-items-dynamically.md).</span><span class="sxs-lookup"><span data-stu-id="b923c-107">For the complete code example, see [How to: Add ToolStrip Items Dynamically](../../../../docs/framework/winforms/controls/how-to-add-toolstrip-items-dynamically.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#42)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#42)]  
  
 <span data-ttu-id="b923c-108">Ustaw <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> właściwości `true` zapobiegające otwarcia menu.</span><span class="sxs-lookup"><span data-stu-id="b923c-108">Set the <xref:System.ComponentModel.CancelEventArgs.Cancel%2A?displayProperty=nameWithType> property to `true` to prevent the menu from opening.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b923c-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b923c-109">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>  
 <xref:System.Windows.Forms.ToolStripDropDown>  
 [<span data-ttu-id="b923c-110">ToolStrip — formant</span><span class="sxs-lookup"><span data-stu-id="b923c-110">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
