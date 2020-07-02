---
ms.openlocfilehash: 2e13268d4983af5d2fdd6d12b4d9e67d61d07f3d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622129"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="d349c-101">Profilowanie aplikacji ASP.Net MVC4 może prowadzić do błędu aparatu wykonywania krytycznych</span><span class="sxs-lookup"><span data-stu-id="d349c-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

#### <a name="details"></a><span data-ttu-id="d349c-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="d349c-102">Details</span></span>

<span data-ttu-id="d349c-103">Moduły plików używające narzędzia NGEN/profile mogą ulec awarii w profilowanych aplikacjach ASP.NET MVC4 podczas uruchamiania przy użyciu "wyjątku aparatu wykonywania krytycznego"</span><span class="sxs-lookup"><span data-stu-id="d349c-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>

#### <a name="suggestion"></a><span data-ttu-id="d349c-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="d349c-104">Suggestion</span></span>

<span data-ttu-id="d349c-105">Ten problem został rozwiązany w .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="d349c-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="d349c-106">Alternatywnie profiler może uniknąć tego problemu przez określenie <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> w jego masce zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d349c-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>

| <span data-ttu-id="d349c-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="d349c-107">Name</span></span>    | <span data-ttu-id="d349c-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="d349c-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="d349c-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="d349c-109">Scope</span></span>   |<span data-ttu-id="d349c-110">Brzeg</span><span class="sxs-lookup"><span data-stu-id="d349c-110">Edge</span></span>|
|<span data-ttu-id="d349c-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="d349c-111">Version</span></span>|<span data-ttu-id="d349c-112">4.5</span><span class="sxs-lookup"><span data-stu-id="d349c-112">4.5</span></span>|
|<span data-ttu-id="d349c-113">Typ</span><span class="sxs-lookup"><span data-stu-id="d349c-113">Type</span></span>|<span data-ttu-id="d349c-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="d349c-114">Runtime</span></span>|
