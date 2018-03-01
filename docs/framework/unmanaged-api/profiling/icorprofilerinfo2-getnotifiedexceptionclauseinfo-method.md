---
title: "ICorProfilerInfo2::GetNotifiedExceptionClauseInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 170aad39710f6e945495e9988921eddde5d9ba6b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="a6300-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="a6300-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>
<span data-ttu-id="a6300-103">Pobiera natywnego adresu i ramki informacje dla klauzuli wyjątek (`catch`/`finally`/`filter`) ma być uruchomiona albo został uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="a6300-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6300-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6300-104">Syntax</span></span>  
  
```  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6300-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6300-105">Parameters</span></span>  
 `pinfo`  
 <span data-ttu-id="a6300-106">[out] Wskaźnik do [cor_prf_ex_clause_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) strukturę, która opisuje bieżącego wystąpienia wyjątku w klauzuli i jego skojarzony ramki.</span><span class="sxs-lookup"><span data-stu-id="a6300-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6300-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6300-107">Remarks</span></span>  
 <span data-ttu-id="a6300-108">Po otrzymaniu powiadomienia wyjątek `GetNotifiedExceptionClauseInfo` może służyć do Pobierz natywnego adresu i ramki informacje dla klauzuli wyjątek (`catch`/`finally`/`filter`) to działać ([ ICorProfilerCallback::ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), lub [ICorProfilerCallback::ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)wywołania zwrotnego jest odbierany przez profiler) lub została uruchomiona ([ICorProfilerCallback::ExceptionCatcherLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), lub [ ICorProfilerCallback::ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) wywołania zwrotnego jest odbierany przez profiler).</span><span class="sxs-lookup"><span data-stu-id="a6300-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="a6300-109">To wywołanie może się w dowolnym momencie po jednej z powyższych wywołania zwrotne Enter aż do otrzymania pasującego wywołania zwrotnego pozostaw lub zagnieżdżone wyjątek w bieżącej klauzuli, w którym zdarza się, nie pozostaw powiadomienia dla tej klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a6300-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="a6300-110">Należy pamiętać, że nie jest możliwe zwrócony wyjątek anulować `filter` klauzuli wyjątek, dlatego zawsze powiadomienie pozostaw w takim przypadku.</span><span class="sxs-lookup"><span data-stu-id="a6300-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6300-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6300-111">Requirements</span></span>  
 <span data-ttu-id="a6300-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6300-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6300-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a6300-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6300-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6300-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6300-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6300-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6300-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6300-116">See Also</span></span>  
 [<span data-ttu-id="a6300-117">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6300-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="a6300-118">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a6300-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
