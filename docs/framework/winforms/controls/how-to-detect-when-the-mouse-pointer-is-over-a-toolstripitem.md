---
title: 'Porady: wykrywanie, kiedy wskaźnik myszy znajduje się nad elementem ToolStripItem'
ms.date: 03/30/2017
helpviewer_keywords:
- toolbars [Windows Forms], detecting mouse movement
- ToolStrip control [Windows Forms], detecting mouse movement
- ToolStripItem class [Windows Forms], detecting mouse movement
- mouse [Windows Forms], detecting movement on toolbars
ms.assetid: d38b5082-aba7-4f6c-841b-bd9714e307fd
ms.openlocfilehash: 15a7562efd9a86a029754610ffd9e77c372d1ac2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530500"
---
# <a name="how-to-detect-when-the-mouse-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="2c1c4-102">Porady: wykrywanie, kiedy wskaźnik myszy znajduje się nad elementem ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="2c1c4-102">How to: Detect When the Mouse Pointer Is Over a ToolStripItem</span></span>
<span data-ttu-id="2c1c4-103">Użyj poniższej procedury do wykrycia, gdy wskaźnik myszy znajduje się nad <xref:System.Windows.Forms.ToolStripItem>.</span><span class="sxs-lookup"><span data-stu-id="2c1c4-103">Use the following procedure to detect when the mouse pointer is over a <xref:System.Windows.Forms.ToolStripItem>.</span></span>  
  
### <a name="to-detect-when-the-pointer-is-over-a-toolstripitem"></a><span data-ttu-id="2c1c4-104">Do wykrycia, gdy kursor znajduje się nad elementem ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="2c1c4-104">To detect when the pointer is over a ToolStripItem</span></span>  
  
-   <span data-ttu-id="2c1c4-105">Użyj <xref:System.Windows.Forms.ToolStripItem.Selected%2A> właściwości dla elementów, w którym <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> jest `true`.</span><span class="sxs-lookup"><span data-stu-id="2c1c4-105">Use the <xref:System.Windows.Forms.ToolStripItem.Selected%2A> property for items in which <xref:System.Windows.Forms.ToolStripItem.CanSelect%2A> is `true`.</span></span>  
  
     <span data-ttu-id="2c1c4-106">Zostanie uniemożliwić uzyskanie do synchronizowania <xref:System.Windows.Forms.ToolStripItem.MouseEnter> i <xref:System.Windows.Forms.ToolStripItem.MouseLeave> zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2c1c4-106">This will prevent you from having to synchronize the <xref:System.Windows.Forms.ToolStripItem.MouseEnter> and <xref:System.Windows.Forms.ToolStripItem.MouseLeave> events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c1c4-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2c1c4-107">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripItem.Selected%2A>  
 [<span data-ttu-id="2c1c4-108">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="2c1c4-108">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
