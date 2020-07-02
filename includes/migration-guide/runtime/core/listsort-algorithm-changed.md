---
ms.openlocfilehash: 9dada93c3330331064b7a944d97d61edb4dea299
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620248"
---
### <a name="listsort-algorithm-changed"></a><span data-ttu-id="c6d22-101">Zmieniono algorytm list. Sort</span><span class="sxs-lookup"><span data-stu-id="c6d22-101">List.Sort algorithm changed</span></span>

#### <a name="details"></a><span data-ttu-id="c6d22-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="c6d22-102">Details</span></span>

<span data-ttu-id="c6d22-103">Począwszy od .NET Framework 4,5, <xref:System.Collections.Generic.List%601?displayProperty=fullName> algorytm sortowania został zmieniony (algorytmu sortowanie zamiast szybkiego sortowania).</span><span class="sxs-lookup"><span data-stu-id="c6d22-103">Beginning in .NET Framework 4.5, <xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort algorithm has changed (to be an introspective sort instead of a quick sort).</span></span> <span data-ttu-id="c6d22-104"><xref:System.Collections.Generic.List%601?displayProperty=fullName>sortowanie nigdy nie było stabilne, ale ta zmiana może spowodować, że inne scenariusze będą sortowane w niestabilny sposób.</span><span class="sxs-lookup"><span data-stu-id="c6d22-104"><xref:System.Collections.Generic.List%601?displayProperty=fullName>'s sort has never been stable, but this change may cause different scenarios to sort in unstable ways.</span></span> <span data-ttu-id="c6d22-105">Oznacza to po prostu, że równoważne elementy mogą sortować w różnych zamówieniach w kolejnych wywołaniach interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="c6d22-105">That simply means that equivalent items may sort in different orders in subsequent calls of the API.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c6d22-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="c6d22-106">Suggestion</span></span>

<span data-ttu-id="c6d22-107">Ponieważ stary algorytm sortowania był również niestabilny (choć nieco inaczej), nie powinien być kod, który zależy od elementów równoważnych zawsze sortowanych w określonej kolejności.</span><span class="sxs-lookup"><span data-stu-id="c6d22-107">Because the old sort algorithm was also unstable (though in slightly different ways), there should be no code that depends on equivalent items always sorting in a particular order.</span></span> <span data-ttu-id="c6d22-108">Jeśli istnieją wystąpienia kodu, w zależności od tego i są cieszymy ze starym zachowaniem, kod ten należy zaktualizować, aby użyć funkcji porównującej, która będzie w sposób jednoznaczny sortować elementy w żądanej kolejności.</span><span class="sxs-lookup"><span data-stu-id="c6d22-108">If there are instances of code depending upon that and being lucky with the old behavior, that code should be updated to use a comparer that will deterministically sort the items in the desired order.</span></span>

| <span data-ttu-id="c6d22-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="c6d22-109">Name</span></span>    | <span data-ttu-id="c6d22-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="c6d22-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c6d22-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="c6d22-111">Scope</span></span>   |<span data-ttu-id="c6d22-112">Przezroczyste</span><span class="sxs-lookup"><span data-stu-id="c6d22-112">Transparent</span></span>|
|<span data-ttu-id="c6d22-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="c6d22-113">Version</span></span>|<span data-ttu-id="c6d22-114">4.5</span><span class="sxs-lookup"><span data-stu-id="c6d22-114">4.5</span></span>|
|<span data-ttu-id="c6d22-115">Typ</span><span class="sxs-lookup"><span data-stu-id="c6d22-115">Type</span></span>|<span data-ttu-id="c6d22-116">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="c6d22-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c6d22-117">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="c6d22-117">Affected APIs</span></span>

-<xref:System.Collections.Generic.List%601.Sort?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Comparison{%600})?displayProperty=nameWithType></li><li><xref:System.Collections.Generic.List%601.Sort(System.Int32,System.Int32,System.Collections.Generic.IComparer{%600})?displayProperty=nameWithType></li></ul>|
