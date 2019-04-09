---
title: ICorProfilerInfo3::GetFunctionTailcall3Info — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40e518e3cf5967d2b0a7eda8c7b58ec0f918e219
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187437"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a><span data-ttu-id="b93b2-102">ICorProfilerInfo3::GetFunctionTailcall3Info — Metoda</span><span class="sxs-lookup"><span data-stu-id="b93b2-102">ICorProfilerInfo3::GetFunctionTailcall3Info Method</span></span>
<span data-ttu-id="b93b2-103">Udostępnia ramki stosu funkcji, która jest zgłaszany do profilera za [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) funkcji.</span><span class="sxs-lookup"><span data-stu-id="b93b2-103">Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) function.</span></span> <span data-ttu-id="b93b2-104">Ta metoda może być wywoływana tylko podczas `FunctionTailcall3WithInfo` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b93b2-104">This method can be called only during the `FunctionTailcall3WithInfo` callback.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b93b2-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b93b2-105">Syntax</span></span>  
  
```  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b93b2-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b93b2-106">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="b93b2-107">[in] `FunctionID` Funkcji, która zwraca.</span><span class="sxs-lookup"><span data-stu-id="b93b2-107">[in] The `FunctionID` of the function that is returning.</span></span>  
  
 `eltInfo`  
 <span data-ttu-id="b93b2-108">[in] Dojście nieprzezroczyste reprezentujący informacji na temat ramkę stosu w danym.</span><span class="sxs-lookup"><span data-stu-id="b93b2-108">[in] An opaque handle that represents information about a given stack frame.</span></span> <span data-ttu-id="b93b2-109">Program profilujący powinien udostępniać takie same `eltInfo` , zostało przekazane do profilera za `FunctionTailcall3WithInfo` funkcji.</span><span class="sxs-lookup"><span data-stu-id="b93b2-109">The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.</span></span>  
  
 `pFrameInfo`  
 <span data-ttu-id="b93b2-110">[out] Dojście nieprzezroczyste reprezentujący typów ogólnych informacji na temat ramkę stosu w danym.</span><span class="sxs-lookup"><span data-stu-id="b93b2-110">[out] An opaque handle that represents generics information about a given stack frame.</span></span> <span data-ttu-id="b93b2-111">Tego dojścia jest prawidłowy tylko podczas `FunctionTailcall3WithInfo` wywołania zwrotnego, w którym profiler wywołał metodę `GetFunctionTailcall3Info` metody.</span><span class="sxs-lookup"><span data-stu-id="b93b2-111">This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b93b2-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b93b2-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b93b2-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b93b2-113">Requirements</span></span>  
 <span data-ttu-id="b93b2-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b93b2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b93b2-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b93b2-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b93b2-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b93b2-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b93b2-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b93b2-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b93b2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b93b2-118">See also</span></span>

- [<span data-ttu-id="b93b2-119">FunctionEnter3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b93b2-119">FunctionEnter3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [<span data-ttu-id="b93b2-120">FunctionLeave3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b93b2-120">FunctionLeave3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [<span data-ttu-id="b93b2-121">FunctionTailcall3WithInfo</span><span class="sxs-lookup"><span data-stu-id="b93b2-121">FunctionTailcall3WithInfo</span></span>](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [<span data-ttu-id="b93b2-122">ICorProfilerInfo3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b93b2-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="b93b2-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="b93b2-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="b93b2-124">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="b93b2-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
