---
title: Interfejs ICorProfilerCallback8
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92120cc5948efca696d922448da215601f9e6b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="5baa9-102">Interfejs ICorProfilerCallback8</span><span class="sxs-lookup"><span data-stu-id="5baa9-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="5baa9-103">[Obsługiwane w programie .NET Framework 4.7 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="5baa9-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="5baa9-104">Podklasa [ICorProfilerCallback7](icorprofilercallback7-interface.md) zapewnia metody wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego powiadomiono profiler kompilacji JIT metody dynamicznej ma rozpoczęcia i zakończenia.</span><span class="sxs-lookup"><span data-stu-id="5baa9-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="5baa9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5baa9-105">Methods</span></span>  
  
|<span data-ttu-id="5baa9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5baa9-106">Method</span></span>|<span data-ttu-id="5baa9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5baa9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5baa9-108">DynamicMethodJITCompilationStarted — metoda</span><span class="sxs-lookup"><span data-stu-id="5baa9-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="5baa9-109">Powiadamia profilera uruchomienia kompilacji JIT metody dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="5baa9-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="5baa9-110">DynamicMethodJITCompilationFinished — metoda</span><span class="sxs-lookup"><span data-stu-id="5baa9-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="5baa9-111">Powiadamia profilera zakończenie kompilacji JIT metody dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="5baa9-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5baa9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5baa9-112">Requirements</span></span>  
 <span data-ttu-id="5baa9-113">**Platformy:** zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5baa9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5baa9-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5baa9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="5baa9-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5baa9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="5baa9-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5baa9-116">See Also</span></span>  
<span data-ttu-id="5baa9-117">[Interfejsy profilowania](profiling-interfaces.md) </span><span class="sxs-lookup"><span data-stu-id="5baa9-117">[Profiling Interfaces](profiling-interfaces.md) </span></span>  
[<span data-ttu-id="5baa9-118">Interfejs ICorProfilerCallback9</span><span class="sxs-lookup"><span data-stu-id="5baa9-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
