---
ms.openlocfilehash: 1687b1b9a1a6861f9569a0e29426de7f32ffc32b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804531"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a><span data-ttu-id="e30b0-101">IL ret nie jest dozwolony w regionie try</span><span class="sxs-lookup"><span data-stu-id="e30b0-101">IL ret not allowed in a try region</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e30b0-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="e30b0-102">Details</span></span>|<span data-ttu-id="e30b0-103">W przeciwieństwie do kompilatora just-in-time JIT64 RyuJIT (używany w .NET Framework 4.6) nie zezwala na instrukcję IL ret w regionie try.</span><span class="sxs-lookup"><span data-stu-id="e30b0-103">Unlike the JIT64 just-in-time compiler, RyuJIT (used in .NET Framework 4.6) does not allow an IL ret instruction in a try region.</span></span> <span data-ttu-id="e30b0-104">Powrót z regionu try jest niedozwolony przez specyfikację ECMA-335 i żaden znany kompilator zarządzany nie generuje takiego identyfikatora IL.</span><span class="sxs-lookup"><span data-stu-id="e30b0-104">Returning from a try region is disallowed by the ECMA-335 specification, and no known managed compiler generates such IL.</span></span> <span data-ttu-id="e30b0-105">Jednak kompilator JIT64 wykona takie IL, jeśli jest generowany przy użyciu emisji odbicia.</span><span class="sxs-lookup"><span data-stu-id="e30b0-105">However, the JIT64 compiler will execute such IL if it is generated using reflection emit.</span></span>|
|<span data-ttu-id="e30b0-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="e30b0-106">Suggestion</span></span>|<span data-ttu-id="e30b0-107">Jeśli aplikacja generuje IL, który zawiera kod opcode ret w regionie try, aplikacja może kierować .NET Framework 4.5 do korzystania ze starego JIT i uniknąć tej przerwy.</span><span class="sxs-lookup"><span data-stu-id="e30b0-107">If an app is generating IL that includes a ret opcode in a try region, the app may target .NET Framework 4.5 to use the old JIT and avoid this break.</span></span> <span data-ttu-id="e30b0-108">Alternatywnie wygenerowany IL może zostać zaktualizowany, aby powrócić po regionie try.</span><span class="sxs-lookup"><span data-stu-id="e30b0-108">Alternatively, the generated IL may be updated to return after the try region.</span></span>|
|<span data-ttu-id="e30b0-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="e30b0-109">Scope</span></span>|<span data-ttu-id="e30b0-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="e30b0-110">Edge</span></span>|
|<span data-ttu-id="e30b0-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="e30b0-111">Version</span></span>|<span data-ttu-id="e30b0-112">4.6</span><span class="sxs-lookup"><span data-stu-id="e30b0-112">4.6</span></span>|
|<span data-ttu-id="e30b0-113">Typ</span><span class="sxs-lookup"><span data-stu-id="e30b0-113">Type</span></span>|<span data-ttu-id="e30b0-114">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="e30b0-114">Retargeting</span></span>|
