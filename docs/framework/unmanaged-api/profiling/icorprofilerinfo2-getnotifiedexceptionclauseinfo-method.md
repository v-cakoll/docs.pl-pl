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
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a>ICorProfilerInfo2::GetNotifiedExceptionClauseInfo — Metoda
Pobiera natywne informacje dotyczące adresów i ramki dla klauzuli wyjątek (`catch`/`finally`/`filter`) który ma być uruchomiona lub została uruchomiona.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a>Parametry  
 `pinfo`  
 [out] Wskaźnik do [cor_prf_ex_clause_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) strukturę, która opisuje bieżące wystąpienie wyjątku w klauzuli i jego skojarzone ramki.  
  
## <a name="remarks"></a>Uwagi  
 Po odebraniu powiadomienia wyjątku `GetNotifiedExceptionClauseInfo` pozwala uzyskać natywnych informacje dotyczące adresów i ramki dla klauzuli wyjątek (`catch`/`finally`/`filter`) czyli można uruchomić ([ Icorprofilercallback::exceptioncatcherenter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [icorprofilercallback::exceptionunwindfinallyenter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), lub [icorprofilercallback::exceptionsearchfilterenter —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)wywołania zwrotnego jest odbierany przez profiler) lub po prostu zostały uruchomione ([icorprofilercallback::exceptioncatcherleave —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [icorprofilercallback::exceptionunwindfinallyleave —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), lub [ Icorprofilercallback::exceptionsearchfilterleave —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) wywołania zwrotnego jest odbierany przez profiler).  
  
 To wywołanie może się w dowolnym momencie po jednej z powyższych wywołania zwrotne Enter aż do dopasowywania wywołania zwrotnego pozostaw została odebrana lub zagnieżdżone wyjątek jest zgłaszany w klauzuli bieżącej, w którym nie jest brak powiadomienia pozostaw dla tej klauzuli. Należy pamiętać, że nie jest możliwe zgłoszony wyjątek anulować `filter` klauzuli wyjątek, dzięki czemu zawsze jest powiadomienie o urlop w takiej sytuacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
