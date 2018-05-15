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
ms.openlocfilehash: 05e571149a794cbffa9e602255455d779a83e2a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="72ed3-102">Interfejs ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="72ed3-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="72ed3-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="72ed3-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="72ed3-104">Podklasa [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) zapewnia metody wywołania zwrotnego, która środowisko uruchomieniowe języka wspólnego używa powiadomiono profilera, który jest ładowany zestaw.</span><span class="sxs-lookup"><span data-stu-id="72ed3-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72ed3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="72ed3-105">Methods</span></span>  
  
|<span data-ttu-id="72ed3-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="72ed3-106">Method</span></span>|<span data-ttu-id="72ed3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="72ed3-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72ed3-108">GetAssemblyReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="72ed3-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="72ed3-109">Powiadamia profilera, że zestaw w bardzo wczesny ładuje etapie, gdy środowisko uruchomieniowe języka wspólnego wykonuje przeszukiwania zamknięcia odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="72ed3-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72ed3-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72ed3-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72ed3-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="72ed3-111">Requirements</span></span>  
 <span data-ttu-id="72ed3-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72ed3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72ed3-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="72ed3-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="72ed3-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72ed3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72ed3-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="72ed3-115">See Also</span></span>  
 [<span data-ttu-id="72ed3-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="72ed3-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
