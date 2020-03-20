---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted Metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: e8b1a243b691d8d5eb364fd16821fd9156505c60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177049"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationStarted Metoda
[Obsługiwane w .NET Framework 4.7 i nowszych wersjach]  
  
Powiadamia profiler przy każdym uruchomieniu kompilacji JIT metody dynamicznej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,
     [in]  BOOL        fIsSafeToBlock,
     [in]  LPCBYTE     pILHeader,
     [in]  LONG        cbILHeader
);  
```  
  
## <a name="parameters"></a>Parametry  
[w]`functionId`  
Identyfikator funkcji w pamięci, dla której jest uruchomiona kompilacja JIT.

[w] `fIsSafeToBlock` aby wskazać, że blokowanie może spowodować, że środowisko uruchomieniowe czekać na wątek wywołujący do powrotu z tego wywołania zwrotnego; 
 `true` `false` , aby wskazać, że blokowanie nie wpłynie na działanie środowiska wykonawczego.  

[w] `pILHeader` Wskaźnik do pierwszego bajtu nagłówka IL metody.

[w] `cbILHeader` Liczba bajtów w nagłówku IL.

## <a name="remarks"></a>Uwagi  

To wywołanie zwrotne jest wyzwalane, gdy metoda dynamiczna jest skompilowana przez JIT. Obejmuje to różne wycinki IL i metody LCG. Jego celem jest dostarczenie pisarzom profilerów wystarczającej ilości informacji, aby zidentyfikować skompilowaną metodę dla użytkowników.

> [!NOTE]
> `functionId`wartości nie mogą być używane do rozpoznawania ich tokenów metadanych, ponieważ metody dynamiczne nie mają metadanych.

Wskaźnik `pILHeader` jest prawidłowy tylko podczas wywołania zwrotnego.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [DynamicMethodJITCompilationFinished, metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback8, interfejs](icorprofilercallback8-interface.md)
