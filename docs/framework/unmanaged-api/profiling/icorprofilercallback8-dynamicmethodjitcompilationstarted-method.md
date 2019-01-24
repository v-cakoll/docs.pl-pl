---
title: ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8.DynamicMethodJITCompilationStarted
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 062229245e3ae209de0eda65d4be59e286f4da7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517750"
---
# <a name="icorprofilercallback8dynamicmethodjitcompilationstarted-method"></a>ICorProfilerCallback8::DynamicMethodJITCompilationStarted Method
[Obsługiwane w programie .NET Framework 4.7 i nowszych wersjach]  
  
Powiadamia program profilujący, zawsze wtedy, gdy rozpoczęto kompilację JIT metodę dynamiczną.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DynamicMethodJITCompilationStarted(  
     [in]  FunctionID  functionId,   
     [in]  BOOL        fIsSafeToBlock,   
     [in]  LPCBYTE     pILHeader,   
     [in]  LONG        cbILHeader   
);  
```  
  
#### <a name="parameters"></a>Parametry  
[in] `functionId`  
Identyfikator funkcji w pamięci, dla których JIT kompilacja jest uruchomiona.   

[in] `fIsSafeToBlock`   
`true` Aby wskazać, że blokuje może spowodować, że środowisko uruchomieniowe oczekiwania na wątek wywołujący, zostać zwrócony przez to wywołanie zwrotne; `false` do wskazania, że blokuje nie wpłynie na funkcjonowanie środowiska uruchomieniowego.  

[in] `pILHeader`    
Wskaźnik do pierwszego bajtu nagłówek IL metody.   

[in] `cbILHeader`    
Liczba bajtów w nagłówku IL. 

## <a name="remarks"></a>Uwagi  

To wywołanie zwrotne jest wywoływane zawsze wtedy, gdy metoda dynamiczna kompilowanego dokładnie na czas. Obejmuje to różne wycinki kodu IL i LCG metody. Jego celem jest zapewnienie autorzy profilera wystarczających informacji do identyfikowania metody skompilowanej dla użytkowników.

> [!NOTE]
> `functionId` Nie można użyć wartości do rozpoznawania tokenów metadanych, ponieważ metody dynamiczne mają Brak metadanych.

`pILHeader` Wskaźnik jest prawidłowy tylko podczas wywołania zwrotnego.

## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
  
## <a name="see-also"></a>Zobacz także
- [DynamicMethodJITCompilationFinished, metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
- [ICorProfilerCallback8, interfejs](icorprofilercallback8-interface.md)
