---
title: ICorProfilerCallback7 Interface
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
ms.openlocfilehash: 81477010b22edee71098edfc1b8557db08b6038f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178636"
---
# <a name="icorprofilercallback7-interface"></a><span data-ttu-id="8f968-102">ICorProfilerCallback7 Interface</span><span class="sxs-lookup"><span data-stu-id="8f968-102">ICorProfilerCallback7 Interface</span></span>
<span data-ttu-id="8f968-103">[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="8f968-103">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="8f968-104">Podklasa klasy [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) który zapewnia metodę wywołania zwrotnego, która środowiska uruchomieniowego języka wspólnego używa powiadomić profiler, że strumień symbol skojarzone z modułem w pamięci jest aktualizowana.</span><span class="sxs-lookup"><span data-stu-id="8f968-104">A subclass of [ICorProfilerCallback6](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md) that provides a callback method that the common language runtime uses to notify the profiler that the symbol stream associated with an in-memory module is updated.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8f968-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8f968-105">Methods</span></span>  
  
|<span data-ttu-id="8f968-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="8f968-106">Method</span></span>|<span data-ttu-id="8f968-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8f968-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8f968-108">ModuleInMemorySymbolsUpdated, metoda</span><span class="sxs-lookup"><span data-stu-id="8f968-108">ModuleInMemorySymbolsUpdated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|<span data-ttu-id="8f968-109">Powiadamia program profilujący, że strumień symbol skojarzone z modułem w pamięci jest aktualizowana.</span><span class="sxs-lookup"><span data-stu-id="8f968-109">Notifies the profiler that the symbol stream associated with an in-memory module is updated.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f968-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f968-110">Requirements</span></span>  
 <span data-ttu-id="8f968-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f968-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f968-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8f968-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 **<span data-ttu-id="8f968-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8f968-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8f968-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f968-114">See also</span></span>

- [<span data-ttu-id="8f968-115">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="8f968-115">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
