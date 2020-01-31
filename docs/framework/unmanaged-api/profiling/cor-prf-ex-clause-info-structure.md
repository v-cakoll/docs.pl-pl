---
title: COR_PRF_EX_CLAUSE_INFO — Struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_EX_CLAUSE_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_EX_CLAUSE_INFO
helpviewer_keywords:
- COR_PRF_EX_CLAUSE_INFO structure [.NET Framework profiling]
ms.assetid: 7d0d6fb7-bc9d-40f0-8163-c0d162eaba7d
topic_type:
- apiref
ms.openlocfilehash: fb6d2e5fc21047fea0928137f983c553f9bb2bbd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867285"
---
# <a name="cor_prf_ex_clause_info-structure"></a>COR_PRF_EX_CLAUSE_INFO — Struktura
Przechowuje informacje o konkretnym wystąpieniu klauzuli wyjątku i skojarzonej z nią ramce.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct COR_PRF_EX_CLAUSE_INFO {  
    COR_PRF_CLAUSE_TYPE clauseType;  
    UINT_PTR programCounter;  
    UINT_PTR framePointer;  
    UINT_PTR shadowStackPointer;  
} COR_PRF_EX_CLAUSE_INFO;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`clauseType`|Wartość wyliczenia [COR_PRF_CLAUSE_TYPE](cor-prf-clause-type-enumeration.md) , która określa typ klauzuli wyjątku, która właśnie została wprowadzona lub po lewej stronie.|  
|`programCounter`|Natywny punkt wejścia procedury obsługi klauzuli — na przykład zawartość rejestru EIP klasy x86.|  
|`framePointer`|Wskaźnik do ramki logicznej programu obsługi klauzuli — na przykład zawartość rejestru x86 EBP.|  
|`shadowStackPointer`|Wskaźnik do stosu cienia. Ta wartość jest zawartością rejestru zestawu Winsock i ma zastosowanie tylko do IA64.|  
  
## <a name="remarks"></a>Uwagi  
 Po otrzymaniu powiadomienia o wyjątku [ICorProfilerInfo2:: GetNotifiedExceptionClauseInfo —](icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md) może służyć do uzyskiwania informacji o adresie i ramce natywnej dla klauzuli wyjątku (`catch`/`finally`/Filter), która ma zostać uruchomiona lub właśnie została uruchomiona.  
  
 Wykonanie klauzuli wyjątku obejmuje te wywołania zwrotne z aparatu plików wykonywalnych języka wspólnego (CLR):  
  
- [ICorProfilerCallback::ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md)  
  
- [ICorProfilerCallback::ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md)  
  
- [ICorProfilerCallback::ExceptionSearchFilterEnter](icorprofilercallback-exceptionsearchfilterenter-method.md)  
  
- [ICorProfilerCallback::ExceptionCatcherLeave](icorprofilercallback-exceptioncatcherleave-method.md)  
  
- [ICorProfilerCallback:: ExceptionUnwindFinallyLeave —](icorprofilercallback-exceptionunwindfinallyleave-method.md)  
  
- [ICorProfilerCallback::ExceptionSearchFilterLeave](icorprofilercallback-exceptionsearchfilterleave-method.md)  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Profiling — struktury](profiling-structures.md)
