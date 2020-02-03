---
title: 'Porady: zarządzanie przepełnieniem elementu ToolStrip'
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
ms.openlocfilehash: 52cc02e626bee2d2457355028ecddc17e462d8fa
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736149"
---
# <a name="how-to-manage-toolstrip-overflow-in-windows-forms"></a><span data-ttu-id="3f06c-102">Porady: zarządzanie przepełnieniem elementu ToolStrip w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3f06c-102">How to: Manage ToolStrip Overflow in Windows Forms</span></span>

<span data-ttu-id="3f06c-103">Gdy wszystkie elementy w formancie <xref:System.Windows.Forms.ToolStrip> nie mieszczą się w wyznaczonym miejscu, można włączyć funkcję przepełniania na <xref:System.Windows.Forms.ToolStrip> i określić zachowanie przepełnienia dla konkretnych <xref:System.Windows.Forms.ToolStripItem>s.</span><span class="sxs-lookup"><span data-stu-id="3f06c-103">When all the items on a <xref:System.Windows.Forms.ToolStrip> control do not fit in the allotted space, you can enable overflow functionality on the <xref:System.Windows.Forms.ToolStrip> and determine the overflow behavior of specific <xref:System.Windows.Forms.ToolStripItem>s.</span></span>

<span data-ttu-id="3f06c-104">Po dodaniu <xref:System.Windows.Forms.ToolStripItem>s, które wymagają więcej miejsca niż jest przydzielony do <xref:System.Windows.Forms.ToolStrip> o bieżącym rozmiarze formularza, <xref:System.Windows.Forms.ToolStripOverflowButton> automatycznie pojawia się na <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="3f06c-104">When you add <xref:System.Windows.Forms.ToolStripItem>s that require more space than is allotted to the <xref:System.Windows.Forms.ToolStrip> given the form's current size, a <xref:System.Windows.Forms.ToolStripOverflowButton> automatically appears on the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="3f06c-105"><xref:System.Windows.Forms.ToolStripOverflowButton> pojawia się, a elementy z obsługą przepełnienia są przenoszone do menu przepełnienie rozwijane.</span><span class="sxs-lookup"><span data-stu-id="3f06c-105">The <xref:System.Windows.Forms.ToolStripOverflowButton> appears, and overflow-enabled items are moved into the drop-down overflow menu.</span></span> <span data-ttu-id="3f06c-106">Umożliwia to dostosowanie i ustalanie priorytetów, jak elementy <xref:System.Windows.Forms.ToolStrip> prawidłowo dostosowują się do różnych rozmiarów.</span><span class="sxs-lookup"><span data-stu-id="3f06c-106">This allows you to customize and prioritize how your <xref:System.Windows.Forms.ToolStrip> items properly adjust to different form sizes.</span></span> <span data-ttu-id="3f06c-107">Możesz również zmienić wygląd elementów po ich przepełnieniu przy użyciu właściwości <xref:System.Windows.Forms.ToolStripItem.Placement%2A> i <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> oraz zdarzenia <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>.</span><span class="sxs-lookup"><span data-stu-id="3f06c-107">You can also change the appearance of your items when they fall into the overflow by using the <xref:System.Windows.Forms.ToolStripItem.Placement%2A> and <xref:System.Windows.Forms.ToolStripOverflow.DisplayedItems%2A?displayProperty=nameWithType> properties and the <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> event.</span></span> <span data-ttu-id="3f06c-108">W przypadku powiększania formularza w czasie projektowania lub czasu wykonywania więcej <xref:System.Windows.Forms.ToolStripItem>s można wyświetlić na głównym <xref:System.Windows.Forms.ToolStrip>, a <xref:System.Windows.Forms.ToolStripOverflowButton> może nawet zniknąć do momentu zmniejszenia rozmiaru formularza.</span><span class="sxs-lookup"><span data-stu-id="3f06c-108">If you enlarge the form at either design time or run time, more <xref:System.Windows.Forms.ToolStripItem>s can be displayed on the main <xref:System.Windows.Forms.ToolStrip> and the <xref:System.Windows.Forms.ToolStripOverflowButton> might even disappear until you decrease the size of the form.</span></span>

## <a name="to-enable-overflow-on-a-toolstrip-control"></a><span data-ttu-id="3f06c-109">Aby włączyć przepełnienie na formancie ToolStrip</span><span class="sxs-lookup"><span data-stu-id="3f06c-109">To enable overflow on a ToolStrip control</span></span>

- <span data-ttu-id="3f06c-110">Upewnij się, że właściwość <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> nie jest ustawiona na `false` dla <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="3f06c-110">Ensure that the <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> property is not set to `false` for the <xref:System.Windows.Forms.ToolStrip>.</span></span> <span data-ttu-id="3f06c-111">Wartość domyślna to `True`.</span><span class="sxs-lookup"><span data-stu-id="3f06c-111">The default is `True`.</span></span>

     <span data-ttu-id="3f06c-112">Gdy <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> jest `True` (domyślnie), <xref:System.Windows.Forms.ToolStripItem> jest wysyłana do menu przepełnienia listy rozwijanej, gdy zawartość <xref:System.Windows.Forms.ToolStripItem> przekroczy szerokość <xref:System.Windows.Forms.ToolStrip> poziomej lub wysokość <xref:System.Windows.Forms.ToolStrip>pionowej.</span><span class="sxs-lookup"><span data-stu-id="3f06c-112">When <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A> is `True` (the default), a <xref:System.Windows.Forms.ToolStripItem> is sent to the drop-down overflow menu when the content of the <xref:System.Windows.Forms.ToolStripItem> exceeds the width of a horizontal <xref:System.Windows.Forms.ToolStrip> or the height of a vertical <xref:System.Windows.Forms.ToolStrip>.</span></span>

## <a name="to-specify-overflow-behavior-of-a-specific-toolstripitem"></a><span data-ttu-id="3f06c-113">Aby określić zachowanie przepełnienia dla określonego elementu ToolStripItem</span><span class="sxs-lookup"><span data-stu-id="3f06c-113">To specify overflow behavior of a specific ToolStripItem</span></span>

- <span data-ttu-id="3f06c-114">Ustaw właściwość <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> <xref:System.Windows.Forms.ToolStripItem> na żądaną wartość.</span><span class="sxs-lookup"><span data-stu-id="3f06c-114">Set the <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> property of the <xref:System.Windows.Forms.ToolStripItem> to the desired value.</span></span> <span data-ttu-id="3f06c-115">Możliwości są `Always`, `Never`i `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="3f06c-115">The possibilities are `Always`, `Never`, and `AsNeeded`.</span></span> <span data-ttu-id="3f06c-116">Wartość domyślna to `AsNeeded`.</span><span class="sxs-lookup"><span data-stu-id="3f06c-116">The default is `AsNeeded`.</span></span>

    ```vb
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never
    ```

    ```csharp
    toolStripTextBox1.Overflow = _
    System.Windows.Forms.ToolStripItemOverflow.Never;
    ```

## <a name="see-also"></a><span data-ttu-id="3f06c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f06c-117">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripOverflowButton>
- <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>
- <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>
- [<span data-ttu-id="3f06c-118">ToolStrip, kontrolka — omówienie</span><span class="sxs-lookup"><span data-stu-id="3f06c-118">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
- [<span data-ttu-id="3f06c-119">ToolStrip, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="3f06c-119">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="3f06c-120">ToolStrip — podsumowanie informacji o technologii</span><span class="sxs-lookup"><span data-stu-id="3f06c-120">ToolStrip Technology Summary</span></span>](toolstrip-technology-summary.md)
