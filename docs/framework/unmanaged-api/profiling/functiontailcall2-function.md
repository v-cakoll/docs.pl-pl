---
title: FunctionTailcall2 — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
ms.openlocfilehash: 60276327617ae24e9bdcebf958613c21d3808429
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175190"
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 — Funkcja
Powiadamia profiler, że funkcja aktualnie wykonywania ma zamiar wykonać wywołanie ogona do innej funkcji i zawiera informacje o ramce stosu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,
    [in] UINT_PTR           clientData,
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
## <a name="parameters"></a>Parametry

- `funcId`

  \[w] Identyfikator aktualnie wykonywanej funkcji, która ma na celu wywołanie ogona.

- `clientData`

  \[w] Reemapped identyfikator funkcji, który profiler wcześniej określone za pośrednictwem [FunctionIDMapper](functionidmapper-function.md), funkcji aktualnie wykonywania, który ma zamiar dokonać wywołania ogona.
  
- `func`

  \[w] `COR_PRF_FRAME_INFO` Wartość, która wskazuje informacje o ramce stosu.

  Profiler należy traktować to jako nieprzezroczysty dojście, które mogą być przekazywane z powrotem do aparatu wykonywania w [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) metody.

## <a name="remarks"></a>Uwagi  
 Funkcja docelowa wywołania ogona użyje bieżącej ramki stosu i powróci bezpośrednio do obiektu wywołującego funkcji, która wykonała wywołanie ogona. Oznacza to, że [FunctionLeave2](functionleave2-function.md) wywołania zwrotnego nie zostaną wystawione dla funkcji, która jest celem wywołania ogona.  
  
 Wartość parametru `func` nie jest prawidłowa po powrocie `FunctionTailcall2` funkcji, ponieważ wartość może ulec zmianie lub zostać zniszczona.  
  
 Funkcja `FunctionTailcall2` jest wywołaniem zwrotnym; należy go zaimplementować. Implementacja musi `__declspec`używać`naked`atrybutu () klasy magazynu.  
  
 Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.  
  
- Przy wprowadzaniu należy zapisać wszystkie używane rejestry, w tym rejestry w jednostce zmiennoprzecinkowej (FPU).  
  
- Po wyjściu należy przywrócić stosu przez popping off wszystkie parametry, które zostały wypchnięte przez jego wywołującego.  
  
 Implementacja `FunctionTailcall2` nie należy blokować, ponieważ opóźni wyrzucanie elementów bezużytecznych. Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznym dla wyrzucania elementów bezużytecznych. Jeśli zostanie podjęta próba wyrzucania elementów `FunctionTailcall2` bezużytecznych, środowisko uruchomieniowe zostanie zablokowane, dopóki nie zwróci.  
  
 Ponadto `FunctionTailcall2` funkcja nie może wywoływać kodu zarządzanego lub w jakikolwiek sposób powodować alokacji pamięci zarządzanej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [FunctionEnter2, funkcja](functionenter2-function.md)
- [FunctionLeave2 — Funkcja](functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2, metoda](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)
