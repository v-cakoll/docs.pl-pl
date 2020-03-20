---
title: ICorProfilerCallback8::DynamicMethodJITKomunikacjaKończa metoda
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c2e9489654a0fe5fa65ec638ed0f991a6c01415a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175112"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::DynamicMethodJITKomunikacjaKończa metoda
[Obsługiwane w .NET Framework 4.7 i nowszych wersjach]  
  
Powiadamia profiler po zakończeniu kompilacji JIT metody dynamicznej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,
     [in]  BOOL        hrStatus,
     [in]  BOOL        fIsSafeToBlock
);  
```  
  
## <a name="parameters"></a>Parametry  
[w]`functionId`  
Identyfikator funkcji w pamięci, dla której jest uruchomiona kompilacja JIT.

[w] `hrStatus` Wartość, która wskazuje, czy kompilacja JIT zakończyła się pomyślnie.

[w] `fIsSafeToBlock` aby wskazać, że blokowanie może spowodować, że środowisko uruchomieniowe czekać na wątek wywołujący do powrotu z tego wywołania zwrotnego; 
 `true` `false` , aby wskazać, że blokowanie nie wpłynie na działanie środowiska wykonawczego.  

## <a name="remarks"></a>Uwagi  

To wywołanie zwrotne jest wyzwalane po zakończeniu kompilacji JIT metody dynamicznej. Obejmuje to różne wycinki IL i metody LCG. Jego celem jest dostarczenie pisarzom profilerów wystarczającej ilości informacji, aby zidentyfikować skompilowaną metodę dla użytkowników.

> [!NOTE]
> `functionId`wartości nie mogą być używane do rozpoznawania ich tokenów metadanych, ponieważ metody dynamiczne nie mają metadanych.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Zobacz też

- [DynamicMethodJITCompilationStarted, metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8, interfejs](icorprofilercallback8-interface.md)
