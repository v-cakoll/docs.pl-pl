---
title: Interfejs ICorProfilerCallback7
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f681001b610f42fef28181ffe3b47d702aabdf6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452696"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="90f9c-102">Interfejs ICorProfilerCallback7</span><span class="sxs-lookup"><span data-stu-id="90f9c-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="90f9c-103">[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="90f9c-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="90f9c-104">Podklasa [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) zapewnia metody wywołania zwrotnego, która środowisko uruchomieniowe języka wspólnego używa do powiadamiania profilera zaktualizowaniu strumienia symbol skojarzone z modułu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="90f9c-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="90f9c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="90f9c-105">Methods</span></span>  
  
|<span data-ttu-id="90f9c-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="90f9c-106">Method</span></span>|<span data-ttu-id="90f9c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="90f9c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="90f9c-108">ModuleInMemorySymbolsUpdated, metoda</span><span class="sxs-lookup"><span data-stu-id="90f9c-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="90f9c-109">Powiadamia profilera zaktualizowaniu strumienia symbol skojarzone z modułu w pamięci.</span><span class="sxs-lookup"><span data-stu-id="90f9c-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="90f9c-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="90f9c-110">Requirements</span></span>  
 <span data-ttu-id="90f9c-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90f9c-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90f9c-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="90f9c-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="90f9c-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90f9c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90f9c-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="90f9c-114">See Also</span></span>  
 [<span data-ttu-id="90f9c-115">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="90f9c-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
