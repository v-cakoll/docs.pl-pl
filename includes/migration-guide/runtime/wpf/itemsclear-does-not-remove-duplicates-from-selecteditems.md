---
ms.openlocfilehash: 75f176133697056bab9349ba1d18d7a0e1aa7da2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620125"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a><span data-ttu-id="a8a40-101">Elementy. Clear nie usuwa duplikatów z SelectedItems</span><span class="sxs-lookup"><span data-stu-id="a8a40-101">Items.Clear does not remove duplicates from SelectedItems</span></span>

#### <a name="details"></a><span data-ttu-id="a8a40-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="a8a40-102">Details</span></span>

<span data-ttu-id="a8a40-103">Załóżmy, że selektor (z włączoną obsługą wielu zaznaczeń) ma duplikaty w <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> kolekcji — ten sam element występuje więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="a8a40-103">Suppose a Selector (with multiple selection enabled) has duplicates in its <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> collection - the same item appears more than once.</span></span>  <span data-ttu-id="a8a40-104">Usunięcie tych elementów ze źródła danych (np. przez wywoływanie elementów. Clear) nie powiodło się usunięcie ich z <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> ; tylko pierwsze wystąpienie zostanie usunięte.</span><span class="sxs-lookup"><span data-stu-id="a8a40-104">Removing those items from the data source (e.g. by calling Items.Clear) fails to remove them from <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName>; only the first instance is removed.</span></span> <span data-ttu-id="a8a40-105">Ponadto kolejne użycie <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (np. SelectedItems. Clear ()) może napotkać problemy, takie jak <xref:System.ArgumentException?displayProperty=fullName> , ponieważ <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> zawiera elementy, które nie znajdują się już w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="a8a40-105">Furthermore, subsequent use of <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (e.g. SelectedItems.Clear()) can encounter problems such as <xref:System.ArgumentException?displayProperty=fullName>, because <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> contains items that are no longer in the data source.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a8a40-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="a8a40-106">Suggestion</span></span>

<span data-ttu-id="a8a40-107">Uaktualnij, jeśli to możliwe, aby .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="a8a40-107">Upgrade if possible to .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="a8a40-108">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a8a40-108">Name</span></span>    | <span data-ttu-id="a8a40-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="a8a40-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a8a40-110">Zakres</span><span class="sxs-lookup"><span data-stu-id="a8a40-110">Scope</span></span>   |<span data-ttu-id="a8a40-111">Mały</span><span class="sxs-lookup"><span data-stu-id="a8a40-111">Minor</span></span>|
|<span data-ttu-id="a8a40-112">Wersja</span><span class="sxs-lookup"><span data-stu-id="a8a40-112">Version</span></span>|<span data-ttu-id="a8a40-113">4.5</span><span class="sxs-lookup"><span data-stu-id="a8a40-113">4.5</span></span>|
|<span data-ttu-id="a8a40-114">Typ</span><span class="sxs-lookup"><span data-stu-id="a8a40-114">Type</span></span>|<span data-ttu-id="a8a40-115">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="a8a40-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a8a40-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="a8a40-116">Affected APIs</span></span>

-<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|
