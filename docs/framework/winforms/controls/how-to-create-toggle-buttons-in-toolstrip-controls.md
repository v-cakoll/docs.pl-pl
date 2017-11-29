---
title: "Porady: tworzenie przycisków przełączania w formantach ToolStrip"
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
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a8529637db7bc4cca011d0992b257d5b8ce9aaff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="d53ae-102">Porady: tworzenie przycisków przełączania w formantach ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d53ae-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>
<span data-ttu-id="d53ae-103">Gdy użytkownik kliknie przycisk przełącznika, pojawi się zapadnięta i zachowuje zapadnięta wygląd, dopóki użytkownik kliknie przycisk ponownie.</span><span class="sxs-lookup"><span data-stu-id="d53ae-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>  
  
### <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="d53ae-104">Aby utworzyć toggling element ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="d53ae-104">To create a toggling ToolStripButton</span></span>  
  
-   <span data-ttu-id="d53ae-105">Użyj kodu, takie jak w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="d53ae-105">Use code such as the following code example.</span></span> <span data-ttu-id="d53ae-106">Ten kod przyjęto założenie, że formularz zawiera <xref:System.Windows.Forms.ToolStrip> kontroli, a jego <xref:System.Windows.Forms.ToolStrip.Items%2A> kolekcja zawiera <xref:System.Windows.Forms.ToolStripButton> o nazwie `toolStripButton1`.</span><span class="sxs-lookup"><span data-stu-id="d53ae-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="d53ae-107">Założono również, że masz wywołuje program obsługi zdarzeń `toolStripButton1_CheckedChanged`.</span><span class="sxs-lookup"><span data-stu-id="d53ae-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>  
  
    ```vb  
    toolStripButton1.CheckOnClick = True  
    toolStripButton1.CheckedChanged AddressOf _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
    ```csharp  
    toolStripButton1.CheckOnClick = true;  
    toolStripButton1.CheckedChanged += new _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d53ae-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d53ae-108">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripButton>  
 [<span data-ttu-id="d53ae-109">Informacje o formancie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="d53ae-109">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
