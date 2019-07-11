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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a659e139040174a66043283ed4633d9c9d223ce8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774036"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="d09da-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="d09da-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>
<span data-ttu-id="d09da-103">Pobiera natywne informacje dotyczące adresów i ramki dla klauzuli wyjątek (`catch`/`finally`/`filter`) który ma być uruchomiona lub została uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="d09da-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d09da-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d09da-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d09da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d09da-105">Parameters</span></span>  
 `pinfo`  
 <span data-ttu-id="d09da-106">[out] Wskaźnik do [cor_prf_ex_clause_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) strukturę, która opisuje bieżące wystąpienie wyjątku w klauzuli i jego skojarzone ramki.</span><span class="sxs-lookup"><span data-stu-id="d09da-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d09da-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d09da-107">Remarks</span></span>  
 <span data-ttu-id="d09da-108">Po odebraniu powiadomienia wyjątku `GetNotifiedExceptionClauseInfo` pozwala uzyskać natywnych informacje dotyczące adresów i ramki dla klauzuli wyjątek (`catch`/`finally`/`filter`) czyli można uruchomić ([ Icorprofilercallback::exceptioncatcherenter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [icorprofilercallback::exceptionunwindfinallyenter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), lub [icorprofilercallback::exceptionsearchfilterenter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)wywołania zwrotnego jest odbierany przez profiler) lub po prostu zostały uruchomione ([icorprofilercallback::exceptioncatcherleave —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [icorprofilercallback::exceptionunwindfinallyleave —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), lub [ Icorprofilercallback::exceptionsearchfilterleave —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) wywołania zwrotnego jest odbierany przez profiler).</span><span class="sxs-lookup"><span data-stu-id="d09da-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="d09da-109">To wywołanie może się w dowolnym momencie po jednej z powyższych wywołania zwrotne Enter aż do dopasowywania wywołania zwrotnego pozostaw została odebrana lub zagnieżdżone wyjątek jest zgłaszany w klauzuli bieżącej, w którym nie jest brak powiadomienia pozostaw dla tej klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d09da-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="d09da-110">Należy pamiętać, że nie jest możliwe zgłoszony wyjątek anulować `filter` klauzuli wyjątek, dzięki czemu zawsze jest powiadomienie o urlop w takiej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="d09da-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d09da-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d09da-111">Requirements</span></span>  
 <span data-ttu-id="d09da-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d09da-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d09da-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d09da-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d09da-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d09da-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d09da-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d09da-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d09da-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d09da-116">See also</span></span>

- [<span data-ttu-id="d09da-117">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="d09da-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="d09da-118">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d09da-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
