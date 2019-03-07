---
title: ICorProfilerInfo::GetFunctionInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetFunctionInfo
helpviewer_keywords:
- ICorProfilerInfo::GetFunctionInfo method [.NET Framework profiling]
- GetFunctionInfo method [.NET Framework profiling]
ms.assetid: c42b5891-019d-46b3-b551-4606295b75b8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8db6912700b199c64d2ebf0f7bd2ccd8939af9b6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484709"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="a212b-102">ICorProfilerInfo::GetFunctionInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="a212b-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>
<span data-ttu-id="a212b-103">Pobiera klasy nadrzędnej i metadane token dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="a212b-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a212b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a212b-104">Syntax</span></span>  
  
```  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a212b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a212b-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="a212b-106">[in] Identyfikator funkcji, dla którego można uzyskać tokenu klasy nadrzędnej i metadanych.</span><span class="sxs-lookup"><span data-stu-id="a212b-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="a212b-107">[out] Wskaźnik do funkcji klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="a212b-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="a212b-108">[out] Wskaźnik do modułu, w którym zdefiniowano funkcji klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="a212b-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="a212b-109">[out] Wskaźnik do tokenu metadanych dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="a212b-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a212b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a212b-110">Remarks</span></span>  
 <span data-ttu-id="a212b-111">Program profilujący kodu może wywołać [icorprofilerinfo::getmodulemetadata —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) uzyskać interfejs metadanych dla danego modułu.</span><span class="sxs-lookup"><span data-stu-id="a212b-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="a212b-112">Token metadanych, które są zwracane do lokalizacji, odwołuje się `pToken` następnie może służyć do uzyskania dostępu do funkcji metadanych.</span><span class="sxs-lookup"><span data-stu-id="a212b-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="a212b-113">`ClassID` Funkcji dla klasy generycznej może nie być możliwe do uzyskania bez więcej kontekstowych informacji na temat używania funkcji.</span><span class="sxs-lookup"><span data-stu-id="a212b-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="a212b-114">W tym przypadku `pClassId` będzie mieć wartość 0.</span><span class="sxs-lookup"><span data-stu-id="a212b-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="a212b-115">Profiler kod powinien używać [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) z wartością COR_PRF_FRAME_INFO, aby zapewnić dodatkowy kontekst.</span><span class="sxs-lookup"><span data-stu-id="a212b-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a212b-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a212b-116">Requirements</span></span>  
 <span data-ttu-id="a212b-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a212b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a212b-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a212b-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a212b-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a212b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a212b-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a212b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a212b-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a212b-121">See also</span></span>
- [<span data-ttu-id="a212b-122">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="a212b-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
