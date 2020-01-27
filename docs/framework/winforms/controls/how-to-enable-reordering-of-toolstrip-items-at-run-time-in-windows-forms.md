---
title: 'Porady: włączenie zmiany kolejności elementów ToolStrip w czasie wykonywania'
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
ms.openlocfilehash: 44b52bf997819f090569d08eb395d8af18f61370
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745476"
---
# <a name="how-to-enable-reordering-of-toolstrip-items-at-run-time-in-windows-forms"></a><span data-ttu-id="c3ea6-102">Porady: włączenie zmiany kolejności elementów ToolStrip w czasie wykonywania w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c3ea6-102">How to: Enable Reordering of ToolStrip Items at Run Time in Windows Forms</span></span>
<span data-ttu-id="c3ea6-103">Można umożliwić użytkownikowi zmianę rozmieszczenia formantów <xref:System.Windows.Forms.ToolStripItem> w <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="c3ea6-103">You can enable the user to rearrange <xref:System.Windows.Forms.ToolStripItem> controls on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-enable-toolstripitem-rearrangement-at-run-time"></a><span data-ttu-id="c3ea6-104">Aby włączyć ponowne rozmieszczanie elementu ToolStripItem w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="c3ea6-104">To enable ToolStripItem rearrangement at run time</span></span>  
  
- <span data-ttu-id="c3ea6-105">Ustaw <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="c3ea6-105">Set the <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> property to `true`.</span></span> <span data-ttu-id="c3ea6-106">Domyślnie <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> jest `false`.</span><span class="sxs-lookup"><span data-stu-id="c3ea6-106">By default, <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A> is `false`.</span></span>  
  
     <span data-ttu-id="c3ea6-107">W czasie wykonywania użytkownik ma wciśnięty klawisz ALT i lewy przycisk myszy, aby przeciągnąć <xref:System.Windows.Forms.ToolStripItem> do innej lokalizacji na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="c3ea6-107">At run time, the user holds down the ALT key and the left mouse button to drag a <xref:System.Windows.Forms.ToolStripItem> to a different location on the <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
    ```vb  
    toolStrip1.AllowItemReorder = True  
    ```  
  
    ```csharp  
    toolStrip1.AllowItemReorder = true;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="c3ea6-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3ea6-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.AllowItemReorder%2A>
- [<span data-ttu-id="c3ea6-109">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="c3ea6-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="c3ea6-110">ToolStrip, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="c3ea6-110">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="c3ea6-111">ToolStrip — podsumowanie informacji o technologii</span><span class="sxs-lookup"><span data-stu-id="c3ea6-111">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
