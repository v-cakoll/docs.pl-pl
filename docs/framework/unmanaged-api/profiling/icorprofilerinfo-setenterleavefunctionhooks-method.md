---
title: ICorProfilerInfo::SetEnterLeaveFunctionHooks — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEnterLeaveFunctionHooks
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEnterLeaveFunctionHooks
helpviewer_keywords:
- SetEnterLeaveFunctionHooks method [.NET Framework profiling]
- ICorProfilerInfo::SetEnterLeaveFunctionHooks method [.NET Framework profiling]
ms.assetid: 72399636-c219-4ffd-8ac8-39432c9d4641
topic_type:
- apiref
ms.openlocfilehash: 45593e7e30e1c8f8036489936aab3c607b01dd52
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438649"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="1ab24-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks — Metoda</span><span class="sxs-lookup"><span data-stu-id="1ab24-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="1ab24-103">Określa funkcje zaimplementowane przez profiler, które mają być wywoływane w podpunktach "Enter", "urlop" i "tailcall" punktów zarządzanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="1ab24-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ab24-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1ab24-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ab24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1ab24-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="1ab24-106">podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionEnter —](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) .</span><span class="sxs-lookup"><span data-stu-id="1ab24-106">[in] A pointer to the implementation to be used as the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="1ab24-107">podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionLeave —](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) .</span><span class="sxs-lookup"><span data-stu-id="1ab24-107">[in] A pointer to the implementation to be used as the [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="1ab24-108">podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionTailcall —](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) .</span><span class="sxs-lookup"><span data-stu-id="1ab24-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ab24-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1ab24-109">Remarks</span></span>  
 <span data-ttu-id="1ab24-110">W .NET Framework w wersji 1,0, każdy wskaźnik funkcji może mieć wartość null, aby wyłączyć odpowiednie wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="1ab24-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="1ab24-111">Tylko jeden zestaw wywołań zwrotnych może być aktywny w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="1ab24-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="1ab24-112">W takim przypadku, jeśli Profiler wywoła zarówno `SetEnterLeaveFunctionHooks`, jak i [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), to `SetEnterLeaveFunctionHooks2` ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="1ab24-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="1ab24-113">Metodę `SetEnterLeaveFunctionHooks` można wywołać tylko z [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego profilera.</span><span class="sxs-lookup"><span data-stu-id="1ab24-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ab24-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1ab24-114">Requirements</span></span>  
 <span data-ttu-id="1ab24-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ab24-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ab24-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1ab24-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1ab24-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1ab24-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ab24-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ab24-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ab24-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1ab24-119">See also</span></span>

- [<span data-ttu-id="1ab24-120">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="1ab24-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
