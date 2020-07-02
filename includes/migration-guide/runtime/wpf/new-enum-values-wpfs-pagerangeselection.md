---
ms.openlocfilehash: bae6d7c0f8843211c721c68ce6f16000b35b4401
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620454"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a><span data-ttu-id="0f7ec-101">Nowe wartości wyliczeniowe w PageRangeSelection WPF</span><span class="sxs-lookup"><span data-stu-id="0f7ec-101">New enum values in WPF's PageRangeSelection</span></span>

#### <a name="details"></a><span data-ttu-id="0f7ec-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="0f7ec-102">Details</span></span>

<span data-ttu-id="0f7ec-103">Dodano dwóch nowych członków ( <xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> i <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName> ) do <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0f7ec-103">Two new members (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> and <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) have been added to the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> enum.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="0f7ec-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="0f7ec-104">Suggestion</span></span>

<span data-ttu-id="0f7ec-105">W większości przypadków te zmiany nie wpłyną na kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="0f7ec-105">In most cases, these changes won't impact user code.</span></span> <span data-ttu-id="0f7ec-106">Kod, który zależy od określonej liczby elementów istniejących w <xref:System.Enum.GetNames(System.Type)> lub <xref:System.Enum.GetValues(System.Type)> wywołania <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> typu należy zmodyfikować, chociaż.</span><span class="sxs-lookup"><span data-stu-id="0f7ec-106">Code that depends on a particular number of elements existing in <xref:System.Enum.GetNames(System.Type)> or <xref:System.Enum.GetValues(System.Type)> calls on the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> type should be modified, though.</span></span>

| <span data-ttu-id="0f7ec-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="0f7ec-107">Name</span></span>    | <span data-ttu-id="0f7ec-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="0f7ec-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="0f7ec-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="0f7ec-109">Scope</span></span>   |<span data-ttu-id="0f7ec-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="0f7ec-110">Edge</span></span>|
|<span data-ttu-id="0f7ec-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="0f7ec-111">Version</span></span>|<span data-ttu-id="0f7ec-112">4.5</span><span class="sxs-lookup"><span data-stu-id="0f7ec-112">4.5</span></span>|
|<span data-ttu-id="0f7ec-113">Typ</span><span class="sxs-lookup"><span data-stu-id="0f7ec-113">Type</span></span>|<span data-ttu-id="0f7ec-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="0f7ec-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0f7ec-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="0f7ec-115">Affected APIs</span></span>

-<xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType></li></ul>|
