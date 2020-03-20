---
title: FunctionEnter2 — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: 9aeb7a294beb10f9c2968e6161c72fdc362c4991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177062"
---
# <a name="functionenter2-function"></a>FunctionEnter2 — Funkcja
Powiadamia profiler, że formant jest przekazywany do funkcji i zawiera informacje o ramce stosu i argumenty funkcji. Ta funkcja zastępuje [functionenter](functionenter-function.md) funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,
    [in]  UINT_PTR                         clientData,
    [in]  COR_PRF_FRAME_INFO               func,
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a>Parametry

- `funcId`

  \[w] Identyfikator funkcji, do której formant jest przekazywany.

- `clientData`

  \[w] Semmapowany identyfikator funkcji, który profiler wcześniej określony za pomocą [functionidmapper](functionidmapper-function.md) funkcji.
  
- `func`

  \[w] `COR_PRF_FRAME_INFO` Wartość, która wskazuje informacje o ramce stosu.
  
  Profiler należy traktować to jako nieprzezroczysty dojście, które mogą być przekazywane z powrotem do aparatu wykonywania w [ICorProfilerInfo2::GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md) metody.  
  
- `argumentInfo`

  \[w] Wskaźnik do [struktury COR_PRF_FUNCTION_ARGUMENT_INFO,](cor-prf-function-argument-info-structure.md) który określa lokalizacje w pamięci argumentów funkcji.

  Aby uzyskać dostęp do `COR_PRF_ENABLE_FUNCTION_ARGS` informacji o argudze, należy ustawić flagę. Profiler można użyć [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) metody, aby ustawić flagi zdarzeń.

## <a name="remarks"></a>Uwagi  
 Wartości `func` i `argumentInfo` parametry nie są prawidłowe po zwraca `FunctionEnter2` funkcję, ponieważ wartości mogą ulec zmianie lub zostać zniszczone.  
  
 Funkcja `FunctionEnter2` jest wywołaniem zwrotnym; należy go zaimplementować. Implementacja musi `__declspec`używać`naked`atrybutu () klasy magazynu.  
  
 Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.  
  
- Przy wprowadzaniu należy zapisać wszystkie używane rejestry, w tym rejestry w jednostce zmiennoprzecinkowej (FPU).  
  
- Po wyjściu należy przywrócić stosu przez popping off wszystkie parametry, które zostały wypchnięte przez jego wywołującego.  
  
 Implementacja `FunctionEnter2` nie należy blokować, ponieważ opóźni wyrzucanie elementów bezużytecznych. Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie być w stanie przyjaznym dla wyrzucania elementów bezużytecznych. Jeśli zostanie podjęta próba wyrzucania elementów `FunctionEnter2` bezużytecznych, środowisko uruchomieniowe zostanie zablokowane, dopóki nie zwróci.  
  
 Ponadto `FunctionEnter2` funkcja nie może wywoływać kodu zarządzanego lub w jakikolwiek sposób powodować alokacji pamięci zarządzanej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [FunctionLeave2 — Funkcja](functionleave2-function.md)
- [FunctionTailcall2, funkcja](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2, metoda](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)
