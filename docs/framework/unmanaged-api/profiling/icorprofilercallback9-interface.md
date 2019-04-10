---
title: ICorProfilerCallback9 Interface
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
ms.openlocfilehash: e1711def5e2aa41fd63912361ef8250ad160fb88
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227759"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="f34fc-102">ICorProfilerCallback9 Interface</span><span class="sxs-lookup"><span data-stu-id="f34fc-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="f34fc-103">[Obsługiwane w programie .NET Framework 4.7.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="f34fc-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="f34fc-104">Podklasa klasy [ICorProfilerCallback8](icorprofilercallback8-interface.md) który zapewnia metodę wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego powiadomić profiler, że metoda dynamiczna został pamięci zbierane i następnie zwolnione.</span><span class="sxs-lookup"><span data-stu-id="f34fc-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f34fc-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f34fc-105">Methods</span></span>  
  
|<span data-ttu-id="f34fc-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="f34fc-106">Method</span></span>|<span data-ttu-id="f34fc-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f34fc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f34fc-108">DynamicMethodUnloaded, metoda</span><span class="sxs-lookup"><span data-stu-id="f34fc-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="f34fc-109">Powiadamia program profilujący, że metoda dynamiczna został pamięci zbierane i następnie zwolnione.</span><span class="sxs-lookup"><span data-stu-id="f34fc-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f34fc-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f34fc-110">Requirements</span></span>  
 <span data-ttu-id="f34fc-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f34fc-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f34fc-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f34fc-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
**<span data-ttu-id="f34fc-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f34fc-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a><span data-ttu-id="f34fc-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f34fc-114">See also</span></span>

- [<span data-ttu-id="f34fc-115">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="f34fc-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f34fc-116">ICorProfilerCallback8, interfejs</span><span class="sxs-lookup"><span data-stu-id="f34fc-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="f34fc-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span><span class="sxs-lookup"><span data-stu-id="f34fc-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="f34fc-118">Metoda ICorProfilerCallback8.DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="f34fc-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
