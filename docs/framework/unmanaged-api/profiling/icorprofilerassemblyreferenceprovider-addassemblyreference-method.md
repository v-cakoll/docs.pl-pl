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
ms.openlocfilehash: 33430db8f83f446bab21b1fc86a5c165aecef2af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452367"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="78e10-102">Metoda ICorProfilerAssemblyReferenceProvider::AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="78e10-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="78e10-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="78e10-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="78e10-104">Informuje o środowisko uruchomieniowe języka wspólnego (CLR) z odwołania do zestawu, który profilera zamierza dodatek [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="78e10-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78e10-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="78e10-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78e10-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="78e10-106">Parameters</span></span>  
 <span data-ttu-id="78e10-107">pAssemblyRefInfo</span><span class="sxs-lookup"><span data-stu-id="78e10-107">pAssemblyRefInfo</span></span>  
 <span data-ttu-id="78e10-108">Wskaźnik do [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) strukturę, która dostarcza informacji na temat odwołania do zestawu, do którego on należy wziąć pod uwagę podczas przeszukiwania zamknięcia odwołanie do zestawu CLR.</span><span class="sxs-lookup"><span data-stu-id="78e10-108">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78e10-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78e10-109">Remarks</span></span>  
 <span data-ttu-id="78e10-110">Profiler wywołuje tę metodę dla każdego zestawu docelowego planuje odwoływać się z zestawu określonego w `wszAssemblyPath` argument [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="78e10-110">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="78e10-111">[ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) obiekt interfejsu jest przekazywany do profilera [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) wywołania zwrotnego, wraz z zestawu ścieżki i nazwy w `wszAssemblyPath` argumentu.</span><span class="sxs-lookup"><span data-stu-id="78e10-111">The [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78e10-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78e10-112">Requirements</span></span>  
 <span data-ttu-id="78e10-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78e10-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78e10-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="78e10-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="78e10-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78e10-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78e10-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78e10-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78e10-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="78e10-117">See Also</span></span>  
 [<span data-ttu-id="78e10-118">ICorProfilerAssemblyReferenceProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="78e10-118">ICorProfilerAssemblyReferenceProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 [<span data-ttu-id="78e10-119">GetAssemblyReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="78e10-119">GetAssemblyReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)  
 [<span data-ttu-id="78e10-120">ModuleLoadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="78e10-120">ModuleLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
