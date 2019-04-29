---
title: Metoda ICorProfilerAssemblyReferenceProvider::AddAssemblyReference
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerAssemblyReferenceProvider.AddAssemblyReference
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 3d5af8e7-c337-48f4-9fa6-97c83878b9b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09ce4f3a293e7870ddadf4ad6ee2c15de10f4594
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598538"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="0dfc9-102">Metoda ICorProfilerAssemblyReferenceProvider::AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="0dfc9-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="0dfc9-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="0dfc9-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0dfc9-104">Informuje środowisko uruchomieniowe języka wspólnego (CLR) z odwołania do zestawu, który profilera zamierza dodać w [icorprofilercallback::moduleloadfinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="0dfc9-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dfc9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="0dfc9-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0dfc9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0dfc9-106">Parameters</span></span>  
 <span data-ttu-id="0dfc9-107">pAssemblyRefInfo</span><span class="sxs-lookup"><span data-stu-id="0dfc9-107">pAssemblyRefInfo</span></span>  
 <span data-ttu-id="0dfc9-108">Wskaźnik do [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) strukturę, która udostępnia środowisko CLR z informacjami dotyczącymi odwołania do zestawu, należy rozważyć, podczas przeszukiwania zamknięcia odwołanie do zestawu.</span><span class="sxs-lookup"><span data-stu-id="0dfc9-108">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0dfc9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0dfc9-109">Remarks</span></span>  
 <span data-ttu-id="0dfc9-110">Program profilujący wywołuje tę metodę dla każdego zestawu docelowego, firma planuje odwoływać się z zestawu określonego w `wszAssemblyPath` argument [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="0dfc9-110">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="0dfc9-111">[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interfejsu obiekt jest przekazywany do profilera [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołanie zwrotne, wraz z nazwą w i ścieżka zestawu `wszAssemblyPath` argumentu.</span><span class="sxs-lookup"><span data-stu-id="0dfc9-111">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dfc9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0dfc9-112">Requirements</span></span>  
 <span data-ttu-id="0dfc9-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dfc9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dfc9-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0dfc9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0dfc9-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0dfc9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0dfc9-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dfc9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dfc9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0dfc9-117">See also</span></span>

- [<span data-ttu-id="0dfc9-118">ICorProfilerAssemblyReferenceProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="0dfc9-118">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="0dfc9-119">GetAssemblyReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="0dfc9-119">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="0dfc9-120">ModuleLoadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="0dfc9-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
