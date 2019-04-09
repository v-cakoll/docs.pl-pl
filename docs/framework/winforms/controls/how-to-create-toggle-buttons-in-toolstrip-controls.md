---
title: 'Instrukcje: tworzenie przycisków przełączania w kontrolkach ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: e688e9a220e6c82caa2d107589b5ca9a1e59e72b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091255"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="24528-102">Instrukcje: tworzenie przycisków przełączania w kontrolkach ToolStrip</span><span class="sxs-lookup"><span data-stu-id="24528-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>
<span data-ttu-id="24528-103">Gdy użytkownik kliknie przycisk przełączania, pojawi się wklęsłą i zachowuje wklęsłą wygląd, dopóki użytkownik kliknie przycisk ponownie.</span><span class="sxs-lookup"><span data-stu-id="24528-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>  
  
### <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="24528-104">Aby utworzyć toggling element ToolStripButton</span><span class="sxs-lookup"><span data-stu-id="24528-104">To create a toggling ToolStripButton</span></span>  
  
-   <span data-ttu-id="24528-105">Należy użyć kodu takiego jak w poniższym przykładzie kodu.</span><span class="sxs-lookup"><span data-stu-id="24528-105">Use code such as the following code example.</span></span> <span data-ttu-id="24528-106">Ten kod zakłada, że formularz zawiera <xref:System.Windows.Forms.ToolStrip> kontroli, a jego <xref:System.Windows.Forms.ToolStrip.Items%2A> kolekcja zawiera <xref:System.Windows.Forms.ToolStripButton> o nazwie `toolStripButton1`.</span><span class="sxs-lookup"><span data-stu-id="24528-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="24528-107">Zakłada również, że masz program obsługi zdarzeń wywołuje `toolStripButton1_CheckedChanged`.</span><span class="sxs-lookup"><span data-stu-id="24528-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="24528-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24528-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStripButton>
- [<span data-ttu-id="24528-109">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="24528-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
