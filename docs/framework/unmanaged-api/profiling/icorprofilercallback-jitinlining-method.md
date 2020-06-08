---
title: ICorProfilerCallback::JITInlining — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.JITInlining
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::JITInlining
helpviewer_keywords:
- JITInlining method [.NET Framework profiling]
- ICorProfilerCallback::JITInlining method [.NET Framework profiling]
ms.assetid: c2f45801-dd38-4b78-b6b7-64397dc73f83
topic_type:
- apiref
ms.openlocfilehash: 13ce44c9c7a04b870278bc8926dd9fe5daf10bc3
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500016"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="3f34f-102">ICorProfilerCallback::JITInlining — Metoda</span><span class="sxs-lookup"><span data-stu-id="3f34f-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="3f34f-103">Powiadamia profiler, że kompilator just in Time (JIT) ma wstawić funkcję w wierszu z inną funkcją.</span><span class="sxs-lookup"><span data-stu-id="3f34f-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f34f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f34f-104">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f34f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3f34f-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="3f34f-106">podczas Identyfikator funkcji, do której `calleeId` zostanie wstawiona funkcja.</span><span class="sxs-lookup"><span data-stu-id="3f34f-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="3f34f-107">podczas Identyfikator funkcji, która ma zostać wstawiona.</span><span class="sxs-lookup"><span data-stu-id="3f34f-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="3f34f-108">[out] `true` , aby zezwolić na wstawianie; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="3f34f-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3f34f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3f34f-109">Remarks</span></span>  
 <span data-ttu-id="3f34f-110">Profiler można ustawić tak, aby `pfShouldInline` `false` uniemożliwić `calleeId` Wstawianie funkcji do `callerId` funkcji.</span><span class="sxs-lookup"><span data-stu-id="3f34f-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="3f34f-111">Dodatkowo profiler może globalnie wyłączyć wstawianie wbudowane przy użyciu wartości COR_PRF_DISABLE_INLINING [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) Enumeration.</span><span class="sxs-lookup"><span data-stu-id="3f34f-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="3f34f-112">Wbudowane funkcje nie zgłaszają zdarzeń do wprowadzenia lub opuszczenia.</span><span class="sxs-lookup"><span data-stu-id="3f34f-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="3f34f-113">W związku z tym profiler musi mieć ustawioną wartość `pfShouldInline` `false` w celu wygenerowania dokładnej wykres wywołań.</span><span class="sxs-lookup"><span data-stu-id="3f34f-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="3f34f-114">Ustawienie `pfShouldInline` ma `false` wpływ na wydajność, ponieważ Wstawianie wbudowane zwykle zwiększa szybkość i zmniejsza liczbę oddzielnych zdarzeń kompilacji JIT dla włożonej metody.</span><span class="sxs-lookup"><span data-stu-id="3f34f-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f34f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f34f-115">Requirements</span></span>  
 <span data-ttu-id="3f34f-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f34f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f34f-117">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3f34f-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3f34f-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3f34f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f34f-119">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f34f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f34f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3f34f-120">See also</span></span>

- [<span data-ttu-id="3f34f-121">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3f34f-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
