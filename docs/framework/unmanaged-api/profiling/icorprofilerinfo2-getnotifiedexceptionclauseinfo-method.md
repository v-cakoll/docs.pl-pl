---
title: "ICorProfilerInfo2::GetNotifiedExceptionClauseInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetNotifiedExceptionClauseInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
- GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
ms.assetid: f9594a7e-cb0c-4c48-accb-29f762aa0c21
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3e5ad1742d6f714b53b109bb99fc288bccd4a3bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a>ICorProfilerInfo2::GetNotifiedExceptionClauseInfo — Metoda
Pobiera natywnego adresu i ramki informacje dla klauzuli wyjątek (`catch`/`finally`/`filter`) ma być uruchomiona albo został uruchomiony.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pinfo`  
 [out] Wskaźnik do [cor_prf_ex_clause_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) strukturę, która opisuje bieżącego wystąpienia wyjątku w klauzuli i jego skojarzony ramki.  
  
## <a name="remarks"></a>Uwagi  
 Po otrzymaniu powiadomienia wyjątek `GetNotifiedExceptionClauseInfo` może służyć do Pobierz natywnego adresu i ramki informacje dla klauzuli wyjątek (`catch`/`finally`/`filter`) to działać ([ ICorProfilerCallback::ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), lub [ICorProfilerCallback::ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)wywołania zwrotnego jest odbierany przez profiler) lub została uruchomiona ([ICorProfilerCallback::ExceptionCatcherLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), lub [ ICorProfilerCallback::ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) wywołania zwrotnego jest odbierany przez profiler).  
  
 To wywołanie może się w dowolnym momencie po jednej z powyższych wywołania zwrotne Enter aż do otrzymania pasującego wywołania zwrotnego pozostaw lub zagnieżdżone wyjątek w bieżącej klauzuli, w którym zdarza się, nie pozostaw powiadomienia dla tej klauzuli. Należy pamiętać, że nie jest możliwe zwrócony wyjątek anulować `filter` klauzuli wyjątek, dlatego zawsze powiadomienie pozostaw w takim przypadku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
