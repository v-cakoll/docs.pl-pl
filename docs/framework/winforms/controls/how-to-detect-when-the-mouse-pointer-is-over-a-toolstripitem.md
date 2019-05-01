---
title: 'Instrukcje: wykrywanie, kiedy wskaźnik myszy znajduje się nad elementem ToolStripItem'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: 09fd9f2f9b8cc44b6c04b829bf2854bea4aa8cf7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054266"
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="927b7-102">Instrukcje: wykrywanie, kiedy wskaźnik myszy znajduje się nad elementem ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="927b7-102">How to: Detect When the Mouse Pointer Is Over a ToolStripItem</span></span>
<span data-ttu-id="927b7-103">Użyj poniższej procedury, aby wykryć, kiedy wskaźnik myszy znajduje się nad <xref:System.Windows.Forms.ToolStripItem>.</span><span class="sxs-lookup"><span data-stu-id="927b7-103">Use the following procedure to detect when the mouse pointer is over a <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="927b7-104">Aby wykryć, gdy wskaźnik znajduje się za pośrednictwem elementu ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="927b7-104">To detect when the pointer is over a ToolStripItem</span></span>  
  
- <span data-ttu-id="927b7-105">Użyj <xref:System.Windows.Forms.ToolStripItem.Selected%2A> właściwości dla elementów, w którym <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> jest `true`.</span><span class="sxs-lookup"><span data-stu-id="927b7-105">Use the <xref:System.Windows.Forms.ToolStripItem.Selected%2A> property for items in which <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> is `true`.</span></span>  
  
     <span data-ttu-id="927b7-106">To uniemożliwi konieczności synchronizacji <xref:System.Windows.Forms.ToolStripItem.MouseEnter> i <xref:System.Windows.Forms.ToolStripItem.MouseLeave> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="927b7-106">This will prevent you from having to synchronize the <xref:System.Windows.Forms.ToolStripItem.MouseEnter> and <xref:System.Windows.Forms.ToolStripItem.MouseLeave> events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="927b7-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="927b7-107">See also</span></span>

- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripItem.Selected%2A>
- [<span data-ttu-id="927b7-108">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="927b7-108">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
