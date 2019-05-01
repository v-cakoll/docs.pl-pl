---
title: 'Instrukcje: Włączanie zmiany kolejności elementów ToolStrip w czasie wykonywania w formularzach Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], examples
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], rearranging controls
- ToolStrip control [Windows Forms], reordering items
ms.assetid: 8480b69a-379f-4dc2-8dcf-365ed93692b2
ms.openlocfilehash: daff9d6d351db514d552225853f977775f8e3204
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941443"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a><span data-ttu-id="95002-102">Instrukcje: Włączanie zmiany kolejności elementów ToolStrip w czasie wykonywania w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95002-102">How to: Enable Reordering of ToolStrip Items at Run Time in Windows Forms</span></span>
<span data-ttu-id="95002-103">Można włączyć użytkownika do zmiany rozmieszczenia <xref:System.Windows.Forms.ToolStripItem> formantów na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="95002-103">You can enable the user to rearrange <xref:System.Windows.Forms.ToolStripItem> controls on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a><span data-ttu-id="95002-104">Aby włączyć rozmieszczania ToolStripItem w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="95002-104">To enable ToolStripItem rearrangement at run time</span></span>  
  
- <span data-ttu-id="95002-105">Ustaw <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="95002-105">Set the <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> property to `true`.</span></span> <span data-ttu-id="95002-106">Domyślnie <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> jest `false`.</span><span class="sxs-lookup"><span data-stu-id="95002-106">By default, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> is `false`.</span></span>  
  
     <span data-ttu-id="95002-107">W czasie wykonywania, użytkownik posiada naciśnięty klawisz ALT i lewego przycisku myszy przeciągnij <xref:System.Windows.Forms.ToolStripItem> do innej lokalizacji na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="95002-107">At run time, the user holds down the ALT key and the left mouse button to drag a <xref:System.Windows.Forms.ToolStripItem> to a different location on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="95002-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="95002-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>
- [<span data-ttu-id="95002-109">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="95002-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="95002-110">ToolStrip, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="95002-110">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="95002-111">ToolStrip — podsumowanie informacji o technologii</span><span class="sxs-lookup"><span data-stu-id="95002-111">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
