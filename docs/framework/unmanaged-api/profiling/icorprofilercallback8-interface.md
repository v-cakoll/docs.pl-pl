---
title: ICorProfilerCallback8, interfejs
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 4516c8f9673052b521c1f0f594978236fef1e0ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136450"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="2367b-102">ICorProfilerCallback8, interfejs</span><span class="sxs-lookup"><span data-stu-id="2367b-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="2367b-103">[Obsługiwane w .NET Framework 4,7 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="2367b-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="2367b-104">Podklasa elementu [ICorProfilerCallback7](icorprofilercallback7-interface.md) , która zapewnia metody wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera o rozpoczęciu i zakończeniu kompilacji JIT metody dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="2367b-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="2367b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2367b-105">Methods</span></span>  
  
|<span data-ttu-id="2367b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="2367b-106">Method</span></span>|<span data-ttu-id="2367b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2367b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2367b-108">DynamicMethodJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="2367b-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="2367b-109">Powiadamia profiler, że została rozpoczęta kompilacja JIT metody dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="2367b-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="2367b-110">DynamicMethodJITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="2367b-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="2367b-111">Powiadamia profiler, że zakończyła się kompilacja JIT metody dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="2367b-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2367b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2367b-112">Requirements</span></span>  
 <span data-ttu-id="2367b-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2367b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2367b-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2367b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="2367b-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2367b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2367b-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2367b-116">See also</span></span>

- [<span data-ttu-id="2367b-117">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="2367b-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="2367b-118">ICorProfilerCallback9, interfejs</span><span class="sxs-lookup"><span data-stu-id="2367b-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
