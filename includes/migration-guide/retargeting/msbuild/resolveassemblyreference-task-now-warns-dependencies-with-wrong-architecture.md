---
ms.openlocfilehash: 4d410811095786b33580d25f6c6eab3ac2f27148
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616102"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a><span data-ttu-id="6dd26-101">Zadanie ResolveAssemblyReference — teraz ostrzega o zależnościach z niewłaściwą architekturą</span><span class="sxs-lookup"><span data-stu-id="6dd26-101">ResolveAssemblyReference task now warns of dependencies with the wrong architecture</span></span>

#### <a name="details"></a><span data-ttu-id="6dd26-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="6dd26-102">Details</span></span>

<span data-ttu-id="6dd26-103">Zadanie emituje ostrzeżenie, MSB3270, co oznacza, że odwołanie lub jego zależności nie są zgodne z architekturą aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6dd26-103">The task emits a warning, MSB3270, which indicates that a reference or any of its dependencies does not match the app's architecture.</span></span> <span data-ttu-id="6dd26-104">Na przykład dzieje się tak, jeśli aplikacja, która została skompilowana przy użyciu `AnyCPU` opcji zawiera odwołanie do platformy x86.</span><span class="sxs-lookup"><span data-stu-id="6dd26-104">For example, this occurs if an app that was compiled with the `AnyCPU` option includes an x86 reference.</span></span> <span data-ttu-id="6dd26-105">Taki scenariusz może spowodować awarię aplikacji w czasie wykonywania (w tym przypadku, jeśli aplikacja jest wdrażana jako proces x64).</span><span class="sxs-lookup"><span data-stu-id="6dd26-105">Such a scenario could result in an app failure at run time (in this case, if the app is deployed as an x64 process).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="6dd26-106">Sugestia</span><span class="sxs-lookup"><span data-stu-id="6dd26-106">Suggestion</span></span>

<span data-ttu-id="6dd26-107">Istnieją dwa obszary wpływu:</span><span class="sxs-lookup"><span data-stu-id="6dd26-107">There are two areas of impact:</span></span>

- <span data-ttu-id="6dd26-108">Ponowna kompilacja generuje ostrzeżenia, które nie były wyświetlane, gdy aplikacja została skompilowana w poprzedniej wersji programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="6dd26-108">Recompilation generates warnings that did not appear when the app was compiled under a previous version of MSBuild.</span></span> <span data-ttu-id="6dd26-109">Jednak ze względu na to, że ostrzeżenie identyfikuje możliwe Źródło błędu czasu wykonywania, należy zbadać i rozwiązać ten problem.</span><span class="sxs-lookup"><span data-stu-id="6dd26-109">However, because the warning identifies a possible source of runtime failure, it should be investigated and addressed.</span></span>
- <span data-ttu-id="6dd26-110">Jeśli ostrzeżenia są traktowane jako błędy, kompilacja nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="6dd26-110">If warnings are treated as errors, the app will fail to compile.</span></span>

| <span data-ttu-id="6dd26-111">Nazwa</span><span class="sxs-lookup"><span data-stu-id="6dd26-111">Name</span></span>    | <span data-ttu-id="6dd26-112">Wartość</span><span class="sxs-lookup"><span data-stu-id="6dd26-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="6dd26-113">Zakres</span><span class="sxs-lookup"><span data-stu-id="6dd26-113">Scope</span></span>   | <span data-ttu-id="6dd26-114">Mały</span><span class="sxs-lookup"><span data-stu-id="6dd26-114">Minor</span></span>       |
| <span data-ttu-id="6dd26-115">Wersja</span><span class="sxs-lookup"><span data-stu-id="6dd26-115">Version</span></span> | <span data-ttu-id="6dd26-116">4.5.1</span><span class="sxs-lookup"><span data-stu-id="6dd26-116">4.5.1</span></span>       |
| <span data-ttu-id="6dd26-117">Typ</span><span class="sxs-lookup"><span data-stu-id="6dd26-117">Type</span></span>    | <span data-ttu-id="6dd26-118">Przekierowanie</span><span class="sxs-lookup"><span data-stu-id="6dd26-118">Retargeting</span></span> |
