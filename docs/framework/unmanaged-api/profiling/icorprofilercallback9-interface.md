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
ms.openlocfilehash: a6c480af921fb0259ef85beec8d8f65bdd430522
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689320"
---
# <a name="icorprofilercallback9-interface"></a><span data-ttu-id="8f4e3-102">ICorProfilerCallback9 Interface</span><span class="sxs-lookup"><span data-stu-id="8f4e3-102">ICorProfilerCallback9 Interface</span></span>
<span data-ttu-id="8f4e3-103">[Obsługiwane w programie .NET Framework 4.7.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="8f4e3-103">[Supported in the .NET Framework 4.7.2 and later versions]</span></span>  

 <span data-ttu-id="8f4e3-104">Podklasa klasy [ICorProfilerCallback8](icorprofilercallback8-interface.md) który zapewnia metodę wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego powiadomić profiler, że metoda dynamiczna został pamięci zbierane i następnie zwolnione.</span><span class="sxs-lookup"><span data-stu-id="8f4e3-104">A subclass of [ICorProfilerCallback8](icorprofilercallback8-interface.md) that provides a callback method used by the common language runtime to notify the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8f4e3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8f4e3-105">Methods</span></span>  
  
|<span data-ttu-id="8f4e3-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="8f4e3-106">Method</span></span>|<span data-ttu-id="8f4e3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8f4e3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8f4e3-108">DynamicMethodUnloaded, metoda</span><span class="sxs-lookup"><span data-stu-id="8f4e3-108">DynamicMethodUnloaded Method</span></span>](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|<span data-ttu-id="8f4e3-109">Powiadamia program profilujący, że metoda dynamiczna został pamięci zbierane i następnie zwolnione.</span><span class="sxs-lookup"><span data-stu-id="8f4e3-109">Notifies the profiler that a dynamic method has been garbage collected and subsequently unloaded.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f4e3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8f4e3-110">Requirements</span></span>  
 <span data-ttu-id="8f4e3-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f4e3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f4e3-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8f4e3-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="8f4e3-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8f4e3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="8f4e3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8f4e3-114">See also</span></span>
- [<span data-ttu-id="8f4e3-115">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="8f4e3-115">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="8f4e3-116">ICorProfilerCallback8, interfejs</span><span class="sxs-lookup"><span data-stu-id="8f4e3-116">ICorProfilerCallback8 Interface</span></span>](icorprofilercallback9-interface.md)
- [<span data-ttu-id="8f4e3-117">Metoda ICorProfilerCallback8.DynamicMethodJITCompilationStarted</span><span class="sxs-lookup"><span data-stu-id="8f4e3-117">ICorProfilerCallback8.DynamicMethodJITCompilationStarted method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [<span data-ttu-id="8f4e3-118">Metoda ICorProfilerCallback8.DynamicMethodJITCompilationFinished</span><span class="sxs-lookup"><span data-stu-id="8f4e3-118">ICorProfilerCallback8.DynamicMethodJITCompilationFinished method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
