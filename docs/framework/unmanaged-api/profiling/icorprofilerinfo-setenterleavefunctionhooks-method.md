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
ms.openlocfilehash: cf0726a12b0274fd7a38e82b66c33430d26b031a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497455"
---
# <a name="icorprofilerinfosetenterleavefunctionhooks-method"></a><span data-ttu-id="ed568-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks — Metoda</span><span class="sxs-lookup"><span data-stu-id="ed568-102">ICorProfilerInfo::SetEnterLeaveFunctionHooks Method</span></span>
<span data-ttu-id="ed568-103">Określa funkcje zaimplementowane przez profiler, które mają być wywoływane w podpunktach "Enter", "urlop" i "tailcall" punktów zarządzanych funkcji.</span><span class="sxs-lookup"><span data-stu-id="ed568-103">Specifies profiler-implemented functions to be called on "enter", "leave", and "tailcall" hooks of managed functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed568-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ed568-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks(  
    [in] FunctionEnter    *pFuncEnter,  
    [in] FunctionLeave    *pFuncLeave,  
    [in] FunctionTailcall *pFuncTailcall);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed568-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ed568-105">Parameters</span></span>  
 `pFuncEnter`  
 <span data-ttu-id="ed568-106">podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionEnter —](functionenter-function.md) .</span><span class="sxs-lookup"><span data-stu-id="ed568-106">[in] A pointer to the implementation to be used as the [FunctionEnter](functionenter-function.md) callback.</span></span>  
  
 `pFuncLeave`  
 <span data-ttu-id="ed568-107">podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionLeave —](functionleave-function.md) .</span><span class="sxs-lookup"><span data-stu-id="ed568-107">[in] A pointer to the implementation to be used as the [FunctionLeave](functionleave-function.md) callback.</span></span>  
  
 `pFuncTailcall`  
 <span data-ttu-id="ed568-108">podczas Wskaźnik do implementacji, który ma być używany jako wywołanie zwrotne [FunctionTailcall —](functiontailcall-function.md) .</span><span class="sxs-lookup"><span data-stu-id="ed568-108">[in] A pointer to the implementation to be used as the [FunctionTailcall](functiontailcall-function.md) callback.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed568-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ed568-109">Remarks</span></span>  
 <span data-ttu-id="ed568-110">W .NET Framework w wersji 1,0, każdy wskaźnik funkcji może mieć wartość null, aby wyłączyć odpowiednie wywołanie zwrotne.</span><span class="sxs-lookup"><span data-stu-id="ed568-110">In the .NET Framework version 1.0, each function pointer can be null to disable that corresponding callback.</span></span>  
  
 <span data-ttu-id="ed568-111">Tylko jeden zestaw wywołań zwrotnych może być aktywny w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="ed568-111">Only one set of callbacks can be active at a time.</span></span> <span data-ttu-id="ed568-112">W takim przypadku, jeśli Profiler wywołuje zarówno element `SetEnterLeaveFunctionHooks` , jak i [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 —](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), `SetEnterLeaveFunctionHooks2` ma pierwszeństwo.</span><span class="sxs-lookup"><span data-stu-id="ed568-112">Thus, if a profiler calls both `SetEnterLeaveFunctionHooks` and [ICorProfilerInfo2::SetEnterLeaveFunctionHooks2](icorprofilerinfo2-setenterleavefunctionhooks2-method.md), then `SetEnterLeaveFunctionHooks2` takes precedence.</span></span>  
  
 <span data-ttu-id="ed568-113">`SetEnterLeaveFunctionHooks`Metodę można wywołać tylko z [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) wywołania zwrotnego profilera.</span><span class="sxs-lookup"><span data-stu-id="ed568-113">The `SetEnterLeaveFunctionHooks` method can be called only from the profiler's [ICorProfilerCallback::Initialize](icorprofilercallback-initialize-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed568-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ed568-114">Requirements</span></span>  
 <span data-ttu-id="ed568-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed568-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed568-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ed568-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ed568-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ed568-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed568-118">**.NET Framework wersje:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed568-118">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed568-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ed568-119">See also</span></span>

- [<span data-ttu-id="ed568-120">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="ed568-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
