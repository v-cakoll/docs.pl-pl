---
ms.openlocfilehash: 107b34c7bd26e1396e8a6638d6929c15de92b8e4
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2019
ms.locfileid: "67803157"
---
### <a name="profiling-aspnet-mvc4-apps-can-lead-to-fatal-execution-engine-error"></a><span data-ttu-id="157ea-101">Profilowanie aplikacji ASP.Net MVC4 może prowadzić do krytyczny błąd aparatu wykonywania</span><span class="sxs-lookup"><span data-stu-id="157ea-101">Profiling ASP.Net MVC4 apps can lead to Fatal Execution Engine Error</span></span>

|   |   |
|---|---|
|<span data-ttu-id="157ea-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="157ea-102">Details</span></span>|<span data-ttu-id="157ea-103">Profilery za pomocą zestawów NGEN/profile może ulec awarii aplikacji ASP.NET MVC4 profilowanych przy uruchamianiu z "Wykonywanie aparatu wyjątek krytyczny"</span><span class="sxs-lookup"><span data-stu-id="157ea-103">Profilers using NGEN /Profile assemblies may crash profiled ASP.NET MVC4 applications on startup with a 'Fatal Execution Engine Exception'</span></span>|
|<span data-ttu-id="157ea-104">Sugestia</span><span class="sxs-lookup"><span data-stu-id="157ea-104">Suggestion</span></span>|<span data-ttu-id="157ea-105">Ten problem został rozwiązany w .NET Framework 4.5.2.</span><span class="sxs-lookup"><span data-stu-id="157ea-105">This issue is fixed in the .NET Framework 4.5.2.</span></span> <span data-ttu-id="157ea-106">Alternatywnie program profilujący może uniknąć tego problemu, określając <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> w jego maski zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="157ea-106">Alternatively, the profiler may avoid this issue by specifying <code>COR_PRF_DISABLE_ALL_NGEN_IMAGES</code> in its event mask.</span></span>|
|<span data-ttu-id="157ea-107">Scope</span><span class="sxs-lookup"><span data-stu-id="157ea-107">Scope</span></span>|<span data-ttu-id="157ea-108">Krawędź</span><span class="sxs-lookup"><span data-stu-id="157ea-108">Edge</span></span>|
|<span data-ttu-id="157ea-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="157ea-109">Version</span></span>|<span data-ttu-id="157ea-110">4.5</span><span class="sxs-lookup"><span data-stu-id="157ea-110">4.5</span></span>|
|<span data-ttu-id="157ea-111">Typ</span><span class="sxs-lookup"><span data-stu-id="157ea-111">Type</span></span>|<span data-ttu-id="157ea-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="157ea-112">Runtime</span></span>|

