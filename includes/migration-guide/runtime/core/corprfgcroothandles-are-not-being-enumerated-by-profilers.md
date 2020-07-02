---
ms.openlocfilehash: 4f52535e54607cc824500f9c6a14964a1dec9d32
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620208"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="94145-101">COR_PRF_GC_ROOT_HANDLEs nie są wyliczane przez program do plików</span><span class="sxs-lookup"><span data-stu-id="94145-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

#### <a name="details"></a><span data-ttu-id="94145-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="94145-102">Details</span></span>

<span data-ttu-id="94145-103">W .NET Framework v 4.5.1 interfejs API profilowania <code>RootReferences2()</code> jest niepoprawnie nigdy nie zwraca <code>COR_PRF_GC_ROOT_HANDLE</code> (są zwracane jako <code>COR_PRF_GC_ROOT_OTHER</code> zamiast).</span><span class="sxs-lookup"><span data-stu-id="94145-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="94145-104">Ten problem został rozwiązany, rozpoczynając od .NET Framework 4,6.</span><span class="sxs-lookup"><span data-stu-id="94145-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="94145-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="94145-105">Suggestion</span></span>

<span data-ttu-id="94145-106">Ten problem został rozwiązany w .NET Framework 4,6 i może zostać rozwiązany przez uaktualnienie do tej wersji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94145-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="94145-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="94145-107">Name</span></span>    | <span data-ttu-id="94145-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="94145-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="94145-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="94145-109">Scope</span></span>   |<span data-ttu-id="94145-110">Mały</span><span class="sxs-lookup"><span data-stu-id="94145-110">Minor</span></span>|
|<span data-ttu-id="94145-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="94145-111">Version</span></span>|<span data-ttu-id="94145-112">4.5.1</span><span class="sxs-lookup"><span data-stu-id="94145-112">4.5.1</span></span>|
|<span data-ttu-id="94145-113">Typ</span><span class="sxs-lookup"><span data-stu-id="94145-113">Type</span></span>|<span data-ttu-id="94145-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="94145-114">Runtime</span></span>|
