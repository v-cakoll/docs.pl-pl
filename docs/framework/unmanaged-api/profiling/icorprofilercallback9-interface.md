---
title: ICorProfilerCallback9, interfejs
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c383a2e221e61770d3c28a65c561c48f6059b6d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136564"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="05fe1-102">ICorProfilerCallback9, interfejs</span><span class="sxs-lookup"><span data-stu-id="05fe1-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="05fe1-103">[Obsługiwane w .NET Framework 4.7.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="05fe1-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="05fe1-104">Podklasa elementu [ICorProfilerCallback8](icorprofilercallback8-interface.md) , która zapewnia metodę wywołania zwrotnego używaną przez środowisko uruchomieniowe języka wspólnego do powiadomienia profilera, że metoda dynamiczna została odtworzona, a następnie zwolniona z pamięci.</span><span class="sxs-lookup"><span data-stu-id="05fe1-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05fe1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="05fe1-105">Methods</span></span>  
  
|<span data-ttu-id="05fe1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="05fe1-106">Method</span></span>|<span data-ttu-id="05fe1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="05fe1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05fe1-108">DynamicMethodUnloaded, metoda</span><span class="sxs-lookup"><span data-stu-id="05fe1-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="05fe1-109">Powiadamia program profilujący, że metoda dynamiczna została odtworzona, a następnie zwolniona.</span><span class="sxs-lookup"><span data-stu-id="05fe1-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05fe1-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05fe1-110">Requirements</span></span>  
 <span data-ttu-id="05fe1-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05fe1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05fe1-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="05fe1-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="05fe1-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="05fe1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="05fe1-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05fe1-114">See also</span></span>

- [<span data-ttu-id="05fe1-115">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="05fe1-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="05fe1-116">ICorProfilerCallback8, interfejs</span><span class="sxs-lookup"><span data-stu-id="05fe1-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="05fe1-117">ICorProfilerCallback8. DynamicMethodJITCompilationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="05fe1-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="05fe1-118">ICorProfilerCallback8. DynamicMethodJITCompilationFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="05fe1-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
