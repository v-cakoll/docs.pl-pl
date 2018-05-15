---
title: 'Porady: zarządzanie przepełnieniem elementu ToolStrip w formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], managing overflow
- toolbars [Windows Forms], managing overflow
- examples [Windows Forms], toolbars
- CanOverflow property
ms.assetid: fa10e0ad-4cbf-4c0d-9082-359c2f855d4e
ms.openlocfilehash: 32bbc06320f0dc7f096a4b9021bebfbefedaf8f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a><span data-ttu-id="a47cd-102">Porady: zarządzanie przepełnieniem elementu ToolStrip w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a47cd-102">How to: Manage ToolStrip Overflow in Windows Forms</span></span>
<span data-ttu-id="a47cd-103">Gdy wszystkie elementy na <xref:System.Windows.Forms.ToolStrip> formantu nie mieszczą się w przydzielonym miejscu, można włączyć funkcji przepełnienie na <xref:System.Windows.Forms.ToolStrip> i określają zachowanie przepełnienie określonych <xref:System.Windows.Forms.ToolStripItem>s.</span><span class="sxs-lookup"><span data-stu-id="a47cd-103">When all the items on a <xref:System.Windows.Forms.ToolStrip> control do not fit in the allotted space, you can enable overflow functionality on the <xref:System.Windows.Forms.ToolStrip> and determine the overflow behavior of specific <xref:System.Windows.Forms.ToolStripItem>s.</span></span>  
  
 <span data-ttu-id="a47cd-104">Po dodaniu <xref:System.Windows.Forms.ToolStripItem>, które wymagają więcej miejsca niż przydzielony <xref:System.Windows.Forms.ToolStrip> danego formularza bieżący rozmiar, <xref:System.Windows.Forms.ToolStripOverflowButton> automatycznie pojawia się na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="a47cd-104">When you add <xref:System.Windows.Forms.ToolStripItem>s that require more space than is allotted to the <xref:System.Windows.Forms.ToolStrip> given the form's current size, a <xref:System.Windows.Forms.ToolStripOverflowButton> automatically appears on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="a47cd-105"><xref:System.Windows.Forms.ToolStripOverflowButton> Pojawia się, i włączone przepełnienie elementy są przenoszone do menu przeciążenia listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="a47cd-105">The <xref:System.Windows.Forms.ToolStripOverflowButton> appears, and overflow-enabled items are moved into the drop-down overflow menu.</span></span> <span data-ttu-id="a47cd-106">Dzięki temu można dostosować i ustalić ich priorytety jak Twoje <xref:System.Windows.Forms.ToolStrip> elementów poprawnie dostosować do różnych rozmiarów.</span><span class="sxs-lookup"><span data-stu-id="a47cd-106">This allows you to customize and prioritize how your <xref:System.Windows.Forms.ToolStrip> items properly adjust to different form sizes.</span></span> <span data-ttu-id="a47cd-107">Można także zmienić wygląd elementów, gdy należą one do przeciążenia przy użyciu <xref:System.Windows.Forms.ToolStripItem.Placement%2A> i <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> właściwości i <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a47cd-107">You can also change the appearance of your items when they fall into the overflow by using the <xref:System.Windows.Forms.ToolStripItem.Placement%2A> and <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> properties and the <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> event.</span></span> <span data-ttu-id="a47cd-108">Jeśli w czasie projektowania lub czas wykonywania powiększyć więcej formularza <xref:System.Windows.Forms.ToolStripItem>s mogą być wyświetlane w głównym <xref:System.Windows.Forms.ToolStrip> i <xref:System.Windows.Forms.ToolStripOverflowButton> nawet może zniknąć dopóki zmniejszyć rozmiar formularza.</span><span class="sxs-lookup"><span data-stu-id="a47cd-108">If you enlarge the form at either design time or run time, more <xref:System.Windows.Forms.ToolStripItem>s can be displayed on the main <xref:System.Windows.Forms.ToolStrip> and the <xref:System.Windows.Forms.ToolStripOverflowButton> might even disappear until you decrease the size of the form.</span></span>  
  
### <a name="to-enable-overflow-on-a-toolstrip-control"></a><span data-ttu-id="a47cd-109">Aby włączyć przepełnienie w formancie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="a47cd-109">To enable overflow on a ToolStrip control</span></span>  
  
-   <span data-ttu-id="a47cd-110">Upewnij się, że <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> nie ustawiono właściwości `false` dla <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="a47cd-110">Ensure that the <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> property is not set to `false` for the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="a47cd-111">Wartość domyślna to `True`.</span><span class="sxs-lookup"><span data-stu-id="a47cd-111">The default is `True`.</span></span>  
  
     <span data-ttu-id="a47cd-112">Podczas <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> jest `True` (ustawienie domyślne), <xref:System.Windows.Forms.ToolStripItem> są wysyłane do menu rozwijanego przepełnienie podczas zawartość <xref:System.Windows.Forms.ToolStripItem> przekracza szerokość poziomego <xref:System.Windows.Forms.ToolStrip> lub wysokości pionowym <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="a47cd-112">When <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> is `True` (the default), a <xref:System.Windows.Forms.ToolStripItem> is sent to the drop-down overflow menu when the content of the <xref:System.Windows.Forms.ToolStripItem> exceeds the width of a horizontal <xref:System.Windows.Forms.ToolStrip> or the height of a vertical <xref:System.Windows.Forms.ToolStrip>.</span></span>  
  
### <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a><span data-ttu-id="a47cd-113">Aby określić zachowanie Przepełnienie elementu ToolStripItem określonych</span><span class="sxs-lookup"><span data-stu-id="a47cd-113">To specify overflow behavior of a specific ToolStripItem</span></span>  
  
-   <span data-ttu-id="a47cd-114">Ustaw <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> właściwość <xref:System.Windows.Forms.ToolStripItem> na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="a47cd-114">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the <xref:System.Windows.Forms.ToolStripItem> to the desired value.</span></span> <span data-ttu-id="a47cd-115">Możliwości są `Always`, `Never`, i `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="a47cd-115">The possibilities are `Always`, `Never`, and `AsNeeded`.</span></span> <span data-ttu-id="a47cd-116">Defaultis `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="a47cd-116">The defaultis `AsNeeded`.</span></span>  
  
    ```vb  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never  
    ```  
  
    ```csharp  
    toolStripTextBox1.Overflow = _  
    System.Windows.Forms.ToolStripItemOverflow.Never;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a47cd-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a47cd-117">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripOverflowButton>  
 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [<span data-ttu-id="a47cd-118">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="a47cd-118">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [<span data-ttu-id="a47cd-119">ToolStrip, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="a47cd-119">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="a47cd-120">ToolStrip — podsumowanie informacji o technologii</span><span class="sxs-lookup"><span data-stu-id="a47cd-120">ToolStrip Technology Summary</span></span>](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
