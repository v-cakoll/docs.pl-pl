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
ms.openlocfilehash: 0009d935e2e3b2abf590aca270113717ceb7e2d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127485"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="47ab1-102">Interfejs ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="47ab1-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="47ab1-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="47ab1-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="47ab1-104">Podklasa elementu [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) , która zapewnia metodę wywołania zwrotnego używaną przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera o ładowaniu zestawu.</span><span class="sxs-lookup"><span data-stu-id="47ab1-104">A subclass of [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="47ab1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="47ab1-105">Methods</span></span>  
  
|<span data-ttu-id="47ab1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="47ab1-106">Method</span></span>|<span data-ttu-id="47ab1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="47ab1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="47ab1-108">GetAssemblyReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="47ab1-108">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="47ab1-109">Powiadamia program profilujący, że zestaw jest w bardzo wczesnym etapie ładowania, gdy środowisko uruchomieniowe języka wspólnego wykonuje przegląd zamknięcia odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="47ab1-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47ab1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="47ab1-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47ab1-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="47ab1-111">Requirements</span></span>  
 <span data-ttu-id="47ab1-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47ab1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47ab1-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="47ab1-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="47ab1-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47ab1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47ab1-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47ab1-115">See also</span></span>

- [<span data-ttu-id="47ab1-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="47ab1-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
