---
ms.openlocfilehash: 439a4976482639cd2e4e17315ec1a53ca54aa477
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804761"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="7b181-101">Profilowanie aplikacji ASP.Net MVC4 może prowadzić do krytyczny błąd aparatu wykonywania</span><span class="sxs-lookup"><span data-stu-id="7b181-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7b181-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="7b181-102">Details</span></span>|<span data-ttu-id="7b181-103">Profilery za pomocą zestawów NGEN/profile może ulec awarii aplikacji ASP.NET MVC4 profilowanych przy uruchamianiu z "Wykonywanie aparatu wyjątek krytyczny"</span><span class="sxs-lookup"><span data-stu-id="7b181-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="7b181-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="7b181-104">Suggestion</span></span>|<span data-ttu-id="7b181-105">Ten problem został rozwiązany w .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="7b181-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="7b181-106">Alternatywnie program profilujący może uniknąć tego problemu, określając <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> w jego maski zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7b181-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="7b181-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="7b181-107">Scope</span></span>|<span data-ttu-id="7b181-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="7b181-108">Edge</span></span>|
|<span data-ttu-id="7b181-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="7b181-109">Version</span></span>|<span data-ttu-id="7b181-110">4.5</span><span class="sxs-lookup"><span data-stu-id="7b181-110">4.5</span></span>|
|<span data-ttu-id="7b181-111">Typ</span><span class="sxs-lookup"><span data-stu-id="7b181-111">Type</span></span>|<span data-ttu-id="7b181-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="7b181-112">Runtime</span></span>|
