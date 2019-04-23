---
title: ICorProfilerCallback8 Interface
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
ms.openlocfilehash: e536e61a8d812e442e1e54188c99d6a1d4586757
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59125570"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="cff2a-102">ICorProfilerCallback8 Interface</span><span class="sxs-lookup"><span data-stu-id="cff2a-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="cff2a-103">[Obsługiwane w programie .NET Framework 4.7 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="cff2a-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="cff2a-104">Podklasa klasy [ICorProfilerCallback7](icorprofilercallback7-interface.md) zapewniający metody wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego powiadomić profiler, który kompilację JIT metoda dynamiczna ma rozpoczęcia i zakończenia.</span><span class="sxs-lookup"><span data-stu-id="cff2a-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="cff2a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="cff2a-105">Methods</span></span>  
  
|<span data-ttu-id="cff2a-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="cff2a-106">Method</span></span>|<span data-ttu-id="cff2a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cff2a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cff2a-108">DynamicMethodJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="cff2a-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="cff2a-109">Powiadamia program profilujący rozpoczęto kompilację JIT metodę dynamiczną.</span><span class="sxs-lookup"><span data-stu-id="cff2a-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="cff2a-110">DynamicMethodJITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="cff2a-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="cff2a-111">Powiadamia program profilujący zakończenie kompilację JIT metodę dynamiczną.</span><span class="sxs-lookup"><span data-stu-id="cff2a-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cff2a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cff2a-112">Requirements</span></span>  
 <span data-ttu-id="cff2a-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cff2a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cff2a-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cff2a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="cff2a-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="cff2a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="cff2a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cff2a-116">See also</span></span>

- [<span data-ttu-id="cff2a-117">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="cff2a-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="cff2a-118">ICorProfilerCallback9, interfejs</span><span class="sxs-lookup"><span data-stu-id="cff2a-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
