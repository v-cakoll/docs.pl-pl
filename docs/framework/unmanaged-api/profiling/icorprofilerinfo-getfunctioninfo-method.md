---
title: "ICorProfilerInfo::GetFunctionInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetFunctionInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 859887d25e33b4780920ed688684c22031eac16c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="e9462-102">ICorProfilerInfo::GetFunctionInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="e9462-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>
<span data-ttu-id="e9462-103">Pobiera klasy nadrzędnej i metadanych token dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9462-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9462-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e9462-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9462-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9462-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e9462-106">[in] Identyfikator funkcji, dla którego można pobrać tokenu klasy nadrzędnej i metadanych.</span><span class="sxs-lookup"><span data-stu-id="e9462-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="e9462-107">[out] Wskaźnik do funkcji klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="e9462-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="e9462-108">[out] Wskaźnik do modułu, w którym zdefiniowana jest klasa nadrzędna funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9462-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="e9462-109">[out] Wskaźnik do tokenu metadanych dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9462-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9462-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e9462-110">Remarks</span></span>  
 <span data-ttu-id="e9462-111">Kod profiler może wywołać [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) uzyskać interfejs metadanych dla danego modułu.</span><span class="sxs-lookup"><span data-stu-id="e9462-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="e9462-112">Token metadanych, która jest zwracana do lokalizacji odwołuje się `pToken` mogą następnie służyć do uzyskania dostępu do funkcji metadanych.</span><span class="sxs-lookup"><span data-stu-id="e9462-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="e9462-113">`ClassID` Funkcji dla klasy generycznej może nie być możliwe do uzyskania bez więcej informacje kontekstowe dotyczące użycia funkcji.</span><span class="sxs-lookup"><span data-stu-id="e9462-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="e9462-114">W takim przypadku `pClassId` będzie równa 0.</span><span class="sxs-lookup"><span data-stu-id="e9462-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="e9462-115">Należy użyć kodu profilera [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) z wartością COR_PRF_FRAME_INFO, aby zapewnić więcej kontekstu.</span><span class="sxs-lookup"><span data-stu-id="e9462-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9462-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e9462-116">Requirements</span></span>  
 <span data-ttu-id="e9462-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9462-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9462-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e9462-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e9462-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9462-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9462-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9462-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9462-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9462-121">See Also</span></span>  
 [<span data-ttu-id="e9462-122">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="e9462-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
