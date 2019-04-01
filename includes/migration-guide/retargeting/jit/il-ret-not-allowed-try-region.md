---
ms.openlocfilehash: 060da3ebc60057554fd572bd2569652afee6bd0f
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761075"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a><span data-ttu-id="d12a1-101">Instrukcji IL, nie są dozwolone w regionie try</span><span class="sxs-lookup"><span data-stu-id="d12a1-101">IL ret not allowed in a try region</span></span>

|   |   |
|---|---|
|<span data-ttu-id="d12a1-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d12a1-102">Details</span></span>|<span data-ttu-id="d12a1-103">W przeciwieństwie do kompilatora just-in-time JIT64 elementach RyuJIT (używane w programie .NET Framework 4.6) nie zezwala na IL ret instrukcji w regionie try.</span><span class="sxs-lookup"><span data-stu-id="d12a1-103">Unlike the JIT64 just-in-time compiler, RyuJIT (used in .NET Framework 4.6) does not allow an IL ret instruction in a try region.</span></span> <span data-ttu-id="d12a1-104">Zwracanie z regionu spróbuj jest zabroniona przez specyfikację ECMA-335, a nie znane zarządzanych kompilator generuje taki IL.</span><span class="sxs-lookup"><span data-stu-id="d12a1-104">Returning from a try region is disallowed by the ECMA-335 specification, and no known managed compiler generates such IL.</span></span> <span data-ttu-id="d12a1-105">Jednak kompilatora JIT64 będzie wykonywać takie IL, jeśli jest ona generowana za pomocą odbicia emisji.</span><span class="sxs-lookup"><span data-stu-id="d12a1-105">However, the JIT64 compiler will execute such IL if it is generated using reflection emit.</span></span>|
|<span data-ttu-id="d12a1-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="d12a1-106">Suggestion</span></span>|<span data-ttu-id="d12a1-107">Jeśli aplikacja generuje IL, która obejmuje ret opcode w regionie, spróbuj, aplikacji mogą odnosić się do programu .NET Framework 4.5 do używania starego JIT i uniknąć tego podziału.</span><span class="sxs-lookup"><span data-stu-id="d12a1-107">If an app is generating IL that includes a ret opcode in a try region, the app may target .NET Framework 4.5 to use the old JIT and avoid this break.</span></span> <span data-ttu-id="d12a1-108">Alternatywnie wygenerowanego IL może zostać zaktualizowany do zwracania po try region.</span><span class="sxs-lookup"><span data-stu-id="d12a1-108">Alternatively, the generated IL may be updated to return after the try region.</span></span>|
|<span data-ttu-id="d12a1-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="d12a1-109">Scope</span></span>|<span data-ttu-id="d12a1-110">Krawędź</span><span class="sxs-lookup"><span data-stu-id="d12a1-110">Edge</span></span>|
|<span data-ttu-id="d12a1-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="d12a1-111">Version</span></span>|<span data-ttu-id="d12a1-112">4.6</span><span class="sxs-lookup"><span data-stu-id="d12a1-112">4.6</span></span>|
|<span data-ttu-id="d12a1-113">Typ</span><span class="sxs-lookup"><span data-stu-id="d12a1-113">Type</span></span>|<span data-ttu-id="d12a1-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="d12a1-114">Retargeting</span></span>|

