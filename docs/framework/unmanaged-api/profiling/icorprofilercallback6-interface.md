---
title: Interfejs ICorProfilerCallback6
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8fda98c20b42355b9f52595929bbf5b980b5b857
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077241"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="7650c-102">Interfejs ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="7650c-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="7650c-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="7650c-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="7650c-104">Podklasa klasy [icorprofilercallback5 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) który zapewnia metodę wywołania zwrotnego, który środowiska uruchomieniowego języka wspólnego używa powiadomić profiler, który jest ładowany zestaw.</span><span class="sxs-lookup"><span data-stu-id="7650c-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7650c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7650c-105">Methods</span></span>  
  
|<span data-ttu-id="7650c-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7650c-106">Method</span></span>|<span data-ttu-id="7650c-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7650c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7650c-108">GetAssemblyReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="7650c-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="7650c-109">Powiadamia program profilujący, że zestaw w bardzo wczesnym ładowania etapie, gdy środowisko uruchomieniowe języka wspólnego wykonuje przeszukiwania zamknięcia odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="7650c-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7650c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7650c-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7650c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7650c-111">Requirements</span></span>  
 <span data-ttu-id="7650c-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7650c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7650c-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7650c-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7650c-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7650c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7650c-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7650c-115">See also</span></span>

- [<span data-ttu-id="7650c-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="7650c-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
