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
ms.openlocfilehash: 0156a7dfa2a67ce9e62b502df00fc6bc5fccf925
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499184"
---
# <a name="icorprofilercallback6-interface"></a><span data-ttu-id="65994-102">Interfejs ICorProfilerCallback6</span><span class="sxs-lookup"><span data-stu-id="65994-102">ICorProfilerCallback6 Interface</span></span>
<span data-ttu-id="65994-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="65994-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="65994-104">Podklasa elementu [ICorProfilerCallback5](icorprofilercallback5-interface.md) , która zapewnia metodę wywołania zwrotnego używaną przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera o ładowaniu zestawu.</span><span class="sxs-lookup"><span data-stu-id="65994-104">A subclass of [ICorProfilerCallback5](icorprofilercallback5-interface.md) that provides a callback method that the common language runtime uses to notify a profiler that an assembly is loading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="65994-105">Metody</span><span class="sxs-lookup"><span data-stu-id="65994-105">Methods</span></span>  
  
|<span data-ttu-id="65994-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="65994-106">Method</span></span>|<span data-ttu-id="65994-107">Opis</span><span class="sxs-lookup"><span data-stu-id="65994-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="65994-108">GetAssemblyReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="65994-108">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)|<span data-ttu-id="65994-109">Powiadamia program profilujący, że zestaw jest w bardzo wczesnym etapie ładowania, gdy środowisko uruchomieniowe języka wspólnego wykonuje przegląd zamknięcia odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="65994-109">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65994-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65994-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65994-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65994-111">Requirements</span></span>  
 <span data-ttu-id="65994-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65994-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65994-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="65994-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65994-114">**.NET Framework wersje:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65994-114">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65994-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65994-115">See also</span></span>

- [<span data-ttu-id="65994-116">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="65994-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
