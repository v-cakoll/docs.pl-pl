---
ms.openlocfilehash: b736ab743a628fdcbc53c5ee51551e5dad986885
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888140"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a><span data-ttu-id="a28ce-101">Zdarzenie CellFormatting nie jest wywoływane, jeśli wyświetlana jest etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="a28ce-101">CellFormatting event not raised if tooltip is shown</span></span>

<span data-ttu-id="a28ce-102">A <xref:System.Windows.Forms.DataGridView> pokazuje teraz tekst i etykietki błędów komórki po umieszczeniu wskaźnika myszy i wybraniu za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="a28ce-102">A <xref:System.Windows.Forms.DataGridView> now shows a cell's text and error tooltips when hovered by a mouse and when selected via the keyboard.</span></span> <span data-ttu-id="a28ce-103">Jeśli etykietka narzędzia jest <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> wyświetlana, zdarzenie nie jest wywoływane.</span><span class="sxs-lookup"><span data-stu-id="a28ce-103">If a tooltip is shown, the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event is not raised.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a28ce-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="a28ce-104">Change description</span></span>

<span data-ttu-id="a28ce-105">Przed .NET Core 3.1, <xref:System.Windows.Forms.DataGridView> a, który miał <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> ustawioną właściwość, aby `true` wyświetlić etykietkę narzędzia dla tekstu komórki i błędy, gdy komórka została naniesione przez mysz.</span><span class="sxs-lookup"><span data-stu-id="a28ce-105">Prior to .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that had the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` showed a tooltip for a cell's text and errors when the cell was hovered by a mouse.</span></span> <span data-ttu-id="a28ce-106">Etykietki narzędzi nie były wyświetlane, gdy komórka została wybrana za pomocą klawiatury (na przykład za pomocą klawisza Tab, klawiszy skrótów lub nawigacji strzałką).</span><span class="sxs-lookup"><span data-stu-id="a28ce-106">Tooltips were not shown when a cell was selected via the keyboard (for example, by using the Tab key, shortcut keys, or arrow navigation).</span></span> <span data-ttu-id="a28ce-107">Jeśli użytkownik edytował komórkę, a <xref:System.Windows.Forms.DataGridView> następnie, gdy był jeszcze w trybie edycji, najechał kursorem na komórkę, która nie miała ustawionego <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> właściwości, <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzenie zostało podniesione w celu sformaowania tekstu komórki do wyświetlenia w komórce.</span><span class="sxs-lookup"><span data-stu-id="a28ce-107">If the user edited a cell, and then, while the <xref:System.Windows.Forms.DataGridView> was still in edit mode, hovered over a cell that did not have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set, a <xref:System.Windows.Forms.DataGridView.CellFormatting> event was raised to format the cell's text for display in the cell.</span></span>

<span data-ttu-id="a28ce-108">Aby spełnić standardy ułatwień dostępu, począwszy od <xref:System.Windows.Forms.DataGridView> .NET <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> Core `true` 3.1, a, który ma właściwość ustawioną na wyświetla etykietki dla tekstu komórki i błędy nie tylko po umieszczeniu komórki, ale także wtedy, gdy jest zaznaczona za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="a28ce-108">To meet accessibility standards, starting in .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that has the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` shows tooltips for a cell's text and errors not only when the cell is hovered, but also when it's selected via the keyboard.</span></span> <span data-ttu-id="a28ce-109">W wyniku tej zmiany <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzenie *nie* jest wywoływane, gdy <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> komórki, które nie <xref:System.Windows.Forms.DataGridView> mają zestawu właściwości są najechane, gdy jest w trybie edycji.</span><span class="sxs-lookup"><span data-stu-id="a28ce-109">As a consequence of this change, the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is *not* raised when cells that don't have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set are hovered while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span> <span data-ttu-id="a28ce-110">Zdarzenie nie jest wywoływane, ponieważ zawartość aktywowanej komórki jest wyświetlana jako etykietka narzędzia, a nie wyświetlana w komórce.</span><span class="sxs-lookup"><span data-stu-id="a28ce-110">The event is not raised because the content of the hovered cell is shown as a tooltip instead of being displayed in the cell.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a28ce-111">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="a28ce-111">Version introduced</span></span>

<span data-ttu-id="a28ce-112">3.1</span><span class="sxs-lookup"><span data-stu-id="a28ce-112">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a28ce-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="a28ce-113">Recommended action</span></span>

<span data-ttu-id="a28ce-114">Refaktoryzuje dowolny <xref:System.Windows.Forms.DataGridView.CellFormatting> kod, <xref:System.Windows.Forms.DataGridView> który zależy od zdarzenia, gdy jest w trybie edycji.</span><span class="sxs-lookup"><span data-stu-id="a28ce-114">Refactor any code that depends on the <xref:System.Windows.Forms.DataGridView.CellFormatting> event while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span>

#### <a name="category"></a><span data-ttu-id="a28ce-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="a28ce-115">Category</span></span>

<span data-ttu-id="a28ce-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a28ce-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a28ce-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="a28ce-117">Affected APIs</span></span>

<span data-ttu-id="a28ce-118">Brak</span><span class="sxs-lookup"><span data-stu-id="a28ce-118">None</span></span>

<!-- 

### Affected APIs

Not detectable via API analysis.

-->
