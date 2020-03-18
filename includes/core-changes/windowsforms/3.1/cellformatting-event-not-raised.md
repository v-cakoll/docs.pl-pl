---
ms.openlocfilehash: add3ff8faed2e7fab245e5b6f1b9158b7bdd06f5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74567374"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a><span data-ttu-id="bf5ec-101">Zdarzenie CellFormatting nie jest wywoływane, jeśli wyświetlana jest etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="bf5ec-101">CellFormatting event not raised if tooltip is shown</span></span>

<span data-ttu-id="bf5ec-102">A <xref:System.Windows.Forms.DataGridView> pokazuje teraz tekst komórki i etykietki narzędzi błędów po najechaniu kursorem myszy i wybraniu za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="bf5ec-102">A <xref:System.Windows.Forms.DataGridView> now shows a cell's text and error tooltips when hovered by a mouse and when selected via the keyboard.</span></span> <span data-ttu-id="bf5ec-103">Jeśli zostanie wyświetlona <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> etykietka narzędzia, zdarzenie nie zostanie podniesione.</span><span class="sxs-lookup"><span data-stu-id="bf5ec-103">If a tooltip is shown, the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event is not raised.</span></span>

#### <a name="change-description"></a><span data-ttu-id="bf5ec-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="bf5ec-104">Change description</span></span>

<span data-ttu-id="bf5ec-105">Przed .NET Core 3.1, <xref:System.Windows.Forms.DataGridView> który <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> miał `true` właściwość ustawić, aby pokazał etykietkę narzędzia dla komórki tekstu i błędów, gdy komórka została unosząca się kursorem myszy.</span><span class="sxs-lookup"><span data-stu-id="bf5ec-105">Prior to .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that had the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` showed a tooltip for a cell's text and errors when the cell was hovered by a mouse.</span></span> <span data-ttu-id="bf5ec-106">Etykietki narzędzi nie były wyświetlane, gdy komórka została wybrana za pomocą klawiatury (na przykład za pomocą klawisza Tab, klawiszy skrótów lub nawigacji po strzałkach).</span><span class="sxs-lookup"><span data-stu-id="bf5ec-106">Tooltips were not shown when a cell was selected via the keyboard (for example, by using the Tab key, shortcut keys, or arrow navigation).</span></span> <span data-ttu-id="bf5ec-107">Jeśli użytkownik edytował komórkę, a <xref:System.Windows.Forms.DataGridView> następnie, gdy był jeszcze w trybie edycji, <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> najechał <xref:System.Windows.Forms.DataGridView.CellFormatting> na komórkę, która nie miała ustawionej właściwości, zdarzenie zostało podniesione w celu sformatowania tekstu komórki do wyświetlenia w komórce.</span><span class="sxs-lookup"><span data-stu-id="bf5ec-107">If the user edited a cell, and then, while the <xref:System.Windows.Forms.DataGridView> was still in edit mode, hovered over a cell that did not have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set, a <xref:System.Windows.Forms.DataGridView.CellFormatting> event was raised to format the cell's text for display in the cell.</span></span>

<span data-ttu-id="bf5ec-108">Aby spełnić standardy ułatwień dostępu, począwszy <xref:System.Windows.Forms.DataGridView> od <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> .NET `true` Core 3.1, a, który ma właściwość ustawioną na pokazuje etykietki narzędzi dla tekstu komórki i błędy nie tylko po umieszczeniu komórki, ale także wtedy, gdy jest zaznaczona za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="bf5ec-108">To meet accessibility standards, starting in .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that has the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` shows tooltips for a cell's text and errors not only when the cell is hovered, but also when it's selected via the keyboard.</span></span> <span data-ttu-id="bf5ec-109">W wyniku tej zmiany <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzenie *nie* jest wywoływane, gdy <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> komórki, które nie <xref:System.Windows.Forms.DataGridView> mają ustawionej właściwości są unoszące się podczas trybu edycji.</span><span class="sxs-lookup"><span data-stu-id="bf5ec-109">As a consequence of this change, the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is *not* raised when cells that don't have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set are hovered while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span> <span data-ttu-id="bf5ec-110">Zdarzenie nie jest wywoływane, ponieważ zawartość unoszącej się komórki jest wyświetlana jako etykietka narzędzia, a nie wyświetlana w komórce.</span><span class="sxs-lookup"><span data-stu-id="bf5ec-110">The event is not raised because the content of the hovered cell is shown as a tooltip instead of being displayed in the cell.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="bf5ec-111">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="bf5ec-111">Version introduced</span></span>

<span data-ttu-id="bf5ec-112">3.1</span><span class="sxs-lookup"><span data-stu-id="bf5ec-112">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="bf5ec-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="bf5ec-113">Recommended action</span></span>

<span data-ttu-id="bf5ec-114">Refaktoryzuj dowolny kod, który zależy od <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzenia, <xref:System.Windows.Forms.DataGridView> gdy jest w trybie edycji.</span><span class="sxs-lookup"><span data-stu-id="bf5ec-114">Refactor any code that depends on the <xref:System.Windows.Forms.DataGridView.CellFormatting> event while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span>

#### <a name="category"></a><span data-ttu-id="bf5ec-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="bf5ec-115">Category</span></span>

<span data-ttu-id="bf5ec-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bf5ec-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="bf5ec-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="bf5ec-117">Affected APIs</span></span>

<span data-ttu-id="bf5ec-118">Nie wykrywalne za pomocą analizy Interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="bf5ec-118">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
