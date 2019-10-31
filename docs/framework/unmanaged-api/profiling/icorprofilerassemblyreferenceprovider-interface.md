---
title: Interfejs ICorProfilerAssemblyReferenceProvider
ms.date: 03/30/2017
api_name:
- ICorProfilerAssemblyReferenceProvider
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type:
- apiref
ms.openlocfilehash: f5ba72dca25889fb57c0ae1bb2429e54a8cf2228
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128716"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="1179f-102">Interfejs ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="1179f-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="1179f-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="1179f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1179f-104">Umożliwia programowi Profiler poinformowanie środowiska uruchomieniowego języka wspólnego (CLR) o odwołaniach do zestawu, które Profiler doda do wywołania zwrotnego [ICorProfilerCallback:: ModuleLoadFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1179f-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1179f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1179f-105">Methods</span></span>  
  
|<span data-ttu-id="1179f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="1179f-106">Method</span></span>|<span data-ttu-id="1179f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1179f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1179f-108">AddAssemblyReference, metoda</span><span class="sxs-lookup"><span data-stu-id="1179f-108">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="1179f-109">Informuje środowisko CLR odwołania do zestawu, które program Profiler ma dodać do wywołania zwrotnego [ModuleLoadFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1179f-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1179f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1179f-110">Remarks</span></span>  
 <span data-ttu-id="1179f-111">Środowisko CLR przekazuje profilerowi obiekt interfejsu `ICorProfilerAssemblyReferenceProvider` w wywołaniu zwrotnym [ICorProfilerCallback6:: GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1179f-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="1179f-112">Dzięki temu Profiler będzie informować CLR o odwołaniach do zestawów, które Profiler ma dodać później w [ICorProfilerCallback:: ModuleLoadFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="1179f-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="1179f-113">wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="1179f-113">callback.</span></span> <span data-ttu-id="1179f-114">Poprawia to dokładność analizatora zamknięcia odwołań do zestawu środowiska CLR i jego algorytmy umożliwiające określenie, czy zestawy mogą być udostępniane.</span><span class="sxs-lookup"><span data-stu-id="1179f-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="1179f-115">Tego interfejsu można używać tylko w wywołaniu zwrotnym [ICorProfilerCallback6:: GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) , które przekazuje ten obiekt interfejsu do profilera.</span><span class="sxs-lookup"><span data-stu-id="1179f-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1179f-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1179f-116">Requirements</span></span>  
 <span data-ttu-id="1179f-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1179f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1179f-118">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1179f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1179f-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1179f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1179f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1179f-120">See also</span></span>

- [<span data-ttu-id="1179f-121">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="1179f-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
