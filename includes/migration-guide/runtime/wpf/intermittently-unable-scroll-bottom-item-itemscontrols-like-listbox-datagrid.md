---
ms.openlocfilehash: b92dc8a1c48e83846c3d9a1d86e66629f31b7722
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622119"
---
### <a name="intermittently-unable-to-scroll-to-bottom-item-in-itemscontrols-like-listbox-and-datagrid-when-using-custom-datatemplates"></a><span data-ttu-id="e91b6-101">Sporadycznie nie można przewijać do ostatniego elementu w ItemsControls (na przykład ListBox i DataGrid) przy użyciu niestandardowych szablonów datatemplates</span><span class="sxs-lookup"><span data-stu-id="e91b6-101">Intermittently unable to scroll to bottom item in ItemsControls (like ListBox and DataGrid) when using custom DataTemplates</span></span>

#### <a name="details"></a><span data-ttu-id="e91b6-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e91b6-102">Details</span></span>

<span data-ttu-id="e91b6-103">W niektórych przypadkach usterka w .NET Framework 4,5 powoduje, że w <xref:System.Windows.Controls.ListBox?displayProperty=fullName> <xref:System.Windows.Controls.ComboBox?displayProperty=fullName> <xref:System.Windows.Controls.DataGrid?displayProperty=fullName> przypadku korzystania z niestandardowych szablonów datatemplates ItemsControls (np., itp.).</span><span class="sxs-lookup"><span data-stu-id="e91b6-103">In some instances, a bug in the .NET Framework 4.5 is causing ItemsControls (like <xref:System.Windows.Controls.ListBox?displayProperty=fullName>, <xref:System.Windows.Controls.ComboBox?displayProperty=fullName>, <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>, etc.) to not scroll to their bottom item when using custom DataTemplates.</span></span> <span data-ttu-id="e91b6-104">W przypadku próby przeprowadzenia przewijania po raz drugi (po przeprowadzeniu przewijania kopii zapasowej) działanie zostanie wykonane.</span><span class="sxs-lookup"><span data-stu-id="e91b6-104">If the scrolling is attempted a second time (after scrolling back up), it will work then.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e91b6-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="e91b6-105">Suggestion</span></span>

<span data-ttu-id="e91b6-106">Ten problem został rozwiązany w .NET Framework 4.5.2 i może zostać rozwiązany przez uaktualnienie do tej wersji (lub nowszej) .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e91b6-106">This issue has been fixed in the .NET Framework 4.5.2 and may be addressed by upgrading to that version (or a later version) of the .NET Framework.</span></span> <span data-ttu-id="e91b6-107">Alternatywnie użytkownicy nadal mogą przeciągać paski przewijania do elementów końcowych w tych kolekcjach, ale może być konieczne dwukrotne wykonanie tej czynności.</span><span class="sxs-lookup"><span data-stu-id="e91b6-107">Alternatively, users can still drag scroll bars to the final items in these collections, but may need to try twice to do so successfully.</span></span>

| <span data-ttu-id="e91b6-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="e91b6-108">Name</span></span>    | <span data-ttu-id="e91b6-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="e91b6-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e91b6-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="e91b6-110">Scope</span></span>   |<span data-ttu-id="e91b6-111">Mały</span><span class="sxs-lookup"><span data-stu-id="e91b6-111">Minor</span></span>|
|<span data-ttu-id="e91b6-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="e91b6-112">Version</span></span>|<span data-ttu-id="e91b6-113">4.5</span><span class="sxs-lookup"><span data-stu-id="e91b6-113">4.5</span></span>|
|<span data-ttu-id="e91b6-114">Typ</span><span class="sxs-lookup"><span data-stu-id="e91b6-114">Type</span></span>|<span data-ttu-id="e91b6-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="e91b6-115">Runtime</span></span>|
