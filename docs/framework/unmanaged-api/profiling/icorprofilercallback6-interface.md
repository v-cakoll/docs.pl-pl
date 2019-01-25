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
ms.openlocfilehash: c5025f4bb6433d193ecf7dec1d8375104147e9e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562573"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="c46c2-102">Interfejs ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="c46c2-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="c46c2-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="c46c2-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c46c2-104">Podklasa klasy [icorprofilercallback5 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) który zapewnia metodę wywołania zwrotnego, który środowiska uruchomieniowego języka wspólnego używa powiadomić profiler, który jest ładowany zestaw.</span><span class="sxs-lookup"><span data-stu-id="c46c2-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c46c2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c46c2-105">Methods</span></span>  
  
|<span data-ttu-id="c46c2-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c46c2-106">Method</span></span>|<span data-ttu-id="c46c2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c46c2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c46c2-108">GetAssemblyReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="c46c2-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="c46c2-109">Powiadamia program profilujący, że zestaw w bardzo wczesnym ładowania etapie, gdy środowisko uruchomieniowe języka wspólnego wykonuje przeszukiwania zamknięcia odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="c46c2-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c46c2-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c46c2-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c46c2-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c46c2-111">Requirements</span></span>  
 <span data-ttu-id="c46c2-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c46c2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c46c2-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c46c2-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c46c2-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c46c2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c46c2-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c46c2-115">See also</span></span>
- [<span data-ttu-id="c46c2-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="c46c2-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
