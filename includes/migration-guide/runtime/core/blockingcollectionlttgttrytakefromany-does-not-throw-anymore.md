---
ms.openlocfilehash: a8f51dfa1c82e3b166449d2432dfe8a9b96564b9
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620197"
---
### <a name="blockingcollectionlttgttrytakefromany-does-not-throw-anymore"></a><span data-ttu-id="b3a24-101">BlockingCollection &lt; T &gt; . TryTakeFromAny nie generują się już</span><span class="sxs-lookup"><span data-stu-id="b3a24-101">BlockingCollection&lt;T&gt;.TryTakeFromAny does not throw anymore</span></span>

#### <a name="details"></a><span data-ttu-id="b3a24-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b3a24-102">Details</span></span>

<span data-ttu-id="b3a24-103">Jeśli jedna z kolekcji wejściowych jest oznaczona jako ukończona, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> nie zwraca już wartości-1 i już <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> nie zgłasza wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b3a24-103">If one of the input collections is marked completed, <xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer returns -1 and <xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)> no longer throws an exception.</span></span> <span data-ttu-id="b3a24-104">Ta zmiana umożliwia pracę z wykorzystaniem kolekcji, kiedy jedna z kolekcji jest pusta lub ukończona, ale inna kolekcja ma elementy, które mogą zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="b3a24-104">This change makes it possible to work with collections when one of the collections is either empty or completed, but the other collection still has items that can be retrieved.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b3a24-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="b3a24-105">Suggestion</span></span>

<span data-ttu-id="b3a24-106">Jeśli TryTakeFromAny zwracające wartość-1 lub wyrzucanie TakeFromAny zostało użyte do celów sterowania przepływem w przypadku, gdy trwa zablokowanie kolekcji, taki kod powinien teraz zostać zmieniony, aby można było <code>.Any(b =&gt; b.IsCompleted)</code> wykryć ten warunek.</span><span class="sxs-lookup"><span data-stu-id="b3a24-106">If TryTakeFromAny returning -1 or TakeFromAny throwing were used for control-flow purposes in cases of a blocking collection being completed, such code should now be changed to use <code>.Any(b =&gt; b.IsCompleted)</code> to detect that condition.</span></span>

| <span data-ttu-id="b3a24-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="b3a24-107">Name</span></span>    | <span data-ttu-id="b3a24-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="b3a24-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b3a24-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="b3a24-109">Scope</span></span>   |<span data-ttu-id="b3a24-110">Mały</span><span class="sxs-lookup"><span data-stu-id="b3a24-110">Minor</span></span>|
|<span data-ttu-id="b3a24-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="b3a24-111">Version</span></span>|<span data-ttu-id="b3a24-112">4.5</span><span class="sxs-lookup"><span data-stu-id="b3a24-112">4.5</span></span>|
|<span data-ttu-id="b3a24-113">Typ</span><span class="sxs-lookup"><span data-stu-id="b3a24-113">Type</span></span>|<span data-ttu-id="b3a24-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="b3a24-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b3a24-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="b3a24-115">Affected APIs</span></span>

-<xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Threading.CancellationToken)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType></li><li><xref:System.Collections.Concurrent.BlockingCollection%601.TryTakeFromAny(System.Collections.Concurrent.BlockingCollection{%600}[],%600@,System.TimeSpan)?displayProperty=nameWithType></li></ul>|
