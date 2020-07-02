---
ms.openlocfilehash: 4a65e721e5639f12445a9a44f46baa0d26898a88
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615671"
---
### <a name="il-ret-not-allowed-in-a-try-region"></a><span data-ttu-id="7b250-101">Element IL RET nie jest dozwolony w regionie try</span><span class="sxs-lookup"><span data-stu-id="7b250-101">IL ret not allowed in a try region</span></span>

#### <a name="details"></a><span data-ttu-id="7b250-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7b250-102">Details</span></span>

<span data-ttu-id="7b250-103">W przeciwieństwie do kompilatora JIT64 just in Time RyuJIT (używany w .NET Framework 4,6) nie zezwala na instrukcje języka IL RET w regionie try.</span><span class="sxs-lookup"><span data-stu-id="7b250-103">Unlike the JIT64 just-in-time compiler, RyuJIT (used in .NET Framework 4.6) does not allow an IL ret instruction in a try region.</span></span> <span data-ttu-id="7b250-104">Powrót z regionu try jest niedozwolony w specyfikacji ECMA-335, a żaden znany kompilator zarządzany nie generuje takiego IL.</span><span class="sxs-lookup"><span data-stu-id="7b250-104">Returning from a try region is disallowed by the ECMA-335 specification, and no known managed compiler generates such IL.</span></span> <span data-ttu-id="7b250-105">Jednak kompilator JIT64 wykona takie IL, jeśli zostanie wygenerowany przy użyciu emisji odbicia.</span><span class="sxs-lookup"><span data-stu-id="7b250-105">However, the JIT64 compiler will execute such IL if it is generated using reflection emit.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="7b250-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="7b250-106">Suggestion</span></span>

<span data-ttu-id="7b250-107">Jeśli aplikacja generuje IL, która zawiera kod operacji RET w regionie try, aplikacja może kierować .NET Framework 4,5, aby użyć starego JIT i uniknąć tego przerwy.</span><span class="sxs-lookup"><span data-stu-id="7b250-107">If an app is generating IL that includes a ret opcode in a try region, the app may target .NET Framework 4.5 to use the old JIT and avoid this break.</span></span> <span data-ttu-id="7b250-108">Alternatywnie wygenerowany kod IL może zostać zaktualizowany w celu powrotu po regionie try.</span><span class="sxs-lookup"><span data-stu-id="7b250-108">Alternatively, the generated IL may be updated to return after the try region.</span></span>

| <span data-ttu-id="7b250-109">Nazwa</span><span class="sxs-lookup"><span data-stu-id="7b250-109">Name</span></span>    | <span data-ttu-id="7b250-110">Wartość</span><span class="sxs-lookup"><span data-stu-id="7b250-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="7b250-111">Zakres</span><span class="sxs-lookup"><span data-stu-id="7b250-111">Scope</span></span>   | <span data-ttu-id="7b250-112">Brzeg</span><span class="sxs-lookup"><span data-stu-id="7b250-112">Edge</span></span>        |
| <span data-ttu-id="7b250-113">Wersja</span><span class="sxs-lookup"><span data-stu-id="7b250-113">Version</span></span> | <span data-ttu-id="7b250-114">4.6</span><span class="sxs-lookup"><span data-stu-id="7b250-114">4.6</span></span>         |
| <span data-ttu-id="7b250-115">Typ</span><span class="sxs-lookup"><span data-stu-id="7b250-115">Type</span></span>    | <span data-ttu-id="7b250-116">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="7b250-116">Retargeting</span></span> |
