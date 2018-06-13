---
title: Interfejs ICorProfilerCallback9
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 488af069e7798fde650abb1473df256eed2d692f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452380"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="b2ab0-102">Interfejs ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="b2ab0-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="b2ab0-103">[Obsługiwane w programie .NET Framework 4.7.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="b2ab0-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="b2ab0-104">Podklasa [ICorProfilerCallback8](icorprofilercallback8-interface.md) zapewnia metody wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego powiadomiono profilera, czy dynamiczna metoda został odzyskiwanie zbierane i następnie zwalnianie.</span><span class="sxs-lookup"><span data-stu-id="b2ab0-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b2ab0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b2ab0-105">Methods</span></span>  
  
|<span data-ttu-id="b2ab0-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b2ab0-106">Method</span></span>|<span data-ttu-id="b2ab0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b2ab0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b2ab0-108">DynamicMethodUnloaded — metoda</span><span class="sxs-lookup"><span data-stu-id="b2ab0-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="b2ab0-109">Powiadamia profilera, czy dynamiczna metoda został odzyskiwanie zbierane i następnie zwalnianie.</span><span class="sxs-lookup"><span data-stu-id="b2ab0-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2ab0-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b2ab0-110">Requirements</span></span>  
 <span data-ttu-id="b2ab0-111">**Platformy:** zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2ab0-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2ab0-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b2ab0-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="b2ab0-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b2ab0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="b2ab0-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b2ab0-114">See Also</span></span>  
<span data-ttu-id="b2ab0-115">[Interfejsy profilowania](profiling-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="b2ab0-115">[Profiling Interfaces](profiling-interfaces.md) </span></span>  
<span data-ttu-id="b2ab0-116">[Interfejs ICorProfilerCallback8](icorprofilercallback9-interface.md) </span><span class="sxs-lookup"><span data-stu-id="b2ab0-116">[ICorProfilerCallback8 Interface](icorprofilercallback9-interface.md) </span></span>  
<span data-ttu-id="b2ab0-117">[ICorProfilerCallback8.DynamicMethodJITCompilationStarted — metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md) </span><span class="sxs-lookup"><span data-stu-id="b2ab0-117">[ICorProfilerCallback8.DynamicMethodJITCompilationStarted method](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md) </span></span>  
[<span data-ttu-id="b2ab0-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished — metoda</span><span class="sxs-lookup"><span data-stu-id="b2ab0-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)   
