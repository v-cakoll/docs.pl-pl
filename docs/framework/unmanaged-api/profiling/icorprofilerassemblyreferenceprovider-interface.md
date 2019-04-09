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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bad1cc71b9a27896141837a6d342f2cfe068fc5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089735"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="6cb82-102">Interfejs ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="6cb82-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="6cb82-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="6cb82-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6cb82-104">Włącza program profilujący do informowania środowisko uruchomieniowe języka wspólnego (CLR) z odwołań do zestawu programu profilującego doda w [icorprofilercallback::moduleloadfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="6cb82-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6cb82-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6cb82-105">Methods</span></span>  
  
|<span data-ttu-id="6cb82-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="6cb82-106">Method</span></span>|<span data-ttu-id="6cb82-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6cb82-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6cb82-108">AddAssemblyReference, metoda</span><span class="sxs-lookup"><span data-stu-id="6cb82-108">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="6cb82-109">Informuje CLR odwołanie do zestawu, który profilera zamierza dodać w [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="6cb82-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6cb82-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6cb82-110">Remarks</span></span>  
 <span data-ttu-id="6cb82-111">Środowisko CLR przekazuje profiler `ICorProfilerAssemblyReferenceProvider` obiektu interfejsu w [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="6cb82-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="6cb82-112">Dzięki temu program profilujący do informowania CLR odwołania do zestawów, które profilera zamierza dodać później w [icorprofilercallback::moduleloadfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="6cb82-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="6cb82-113">Wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="6cb82-113">callback.</span></span> <span data-ttu-id="6cb82-114">To zwiększa dokładność walker zamknięcia odwołanie do zestawu CLR i jego algorytmów do określenia, czy zestawy mogą być udostępniane.</span><span class="sxs-lookup"><span data-stu-id="6cb82-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="6cb82-115">Ten interfejs może być używana tylko w [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołanie zwrotne, które przekazuje tego obiektu interfejsu do programu profilującego.</span><span class="sxs-lookup"><span data-stu-id="6cb82-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cb82-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6cb82-116">Requirements</span></span>  
 <span data-ttu-id="6cb82-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cb82-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cb82-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6cb82-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 **<span data-ttu-id="6cb82-119">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="6cb82-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6cb82-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6cb82-120">See also</span></span>

- [<span data-ttu-id="6cb82-121">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="6cb82-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
