---
title: ICorProfilerCallback8, interfejs
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 617b27923e96d9abc62ccbf158b076c6e45b20a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175099"
---
# <a name="icorprofilercallback8-interface"></a><span data-ttu-id="45eb2-102">ICorProfilerCallback8, interfejs</span><span class="sxs-lookup"><span data-stu-id="45eb2-102">ICorProfilerCallback8 Interface</span></span>
<span data-ttu-id="45eb2-103">[Obsługiwane w .NET Framework 4.7 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="45eb2-103">[Supported in the .NET Framework 4.7 and later versions]</span></span>  

 <span data-ttu-id="45eb2-104">Podklasa [ICorProfilerCallback7,](icorprofilercallback7-interface.md) która udostępnia metody wywołania zwrotnego używane przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera, że kompilacja JIT metody dynamicznej została uruchomiona i zakończona.</span><span class="sxs-lookup"><span data-stu-id="45eb2-104">A subclass of [ICorProfilerCallback7](icorprofilercallback7-interface.md) that provides callback methods used by the common language runtime to notify the profiler that JIT compilation of a dynamic method has started and finished.</span></span>
  
## <a name="methods"></a><span data-ttu-id="45eb2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="45eb2-105">Methods</span></span>  
  
|<span data-ttu-id="45eb2-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="45eb2-106">Method</span></span>|<span data-ttu-id="45eb2-107">Opis</span><span class="sxs-lookup"><span data-stu-id="45eb2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="45eb2-108">DynamicMethodJITCompilationStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="45eb2-108">DynamicMethodJITCompilationStarted Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|<span data-ttu-id="45eb2-109">Powiadamia profiler, że kompilacja JIT metody dynamicznej została uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="45eb2-109">Notifies the profiler that JIT compilation of a dynamic method has started.</span></span>|  
|[<span data-ttu-id="45eb2-110">DynamicMethodJITCompilationFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="45eb2-110">DynamicMethodJITCompilationFinished Method</span></span>](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|<span data-ttu-id="45eb2-111">Powiadamia profiler, że kompilacja JIT metody dynamicznej została zakończona.</span><span class="sxs-lookup"><span data-stu-id="45eb2-111">Notifies the profiler that JIT compilation of a dynamic method has finished.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="45eb2-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45eb2-112">Requirements</span></span>  
 <span data-ttu-id="45eb2-113">**Platformy:** Zobacz [Wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45eb2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45eb2-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45eb2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
<span data-ttu-id="45eb2-115">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="45eb2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="45eb2-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45eb2-116">See also</span></span>

- [<span data-ttu-id="45eb2-117">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="45eb2-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="45eb2-118">ICorProfilerCallback9, interfejs</span><span class="sxs-lookup"><span data-stu-id="45eb2-118">ICorProfilerCallback9 Interface</span></span>](icorprofilercallback9-interface.md)
