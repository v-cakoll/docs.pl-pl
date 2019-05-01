---
title: 'Instrukcje: dodawanie elementów menu do paska ContextMenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrips [Windows Forms], adding menu items
- shortcut menus [Windows Forms], adding items
- context menus [Windows Forms], adding menu items
ms.assetid: 1ec14776-3ea2-4752-bd22-4fae0fd19e1a
ms.openlocfilehash: 534bbd2c2edb68dca0f2a1c2997ff1ba762ef07c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011050"
---
# <a name="how-to-add-menu-items-to-a-contextmenustrip"></a><span data-ttu-id="407bf-102">Instrukcje: dodawanie elementów menu do paska ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="407bf-102">How to: Add Menu Items to a ContextMenuStrip</span></span>
<span data-ttu-id="407bf-103">Można dodać element menu tylko jeden lub kilka elementów, które znajdują się w czasie <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="407bf-103">You can add just one menu item or several items at a time to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-add-a-single-menu-item-to-a-contextmenustrip"></a><span data-ttu-id="407bf-104">Aby dodać pojedynczy element menu do paska ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="407bf-104">To add a single menu item to a ContextMenuStrip</span></span>  
  
- <span data-ttu-id="407bf-105">Użyj <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> metodę, aby dodać jeden element menu do <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="407bf-105">Use the <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add one menu item to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
    ```vb  
    Me.contextMenuStrip1.Items.Add(Me.toolStripMenuItem1)  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.Add(toolStripMenuItem1);  
    ```  
  
### <a name="to-add-several-menu-items-to-a-contextmenustrip"></a><span data-ttu-id="407bf-106">Aby dodać kilka elementów menu do paska ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="407bf-106">To add several menu items to a ContextMenuStrip</span></span>  
  
- <span data-ttu-id="407bf-107">Użyj <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> metodę, aby dodać kilka elementów menu do <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="407bf-107">Use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> method to add several menu items to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
    ```vb  
    Me.contextMenuStrip1.Items.AddRange(New _  
       System.Windows.Forms.ToolStripItem() {Me.toolStripMenuItem1, _  
          Me.toolStripMenuItem2})  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.AddRange(new   
       System.Windows.Forms.ToolStripItem[] {  
          this.toolStripMenuItem1, this.toolStripMenuItem2});  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="407bf-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="407bf-108">See also</span></span>

- [<span data-ttu-id="407bf-109">ContextMenuStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="407bf-109">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)
