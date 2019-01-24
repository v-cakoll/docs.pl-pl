---
title: 'Instrukcje: Wykryj, kiedy wskaźnik myszy znajduje się nad elementu ToolStripItem'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: 20fbc91773f431fc68f606f8aa9f24f4c0cc06bf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539600"
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="452f8-102">Instrukcje: Wykryj, kiedy wskaźnik myszy znajduje się nad elementu ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="452f8-102">How to: Detect When the Mouse Pointer Is Over a ToolStripItem</span></span>
<span data-ttu-id="452f8-103">Użyj poniższej procedury, aby wykryć, kiedy wskaźnik myszy znajduje się nad <xref:System.Windows.Forms.ToolStripItem>.</span><span class="sxs-lookup"><span data-stu-id="452f8-103">Use the following procedure to detect when the mouse pointer is over a <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="452f8-104">Aby wykryć, gdy wskaźnik znajduje się za pośrednictwem elementu ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="452f8-104">To detect when the pointer is over a ToolStripItem</span></span>  
  
-   <span data-ttu-id="452f8-105">Użyj <xref:System.Windows.Forms.ToolStripItem.Selected%2A> właściwości dla elementów, w którym <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> jest `true`.</span><span class="sxs-lookup"><span data-stu-id="452f8-105">Use the <xref:System.Windows.Forms.ToolStripItem.Selected%2A> property for items in which <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> is `true`.</span></span>  
  
     <span data-ttu-id="452f8-106">To uniemożliwi konieczności synchronizacji <xref:System.Windows.Forms.ToolStripItem.MouseEnter> i <xref:System.Windows.Forms.ToolStripItem.MouseLeave> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="452f8-106">This will prevent you from having to synchronize the <xref:System.Windows.Forms.ToolStripItem.MouseEnter> and <xref:System.Windows.Forms.ToolStripItem.MouseLeave> events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="452f8-107">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="452f8-107">See also</span></span>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripItem.Selected%2A>
- [<span data-ttu-id="452f8-108">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="452f8-108">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
