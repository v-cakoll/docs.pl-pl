---
title: ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationFinished
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dbe8d4f7050b93ffb34280be6d63367ef294ae8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206593"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationfinished-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationFinished Method
[Obsługiwane w programie .NET Framework 4.7 i nowszych wersjach]  
  
Powiadamia program profilujący, zawsze wtedy, gdy kompilacja JIT dynamicznej metody została ukończona.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DynamicMethodJITCompilationFinished(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        hrStatus,   
     [in]  BOOL        fIsSafeToBlock   
);  
```  
  
## <a name="parameters"></a>Parametry  
[in] `functionId`  
Identyfikator funkcji w pamięci, dla których JIT kompilacja jest uruchomiona.   

[in] `hrStatus`   
Wartość, która wskazuje, czy kompilacja JIT zakończyło się pomyślnie.

[in] `fIsSafeToBlock`   
`true` Aby wskazać, że blokuje może spowodować, że środowisko uruchomieniowe oczekiwania na wątek wywołujący, zostać zwrócony przez to wywołanie zwrotne; `false` do wskazania, że blokuje nie wpłynie na funkcjonowanie środowiska uruchomieniowego.  

## <a name="remarks"></a>Uwagi  

To wywołanie zwrotne jest zawsze wyzwalane, gdy kompilacja JIT dynamicznej metody zostało zakończone. Obejmuje to różne wycinki kodu IL i LCG metody. Jego celem jest zapewnienie autorzy profilera wystarczających informacji do identyfikowania metody skompilowanej dla użytkowników.

> [!NOTE]
> `functionId` Nie można użyć wartości do rozpoznawania tokenów metadanych, ponieważ metody dynamiczne mają Brak metadanych.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Zobacz także

- [DynamicMethodJITCompilationStarted, metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8, interfejs](icorprofilercallback8-interface.md)
