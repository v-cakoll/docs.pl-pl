---
ms.openlocfilehash: 4a34a64eba72ea24c1d830566565ce4fbee8e5b7
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721671"
---
### <a name="cellformatting-event-not-raised-if-tooltip-is-shown"></a><span data-ttu-id="ad5e2-101">Zdarzenie CellFormatting nie zostało zgłoszone, jeśli jest wyświetlana etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="ad5e2-101">CellFormatting event not raised if tooltip is shown</span></span>

<span data-ttu-id="ad5e2-102"><xref:System.Windows.Forms.DataGridView>Po umieszczeniu wskaźnika myszy i wybraniu za pośrednictwem klawiatury jest teraz wyświetlana etykietka tekstowa i błędów w komórce.</span><span class="sxs-lookup"><span data-stu-id="ad5e2-102">A <xref:System.Windows.Forms.DataGridView> now shows a cell's text and error tooltips when hovered by a mouse and when selected via the keyboard.</span></span> <span data-ttu-id="ad5e2-103">Jeśli zostanie wyświetlona etykietka narzędzia, <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> zdarzenie nie zostanie zgłoszone.</span><span class="sxs-lookup"><span data-stu-id="ad5e2-103">If a tooltip is shown, the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event is not raised.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ad5e2-104">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="ad5e2-104">Change description</span></span>

<span data-ttu-id="ad5e2-105">Przed platformą .NET Core 3,1, <xref:System.Windows.Forms.DataGridView> która ma <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> ustawioną właściwość, aby była `true` wyświetlana etykietka narzędzia dla tekstu i błędów komórki, gdy komórka została aktywowana przez mysz.</span><span class="sxs-lookup"><span data-stu-id="ad5e2-105">Prior to .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that had the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` showed a tooltip for a cell's text and errors when the cell was hovered by a mouse.</span></span> <span data-ttu-id="ad5e2-106">Etykietki narzędzi nie były wyświetlane, gdy komórka została wybrana za pośrednictwem klawiatury (na przykład za pomocą klawisza Tab, klawiszy skrótów lub nawigacji strzałek).</span><span class="sxs-lookup"><span data-stu-id="ad5e2-106">Tooltips were not shown when a cell was selected via the keyboard (for example, by using the Tab key, shortcut keys, or arrow navigation).</span></span> <span data-ttu-id="ad5e2-107">Jeśli użytkownik edytował komórkę, a następnie, gdy <xref:System.Windows.Forms.DataGridView> był nadal w trybie edycji, przesuwa się nad komórką, która nie ma <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> ustawionej właściwości, <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzenie zostało wywołane w celu sformatowania tekstu komórki na potrzeby wyświetlania w komórce.</span><span class="sxs-lookup"><span data-stu-id="ad5e2-107">If the user edited a cell, and then, while the <xref:System.Windows.Forms.DataGridView> was still in edit mode, hovered over a cell that did not have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set, a <xref:System.Windows.Forms.DataGridView.CellFormatting> event was raised to format the cell's text for display in the cell.</span></span>

<span data-ttu-id="ad5e2-108">Aby spełnić standardy dostępności, począwszy od platformy .NET Core 3,1, <xref:System.Windows.Forms.DataGridView> która ma <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> ustawioną właściwość `true` pokazującą etykietki narzędzi dla tekstu i błędów w komórce, nie tylko wtedy, gdy komórka jest aktywowany, ale również gdy jest zaznaczona za pomocą klawiatury.</span><span class="sxs-lookup"><span data-stu-id="ad5e2-108">To meet accessibility standards, starting in .NET Core 3.1, a <xref:System.Windows.Forms.DataGridView> that has the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A> property set to `true` shows tooltips for a cell's text and errors not only when the cell is hovered, but also when it's selected via the keyboard.</span></span> <span data-ttu-id="ad5e2-109">W związku z tą zmianą <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzenie *nie* jest zgłaszane, gdy komórki, które nie mają <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> ustawionej właściwości są przesuwane, gdy <xref:System.Windows.Forms.DataGridView> jest w trybie edycji.</span><span class="sxs-lookup"><span data-stu-id="ad5e2-109">As a consequence of this change, the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is *not* raised when cells that don't have the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText> property set are hovered while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span> <span data-ttu-id="ad5e2-110">Zdarzenie nie zostało zgłoszone, ponieważ zawartość przesuwanej komórki jest pokazywana jako etykietka narzędzia, a nie wyświetlana w komórce.</span><span class="sxs-lookup"><span data-stu-id="ad5e2-110">The event is not raised because the content of the hovered cell is shown as a tooltip instead of being displayed in the cell.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ad5e2-111">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="ad5e2-111">Version introduced</span></span>

<span data-ttu-id="ad5e2-112">3,1</span><span class="sxs-lookup"><span data-stu-id="ad5e2-112">3.1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ad5e2-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="ad5e2-113">Recommended action</span></span>

<span data-ttu-id="ad5e2-114">Refaktoryzacja dowolnego kodu, który zależy od zdarzenia, <xref:System.Windows.Forms.DataGridView.CellFormatting> podczas gdy <xref:System.Windows.Forms.DataGridView> jest w trybie edycji.</span><span class="sxs-lookup"><span data-stu-id="ad5e2-114">Refactor any code that depends on the <xref:System.Windows.Forms.DataGridView.CellFormatting> event while the <xref:System.Windows.Forms.DataGridView> is in edit mode.</span></span>

#### <a name="category"></a><span data-ttu-id="ad5e2-115">Kategoria</span><span class="sxs-lookup"><span data-stu-id="ad5e2-115">Category</span></span>

<span data-ttu-id="ad5e2-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ad5e2-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ad5e2-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="ad5e2-117">Affected APIs</span></span>

<span data-ttu-id="ad5e2-118">Brak</span><span class="sxs-lookup"><span data-stu-id="ad5e2-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
