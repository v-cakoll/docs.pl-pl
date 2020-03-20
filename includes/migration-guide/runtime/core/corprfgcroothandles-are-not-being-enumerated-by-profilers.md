---
ms.openlocfilehash: 8433899058c6f569e380999800557dbe8ed0a169
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858411"
---
### <a name="cor_prf_gc_root_handles-are-not-being-enumerated-by-profilers"></a><span data-ttu-id="4e7b5-101">COR_PRF_GC_ROOT_HANDLEs nie są wyliczane przez profilerzy</span><span class="sxs-lookup"><span data-stu-id="4e7b5-101">COR_PRF_GC_ROOT_HANDLEs are not being enumerated by profilers</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4e7b5-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="4e7b5-102">Details</span></span>|<span data-ttu-id="4e7b5-103">W programie .NET Framework w wersji 4.5.1 interfejs <code>RootReferences2()</code> <code>COR_PRF_GC_ROOT_HANDLE</code> API profilowania <code>COR_PRF_GC_ROOT_OTHER</code> niepoprawnie nigdy nie zwraca (są one zwracane jako zamiast tego).</span><span class="sxs-lookup"><span data-stu-id="4e7b5-103">In the .NET Framework v4.5.1, the profiling API <code>RootReferences2()</code> is incorrectly never returning <code>COR_PRF_GC_ROOT_HANDLE</code> (they are returned as <code>COR_PRF_GC_ROOT_OTHER</code> instead).</span></span> <span data-ttu-id="4e7b5-104">Ten problem został rozwiązany począwszy od .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="4e7b5-104">This issue is fixed beginning in the .NET Framework 4.6.</span></span>|
|<span data-ttu-id="4e7b5-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="4e7b5-105">Suggestion</span></span>|<span data-ttu-id="4e7b5-106">Ten problem został rozwiązany w .NET Framework 4.6 i może zostać rozwiązany przez uaktualnienie do tej wersji programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4e7b5-106">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>|
|<span data-ttu-id="4e7b5-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="4e7b5-107">Scope</span></span>|<span data-ttu-id="4e7b5-108">Mały</span><span class="sxs-lookup"><span data-stu-id="4e7b5-108">Minor</span></span>|
|<span data-ttu-id="4e7b5-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="4e7b5-109">Version</span></span>|<span data-ttu-id="4e7b5-110">4.5.1</span><span class="sxs-lookup"><span data-stu-id="4e7b5-110">4.5.1</span></span>|
|<span data-ttu-id="4e7b5-111">Typ</span><span class="sxs-lookup"><span data-stu-id="4e7b5-111">Type</span></span>|<span data-ttu-id="4e7b5-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="4e7b5-112">Runtime</span></span>|
