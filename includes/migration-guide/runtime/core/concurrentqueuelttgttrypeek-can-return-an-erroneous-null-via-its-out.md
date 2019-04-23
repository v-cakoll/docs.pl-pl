---
ms.openlocfilehash: a93fbbd787aa50f080337a6170cf8f56d0d24e31
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804718"
---
### <a name="concurrentqueuettrypeek-can-return-an-erroneous-null-via-its-out-parameter"></a><span data-ttu-id="7796e-101">ConcurrentQueue\<T >. TryPeek może zwrócić poproszenie o wartości null za pośrednictwem jego parametru ze specyfikatorem out</span><span class="sxs-lookup"><span data-stu-id="7796e-101">ConcurrentQueue\<T>.TryPeek can return an erroneous null via its out parameter</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7796e-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7796e-102">Details</span></span>|<span data-ttu-id="7796e-103">W niektórych przypadkach wielowątkowych <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> może zwrócić wartość true, ale wypełnić parametr out o wartości null (a nie wartość poprawny, podejrzeć).</span><span class="sxs-lookup"><span data-stu-id="7796e-103">In some multi-threaded scenarios, <xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=name> can return true, but populate the out parameter with a null value (instead of the correct, peeked value).</span></span>|
|<span data-ttu-id="7796e-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="7796e-104">Suggestion</span></span>|<span data-ttu-id="7796e-105">Ten problem został rozwiązany w .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="7796e-105">This issue is fixed in the .NET Framework 4.5.1.</span></span> <span data-ttu-id="7796e-106">Uaktualnienie do tej struktury rozwiąże problem.</span><span class="sxs-lookup"><span data-stu-id="7796e-106">Upgrading to that Framework will solve the issue.</span></span>|
|<span data-ttu-id="7796e-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="7796e-107">Scope</span></span>|<span data-ttu-id="7796e-108">Duży</span><span class="sxs-lookup"><span data-stu-id="7796e-108">Major</span></span>|
|<span data-ttu-id="7796e-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="7796e-109">Version</span></span>|<span data-ttu-id="7796e-110">4.5</span><span class="sxs-lookup"><span data-stu-id="7796e-110">4.5</span></span>|
|<span data-ttu-id="7796e-111">Typ</span><span class="sxs-lookup"><span data-stu-id="7796e-111">Type</span></span>|<span data-ttu-id="7796e-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7796e-112">Runtime</span></span>|
|<span data-ttu-id="7796e-113">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="7796e-113">Affected APIs</span></span>|<ul><li><xref:System.Collections.Concurrent.ConcurrentQueue%601.TryPeek(%600@)?displayProperty=nameWithType></li></ul>|
