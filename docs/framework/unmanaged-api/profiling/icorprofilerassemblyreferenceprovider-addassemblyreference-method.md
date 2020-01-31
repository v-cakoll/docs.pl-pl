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
ms.openlocfilehash: 2357e5348192db5d41adfe1176300359440aeee3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866731"
---
# <a name="icorprofilerassemblyreferenceprovideraddassemblyreference-method"></a><span data-ttu-id="e822a-102">Metoda ICorProfilerAssemblyReferenceProvider::AddAssemblyReference</span><span class="sxs-lookup"><span data-stu-id="e822a-102">ICorProfilerAssemblyReferenceProvider::AddAssemblyReference Method</span></span>
<span data-ttu-id="e822a-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="e822a-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e822a-104">Informuje środowisko uruchomieniowe języka wspólnego (CLR) odwołania do zestawu, które program Profiler ma dodać do wywołania zwrotnego [ICorProfilerCallback:: ModuleLoadFinished —](icorprofilercallback-moduleloadfinished-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e822a-104">Informs the common language runtime (CLR) of an assembly reference that the profiler plans to add in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e822a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e822a-105">Syntax</span></span>  
  
```cpp
HRESULT AddAssemblyReference(  
        const COR_PRF_ASSEMBLY_REFERENCE_INFO* pAssemblyRefInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e822a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="e822a-106">Parameters</span></span>

- `pAssemblyRefInfo`

  <span data-ttu-id="e822a-107">Wskaźnik do struktury [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) , która dostarcza środowisko CLR z informacjami o odwołaniu do zestawu, które należy wziąć pod uwagę podczas przeprowadzania przeszukiwania odwołań do zestawu.</span><span class="sxs-lookup"><span data-stu-id="e822a-107">A pointer to a [COR_PRF_ASSEMBLY_REFERENCE_INFO](cor-prf-assembly-reference-info-structure.md) structure that provides the CLR with information about an assembly reference that it should consider when performing an assembly reference closure walk.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="e822a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e822a-108">Remarks</span></span>  
 <span data-ttu-id="e822a-109">Profiler wywołuje tę metodę dla każdego zestawu docelowego, który planuje się do odwołania z zestawu określonego w `wszAssemblyPath` argument wywołania zwrotnego [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e822a-109">The profiler calls this method for each target assembly it plans to reference from the assembly specified in the `wszAssemblyPath` argument of the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback.</span></span> <span data-ttu-id="e822a-110">Obiekt interfejsu [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) jest przesyłany do wywołania zwrotnego [ICorProfilerCallback6:: GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) , wraz ze ścieżką i nazwą zestawu w argumencie `wszAssemblyPath`.</span><span class="sxs-lookup"><span data-stu-id="e822a-110">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object is passed to the profiler's [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback, along with the assembly path and name in the `wszAssemblyPath` argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e822a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e822a-111">Requirements</span></span>  
 <span data-ttu-id="e822a-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e822a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e822a-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e822a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e822a-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e822a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e822a-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e822a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e822a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e822a-116">See also</span></span>

- [<span data-ttu-id="e822a-117">ICorProfilerAssemblyReferenceProvider, interfejs</span><span class="sxs-lookup"><span data-stu-id="e822a-117">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
- [<span data-ttu-id="e822a-118">GetAssemblyReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="e822a-118">GetAssemblyReferences Method</span></span>](icorprofilercallback6-getassemblyreferences-method.md)
- [<span data-ttu-id="e822a-119">ModuleLoadFinished, metoda</span><span class="sxs-lookup"><span data-stu-id="e822a-119">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
