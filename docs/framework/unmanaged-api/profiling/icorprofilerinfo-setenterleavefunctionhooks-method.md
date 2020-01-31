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
ms.openlocfilehash: f7bc1954d11134a4515d2e29e9e0eb1626ae5d26
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863431"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="bdda2-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks — Metoda</span><span class="sxs-lookup"><span data-stu-id="bdda2-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="bdda2-103">Określa funkcje zaimplementowane przez profiler, które mają być wywoływane w podpunktach "Enter", "urlop" i "tailcall" punktów zarządzanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="bdda2-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdda2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bdda2-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdda2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bdda2-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="bdda2-106">podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionEnter —](functionenter-function.md) .</span><span class="sxs-lookup"><span data-stu-id="bdda2-106">[in] A pointer to the implementation to be used as the [FunctionEnter](functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="bdda2-107">podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionLeave —](functionleave-function.md) .</span><span class="sxs-lookup"><span data-stu-id="bdda2-107">[in] A pointer to the implementation to be used as the [FunctionLeave](functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="bdda2-108">podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionTailcall —](functiontailcall-function.md) .</span><span class="sxs-lookup"><span data-stu-id="bdda2-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdda2-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bdda2-109">Remarks</span></span>  
 <span data-ttu-id="bdda2-110">W .NET Framework w wersji 1,0, każdy wskaźnik funkcji może mieć wartość null, aby wyłączyć odpowiednie wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="bdda2-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="bdda2-111">Tylko jeden zestaw wywołań zwrotnych może być aktywny w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="bdda2-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="bdda2-112">W takim przypadku, jeśli Profiler wywoła zarówno `SetEnterLeaveFunctionHooks`, jak i [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 —](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), to `SetEnterLeaveFunctionHooks2` ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="bdda2-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="bdda2-113">Metodę `SetEnterLeaveFunctionHooks` można wywołać tylko z [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) wywołania zwrotnego profilera.</span><span class="sxs-lookup"><span data-stu-id="bdda2-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdda2-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bdda2-114">Requirements</span></span>  
 <span data-ttu-id="bdda2-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdda2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdda2-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bdda2-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bdda2-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bdda2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdda2-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdda2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdda2-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bdda2-119">See also</span></span>

- [<span data-ttu-id="bdda2-120">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="bdda2-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
