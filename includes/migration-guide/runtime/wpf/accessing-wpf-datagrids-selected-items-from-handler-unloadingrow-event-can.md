---
ms.openlocfilehash: 7ac0cac53ab2fa7657d0ae58f11d9e777631acc9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620441"
---
### <a name="accessing-a-wpf-datagrids-selected-items-from-a-handler-of-the-datagrids-unloadingrow-event-can-cause-a-nullreferenceexception"></a><span data-ttu-id="2366e-101">Dostęp do wybranych elementów programu WPF DataGrid z procedury obsługi zdarzenia UnloadingRow elementu DataGrid może spowodować wystąpienie elementu NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="2366e-101">Accessing a WPF DataGrid's selected items from a handler of the DataGrid's UnloadingRow event can cause a NullReferenceException</span></span>

#### <a name="details"></a><span data-ttu-id="2366e-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="2366e-102">Details</span></span>

<span data-ttu-id="2366e-103">Ze względu na usterkę w .NET Framework 4,5, obsługa zdarzeń dla <xref:System.Windows.Controls.DataGrid> zdarzeń obejmujących usunięcie wiersza może spowodować, że <xref:System.NullReferenceException?displayProperty=fullName> zostanie wygenerowany, jeśli uzyskują dostęp do <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> właściwości lub <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="2366e-103">Due to a bug in the .NET Framework 4.5, event handlers for <xref:System.Windows.Controls.DataGrid> events involving the removal of a row can cause a <xref:System.NullReferenceException?displayProperty=fullName> to be thrown if they access the <xref:System.Windows.Controls.DataGrid>'s <xref:System.Windows.Controls.Primitives.Selector.SelectedItem?displayProperty=fullName> or <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> properties.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2366e-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="2366e-104">Suggestion</span></span>

<span data-ttu-id="2366e-105">Ten problem został rozwiązany w .NET Framework 4,6 i może zostać rozwiązany przez uaktualnienie do tej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2366e-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="2366e-106">Nazwa</span><span class="sxs-lookup"><span data-stu-id="2366e-106">Name</span></span>    | <span data-ttu-id="2366e-107">Wartość</span><span class="sxs-lookup"><span data-stu-id="2366e-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2366e-108">Zakres</span><span class="sxs-lookup"><span data-stu-id="2366e-108">Scope</span></span>   |<span data-ttu-id="2366e-109">Mały</span><span class="sxs-lookup"><span data-stu-id="2366e-109">Minor</span></span>|
|<span data-ttu-id="2366e-110">Wersja</span><span class="sxs-lookup"><span data-stu-id="2366e-110">Version</span></span>|<span data-ttu-id="2366e-111">4.5</span><span class="sxs-lookup"><span data-stu-id="2366e-111">4.5</span></span>|
|<span data-ttu-id="2366e-112">Typ</span><span class="sxs-lookup"><span data-stu-id="2366e-112">Type</span></span>|<span data-ttu-id="2366e-113">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="2366e-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2366e-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="2366e-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.DataGrid.UnloadingRow?displayProperty=nameWithType></li><li><xref:System.Windows.Controls.DataGrid.UnloadingRowDetails?displayProperty=nameWithType></li></ul>|
