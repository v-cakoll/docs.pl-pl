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
ms.openlocfilehash: 823cc5638ff3e0955aca0bd9ba5795f6b369c6b0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863624"
---
# <a name="icorprofilerinfogetfunctioninfo-method"></a><span data-ttu-id="b40c9-102">ICorProfilerInfo::GetFunctionInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="b40c9-102">ICorProfilerInfo::GetFunctionInfo Method</span></span>
<span data-ttu-id="b40c9-103">Pobiera klasę nadrzędną i token metadanych dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b40c9-103">Gets the parent class and metadata token for the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b40c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b40c9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFunctionInfo(  
    [in]  FunctionID functionId,  
    [out] ClassID    *pClassId,  
    [out] ModuleID   *pModuleId,  
    [out] mdToken    *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b40c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b40c9-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b40c9-106">podczas Identyfikator funkcji, dla której ma zostać uzyskana Klasa nadrzędna i token metadanych.</span><span class="sxs-lookup"><span data-stu-id="b40c9-106">[in] The ID of the function for which to get the parent class and metadata token.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="b40c9-107">określoną Wskaźnik do klasy nadrzędnej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b40c9-107">[out] A pointer to the parent class of the function.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="b40c9-108">określoną Wskaźnik do modułu, w którym zdefiniowana jest Klasa nadrzędna funkcji.</span><span class="sxs-lookup"><span data-stu-id="b40c9-108">[out] A pointer to the module in which the function's parent class is defined.</span></span>  
  
 `pToken`  
 <span data-ttu-id="b40c9-109">określoną Wskaźnik do tokenu metadanych dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="b40c9-109">[out] A pointer to the metadata token for the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b40c9-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b40c9-110">Remarks</span></span>  
 <span data-ttu-id="b40c9-111">Kod profilera może wywołać [ICorProfilerInfo:: GetModuleMetaData —](icorprofilerinfo-getmodulemetadata-method.md) w celu uzyskania interfejsu metadanych dla danego modułu.</span><span class="sxs-lookup"><span data-stu-id="b40c9-111">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="b40c9-112">Token metadanych, który jest zwracany do lokalizacji, do której odwołuje się `pToken`, może następnie zostać użyty w celu uzyskania dostępu do metadanych dla funkcji.</span><span class="sxs-lookup"><span data-stu-id="b40c9-112">The metadata token that is returned to the location referenced by `pToken` can then be used to access the metadata for the function.</span></span>  
  
 <span data-ttu-id="b40c9-113">`ClassID` funkcji na klasie generycznej może nie być możliwe do uzyskania bez dodatkowych informacji kontekstowych dotyczących używania funkcji.</span><span class="sxs-lookup"><span data-stu-id="b40c9-113">The `ClassID` of a function on a generic class might not be obtainable without more contextual information about the use of the function.</span></span> <span data-ttu-id="b40c9-114">W takim przypadku `pClassId` będzie równa 0.</span><span class="sxs-lookup"><span data-stu-id="b40c9-114">In this case, `pClassId` will be 0.</span></span> <span data-ttu-id="b40c9-115">Kod profilera powinien używać [ICorProfilerInfo2:: GetFunctionInfo2 —](icorprofilerinfo2-getfunctioninfo2-method.md) z wartością COR_PRF_FRAME_INFO, aby zapewnić więcej kontekstu.</span><span class="sxs-lookup"><span data-stu-id="b40c9-115">Profiler code should use [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) with a COR_PRF_FRAME_INFO value to provide more context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b40c9-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b40c9-116">Requirements</span></span>  
 <span data-ttu-id="b40c9-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b40c9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b40c9-118">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b40c9-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b40c9-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b40c9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b40c9-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b40c9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b40c9-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b40c9-121">See also</span></span>

- [<span data-ttu-id="b40c9-122">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="b40c9-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
