---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803157"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="7fd13-101">Profilowanie ASP.Net aplikacjami MVC4 może prowadzić do błędu silnika wykonanie fatalne</span><span class="sxs-lookup"><span data-stu-id="7fd13-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7fd13-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7fd13-102">Details</span></span>|<span data-ttu-id="7fd13-103">Profilerzy używający zestawów NGEN /Profile mogą ulegać awarii w profilowaniu aplikacji MVC4 ASP.NET podczas uruchamiania z "Fatal Execution Engine Exception"</span><span class="sxs-lookup"><span data-stu-id="7fd13-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="7fd13-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="7fd13-104">Suggestion</span></span>|<span data-ttu-id="7fd13-105">Ten problem został rozwiązany w .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="7fd13-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="7fd13-106">Alternatywnie profiler może uniknąć tego problemu, określając <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> w jego maski zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7fd13-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="7fd13-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="7fd13-107">Scope</span></span>|<span data-ttu-id="7fd13-108">Brzeg</span><span class="sxs-lookup"><span data-stu-id="7fd13-108">Edge</span></span>|
|<span data-ttu-id="7fd13-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="7fd13-109">Version</span></span>|<span data-ttu-id="7fd13-110">4.5</span><span class="sxs-lookup"><span data-stu-id="7fd13-110">4.5</span></span>|
|<span data-ttu-id="7fd13-111">Typ</span><span class="sxs-lookup"><span data-stu-id="7fd13-111">Type</span></span>|<span data-ttu-id="7fd13-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7fd13-112">Runtime</span></span>|
