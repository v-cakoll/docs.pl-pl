---
title: FunctionLeave2 — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionLeave2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave2
helpviewer_keywords:
- FunctionLeave2 function [.NET Framework profiling]
ms.assetid: 8cdac941-8b94-4497-b874-4e571785f3fe
topic_type:
- apiref
ms.openlocfilehash: 0b1ecd1266528f8a08ef114de2f111dd0f71ca8b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866934"
---
# <a name="functionleave2-function"></a>FunctionLeave2 — Funkcja
Powiadamia program profilujący, że funkcja ma zwrócić do obiektu wywołującego i zawiera informacje na temat ramki stosu i wartości zwracanej przez funkcję.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void __stdcall FunctionLeave2 (  
    [in]  FunctionID                        funcId,  
    [in]  UINT_PTR                          clientData,  
    [in]  COR_PRF_FRAME_INFO                func,  
    [in]  COR_PRF_FUNCTION_ARGUMENT_RANGE  *retvalRange  
);  
```  
  
## <a name="parameters"></a>Parametry

- `funcId`

  \[in) identyfikator funkcji, która zwraca.

- `clientData`

  \[w] ponownie mapowany identyfikator funkcji, który Profiler wcześniej określono za pośrednictwem funkcji [FunctionIDMapper](functionidmapper-function.md) .

- `func`

  \[w] `COR_PRF_FRAME_INFO` wartość, która wskazuje na informacje o ramce stosu.

  Profiler powinien być traktowany jako nieprzezroczysty uchwyt, który można przesłać z powrotem do aparatu wykonywania w metodzie [ICorProfilerInfo2:: GetFunctionInfo2 —](icorprofilerinfo2-getfunctioninfo2-method.md) .  
  
- `retvalRange`

  \[w] wskaźnik do struktury [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) , która określa lokalizację pamięci wartości zwracanej przez funkcję.

  Aby można było uzyskać dostęp do informacji o wartości zwracanej, należy ustawić flagę `COR_PRF_ENABLE_FUNCTION_RETVAL`. Profiler może użyć metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) , aby ustawić flagi zdarzeń.

## <a name="remarks"></a>Uwagi  
 Wartości parametrów `func` i `retvalRange` są nieprawidłowe po powrocie funkcji `FunctionLeave2`, ponieważ wartości mogą ulec zmianie lub zostać zniszczone.  
  
 Funkcja `FunctionLeave2` jest wywołaniem zwrotnym; należy zaimplementować go. Implementacja musi używać atrybutu klasy magazynu `__declspec`(`naked`).  
  
 Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.  
  
- We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).  
  
- Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.  
  
 Implementacja `FunctionLeave2` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych. Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych. Jeśli zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu, `FunctionLeave2` zwraca.  
  
 Ponadto funkcja `FunctionLeave2` nie może wywoływać w kodzie zarządzanym lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [FunctionEnter2, funkcja](functionenter2-function.md)
- [FunctionTailcall2, funkcja](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2, metoda](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)
