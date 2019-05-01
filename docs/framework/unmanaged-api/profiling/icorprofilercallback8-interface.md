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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049729"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="0836e-102">ICorProfilerCallback8 Interface</span><span class="sxs-lookup"><span data-stu-id="0836e-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="0836e-103">[Obsługiwane w programie .NET Framework 4.7 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="0836e-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="0836e-104">Podklasa klasy [ICorProfilerCallback7](icorprofilercallback7-interface.md) zapewniający metody wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego powiadomić profiler, który kompilację JIT metoda dynamiczna ma rozpoczęcia i zakończenia.</span><span class="sxs-lookup"><span data-stu-id="0836e-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span> 
  
## <a name="methods"></a><span data-ttu-id="0836e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0836e-105">Methods</span></span>  
  
|<span data-ttu-id="0836e-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="0836e-106">Method</span></span>|<span data-ttu-id="0836e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0836e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0836e-108">DynamicMethodJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="0836e-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="0836e-109">Powiadamia program profilujący rozpoczęto kompilację JIT metodę dynamiczną.</span><span class="sxs-lookup"><span data-stu-id="0836e-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="0836e-110">DynamicMethodJITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="0836e-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="0836e-111">Powiadamia program profilujący zakończenie kompilację JIT metodę dynamiczną.</span><span class="sxs-lookup"><span data-stu-id="0836e-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0836e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0836e-112">Requirements</span></span>  
 <span data-ttu-id="0836e-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0836e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0836e-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0836e-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="0836e-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0836e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0836e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0836e-116">See also</span></span>

- [<span data-ttu-id="0836e-117">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="0836e-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0836e-118">ICorProfilerCallback9, interfejs</span><span class="sxs-lookup"><span data-stu-id="0836e-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
