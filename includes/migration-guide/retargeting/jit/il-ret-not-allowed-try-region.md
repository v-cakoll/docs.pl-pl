---
ms.openlocfilehash: 1687b1b9a1a6861f9569a0e29426de7f32ffc32b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234541"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a><span data-ttu-id="62b35-101">Instrukcji IL, nie są dozwolone w regionie try</span><span class="sxs-lookup"><span data-stu-id="62b35-101">IL ret not allowed in a try region</span></span>

|   |   |
|---|---|
|<span data-ttu-id="62b35-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="62b35-102">Details</span></span>|<span data-ttu-id="62b35-103">W przeciwieństwie do kompilatora just-in-time JIT64 elementach RyuJIT (używane w programie .NET Framework 4.6) nie zezwala na IL ret instrukcji w regionie try.</span><span class="sxs-lookup"><span data-stu-id="62b35-103">Unlike the JIT64 just-in-time compiler, RyuJIT (used in .NET Framework 4.6) does not allow an IL ret instruction in a try region.</span></span> <span data-ttu-id="62b35-104">Zwracanie z regionu spróbuj jest zabroniona przez specyfikację ECMA-335, a nie znane zarządzanych kompilator generuje taki IL.</span><span class="sxs-lookup"><span data-stu-id="62b35-104">Returning from a try region is disallowed by the ECMA-335 specification, and no known managed compiler generates such IL.</span></span> <span data-ttu-id="62b35-105">Jednak kompilatora JIT64 będzie wykonywać takie IL, jeśli jest ona generowana za pomocą odbicia emisji.</span><span class="sxs-lookup"><span data-stu-id="62b35-105">However, the JIT64 compiler will execute such IL if it is generated using reflection emit.</span></span>|
|<span data-ttu-id="62b35-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="62b35-106">Suggestion</span></span>|<span data-ttu-id="62b35-107">Jeśli aplikacja generuje IL, która obejmuje ret opcode w regionie, spróbuj, aplikacji mogą odnosić się do programu .NET Framework 4.5 do używania starego JIT i uniknąć tego podziału.</span><span class="sxs-lookup"><span data-stu-id="62b35-107">If an app is generating IL that includes a ret opcode in a try region, the app may target .NET Framework 4.5 to use the old JIT and avoid this break.</span></span> <span data-ttu-id="62b35-108">Alternatywnie wygenerowanego IL może zostać zaktualizowany do zwracania po try region.</span><span class="sxs-lookup"><span data-stu-id="62b35-108">Alternatively, the generated IL may be updated to return after the try region.</span></span>|
|<span data-ttu-id="62b35-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="62b35-109">Scope</span></span>|<span data-ttu-id="62b35-110">Krawędź</span><span class="sxs-lookup"><span data-stu-id="62b35-110">Edge</span></span>|
|<span data-ttu-id="62b35-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="62b35-111">Version</span></span>|<span data-ttu-id="62b35-112">4.6</span><span class="sxs-lookup"><span data-stu-id="62b35-112">4.6</span></span>|
|<span data-ttu-id="62b35-113">Typ</span><span class="sxs-lookup"><span data-stu-id="62b35-113">Type</span></span>|<span data-ttu-id="62b35-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="62b35-114">Retargeting</span></span>|
