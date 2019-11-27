---
title: ICorProfilerInfo2::GetNotifiedExceptionClauseInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetNotifiedExceptionClauseInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
- GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
ms.assetid: f9594a7e-cb0c-4c48-accb-29f762aa0c21
topic_type:
- apiref
ms.openlocfilehash: 52ad124638a1c1ec7d39fa41b9163f3ab50ffe70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433065"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="f2b0a-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="f2b0a-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>
<span data-ttu-id="f2b0a-103">Pobiera natywne informacje o adresie i ramce dla klauzuli wyjątku (`catch`/`finally`/`filter`), które mają zostać uruchomione lub właśnie uruchomione.</span><span class="sxs-lookup"><span data-stu-id="f2b0a-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2b0a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2b0a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2b0a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2b0a-105">Parameters</span></span>  
 `pinfo`  
 <span data-ttu-id="f2b0a-106">określoną Wskaźnik do struktury [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) , który opisuje bieżące wystąpienie klauzuli wyjątku i skojarzoną z nią ramkę.</span><span class="sxs-lookup"><span data-stu-id="f2b0a-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2b0a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2b0a-107">Remarks</span></span>  
 <span data-ttu-id="f2b0a-108">Po otrzymaniu powiadomienia o wyjątku `GetNotifiedExceptionClauseInfo` może zostać użyty do uzyskania natywnego adresu i informacji o ramce dla klauzuli wyjątku (`catch`/`finally`/`filter`), która ma być uruchamiana ([ICorProfilerCallback:: ExceptionCatcherEnter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback:: ExceptionUnwindFinallyEnter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)lub [ICorProfilerCallback:: ExceptionSearchFilterEnter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md) wywołanie zwrotne jest odbierane przez Profiler) lub właśnie zostało uruchomione ([ICorProfilerCallback:: ExceptionCatcherLeave — ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback:: ExceptionUnwindFinallyLeave —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)lub [ICorProfilerCallback:: ExceptionSearchFilterLeave —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) wywołanie zwrotne jest odbierane przez Profiler).</span><span class="sxs-lookup"><span data-stu-id="f2b0a-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="f2b0a-109">To wywołanie można wykonać w dowolnym momencie po odebraniu jednego z wywołań zwrotnych powyżej do momentu otrzymania zgodnego wywołania zwrotnego urlopu lub wyjątek zagnieżdżony w bieżącej klauzuli, w takim przypadku nie ma powiadomienia o opuszczeniu dla tej klauzuli.</span><span class="sxs-lookup"><span data-stu-id="f2b0a-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="f2b0a-110">Należy zauważyć, że nie jest możliwe dla zgłoszonego wyjątku, aby pominąć klauzulę wyjątku `filter`, więc w takim przypadku zawsze istnieje powiadomienie o pozostawieniu.</span><span class="sxs-lookup"><span data-stu-id="f2b0a-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2b0a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f2b0a-111">Requirements</span></span>  
 <span data-ttu-id="f2b0a-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2b0a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2b0a-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f2b0a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2b0a-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f2b0a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2b0a-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2b0a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b0a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2b0a-116">See also</span></span>

- [<span data-ttu-id="f2b0a-117">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="f2b0a-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="f2b0a-118">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="f2b0a-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
