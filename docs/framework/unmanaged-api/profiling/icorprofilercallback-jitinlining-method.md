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
ms.openlocfilehash: 3e13b17fb03530730a78f6889309f1993419574b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866218"
---
# <a name="icorprofilercallbackjitinlining-method"></a><span data-ttu-id="0a966-102">ICorProfilerCallback::JITInlining — Metoda</span><span class="sxs-lookup"><span data-stu-id="0a966-102">ICorProfilerCallback::JITInlining Method</span></span>
<span data-ttu-id="0a966-103">Powiadamia profiler, że kompilator just in Time (JIT) ma wstawić funkcję w wierszu z inną funkcją.</span><span class="sxs-lookup"><span data-stu-id="0a966-103">Notifies the profiler that the just-in-time (JIT) compiler is about to insert a function in line with another function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a966-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0a966-104">Syntax</span></span>  
  
```cpp  
HRESULT JITInlining(  
    [in]  FunctionID callerId,  
    [in]  FunctionID calleeId,  
    [out] BOOL      *pfShouldInline);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a966-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a966-105">Parameters</span></span>  
 `callerId`  
 <span data-ttu-id="0a966-106">podczas Identyfikator funkcji, w której zostanie wstawiona funkcja `calleeId`.</span><span class="sxs-lookup"><span data-stu-id="0a966-106">[in] The ID of the function into which the `calleeId` function will be inserted.</span></span>  
  
 `calleeId`  
 <span data-ttu-id="0a966-107">podczas Identyfikator funkcji, która ma zostać wstawiona.</span><span class="sxs-lookup"><span data-stu-id="0a966-107">[in] The ID of the function to be inserted.</span></span>  
  
 `pfShouldInline`  
 <span data-ttu-id="0a966-108">[out] `true`, aby zezwolić na wstawianie; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="0a966-108">[out] `true` to allow the insertion to occur; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a966-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0a966-109">Remarks</span></span>  
 <span data-ttu-id="0a966-110">Profiler może ustawić `pfShouldInline` na `false`, aby uniemożliwić Wstawianie funkcji `calleeId` do funkcji `callerId`.</span><span class="sxs-lookup"><span data-stu-id="0a966-110">The profiler can set `pfShouldInline` to `false` to prevent the `calleeId` function from being inserted into the `callerId` function.</span></span> <span data-ttu-id="0a966-111">Dodatkowo profiler może globalnie wyłączyć wstawianie wbudowane przy użyciu wartości COR_PRF_DISABLE_INLINING [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) Enumeration.</span><span class="sxs-lookup"><span data-stu-id="0a966-111">Also, the profiler can globally disable inline insertion by using the COR_PRF_DISABLE_INLINING value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="0a966-112">Wbudowane funkcje nie zgłaszają zdarzeń do wprowadzenia lub opuszczenia.</span><span class="sxs-lookup"><span data-stu-id="0a966-112">Functions inserted inline do not raise events for entering or leaving.</span></span> <span data-ttu-id="0a966-113">W związku z tym profiler musi ustawić `pfShouldInline`, aby `false` w celu wygenerowania dokładnej wykres wywołań.</span><span class="sxs-lookup"><span data-stu-id="0a966-113">Therefore, the profiler must set `pfShouldInline` to `false` in order to produce an accurate callgraph.</span></span> <span data-ttu-id="0a966-114">Ustawienie `pfShouldInline` na `false` będzie miało wpływ na wydajność, ponieważ Wstawianie wbudowane zwykle zwiększa szybkość i zmniejsza liczbę oddzielnych zdarzeń kompilacji JIT dla włożonej metody.</span><span class="sxs-lookup"><span data-stu-id="0a966-114">Setting `pfShouldInline` to `false` will affect performance, because inline insertion typically increases speed and reduces the number of separate JIT compilation events for the inserted method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a966-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0a966-115">Requirements</span></span>  
 <span data-ttu-id="0a966-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a966-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a966-117">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0a966-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0a966-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0a966-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a966-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a966-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a966-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a966-120">See also</span></span>

- [<span data-ttu-id="0a966-121">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="0a966-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
