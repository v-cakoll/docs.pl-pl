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
ms.openlocfilehash: 90071121411b706052e1cbb4cb647536dae2835a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864872"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="eef64-102">Interfejs ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="eef64-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="eef64-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="eef64-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="eef64-104">Podklasa elementu [ICorProfilerCallback5](icorprofilercallback5-interface.md) , która zapewnia metodę wywołania zwrotnego używaną przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera o ładowaniu zestawu.</span><span class="sxs-lookup"><span data-stu-id="eef64-104">A subclass of [ICorProfilerCallback5](icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="eef64-105">Metody</span><span class="sxs-lookup"><span data-stu-id="eef64-105">Methods</span></span>  
  
|<span data-ttu-id="eef64-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="eef64-106">Method</span></span>|<span data-ttu-id="eef64-107">Opis</span><span class="sxs-lookup"><span data-stu-id="eef64-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="eef64-108">GetAssemblyReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="eef64-108">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="eef64-109">Powiadamia program profilujący, że zestaw jest w bardzo wczesnym etapie ładowania, gdy środowisko uruchomieniowe języka wspólnego wykonuje przegląd zamknięcia odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="eef64-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eef64-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eef64-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eef64-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="eef64-111">Requirements</span></span>  
 <span data-ttu-id="eef64-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eef64-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eef64-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="eef64-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eef64-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eef64-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eef64-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eef64-115">See also</span></span>

- [<span data-ttu-id="eef64-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="eef64-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
