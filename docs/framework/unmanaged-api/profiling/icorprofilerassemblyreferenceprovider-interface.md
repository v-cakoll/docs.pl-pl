---
title: Interfejs ICorProfilerAssemblyReferenceProvider
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerAssemblyReferenceProvider
api_location: mscorwks.dll
api_type: COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 203362d2780d372236b05f753bedc0d59565d2b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a><span data-ttu-id="1443f-102">Interfejs ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="1443f-102">ICorProfilerAssemblyReferenceProvider Interface</span></span>
<span data-ttu-id="1443f-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="1443f-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="1443f-104">Włącza profiler do informowania środowisko uruchomieniowe języka wspólnego (CLR) z odwołaniami do zestawów, które profilera doda w [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="1443f-104">Enables the profiler to inform the common language runtime (CLR) of assembly references that the profiler will add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1443f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1443f-105">Methods</span></span>  
  
|<span data-ttu-id="1443f-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="1443f-106">Method</span></span>|<span data-ttu-id="1443f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1443f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1443f-108">AddAssemblyReference, metoda</span><span class="sxs-lookup"><span data-stu-id="1443f-108">AddAssemblyReference Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|<span data-ttu-id="1443f-109">Informuje o CLR odwołania do zestawu, który profilera zamierza dodatek [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="1443f-109">Informs the CLR of an assembly reference that the profiler plans to add in the [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1443f-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1443f-110">Remarks</span></span>  
 <span data-ttu-id="1443f-111">Środowisko CLR przekazuje profilera `ICorProfilerAssemblyReferenceProvider` obiektu interfejsu w [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="1443f-111">The CLR passes the profiler an `ICorProfilerAssemblyReferenceProvider` interface object in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="1443f-112">Dzięki temu profiler do informowania CLR odwołania do zestawów, które planuje dodać później w profilera [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span><span class="sxs-lookup"><span data-stu-id="1443f-112">This enables the profiler to inform the CLR of assembly references that the profiler plans to add later in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md).</span></span> <span data-ttu-id="1443f-113">Wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="1443f-113">callback.</span></span> <span data-ttu-id="1443f-114">Zwiększa to dokładność walkera zamknięcia odwołanie do zestawu CLR i jego algorytmów wyznaczania, czy zestawy mogą być udostępniane.</span><span class="sxs-lookup"><span data-stu-id="1443f-114">This improves the accuracy of the CLR's assembly reference closure walker and its algorithms for determining whether assemblies may be shared.</span></span>  
  
 <span data-ttu-id="1443f-115">Ten interfejs może służyć tylko w [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego, która przekazuje tego obiektu interfejsu do profilera.</span><span class="sxs-lookup"><span data-stu-id="1443f-115">This interface can be used only in the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback that passes this interface object to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1443f-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1443f-116">Requirements</span></span>  
 <span data-ttu-id="1443f-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1443f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1443f-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1443f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1443f-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1443f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1443f-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1443f-120">See Also</span></span>  
 [<span data-ttu-id="1443f-121">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="1443f-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
