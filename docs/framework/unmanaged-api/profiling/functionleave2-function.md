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
ms.openlocfilehash: a2a3d58e0631fceab96c32f9d86fef25973fed84
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500666"
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

  \[in] Identyfikator zwracanej funkcji.

- `clientData`

  \[w] ponownie mapowany identyfikator funkcji, który Profiler poprzednio określony przez funkcję [FunctionIDMapper](functionidmapper-function.md) .

- `func`

  \[in) `COR_PRF_FRAME_INFO` wartość, która wskazuje na informacje o ramce stosu.

  Profiler powinien być traktowany jako nieprzezroczysty uchwyt, który można przesłać z powrotem do aparatu wykonywania w metodzie [ICorProfilerInfo2:: GetFunctionInfo2 —](icorprofilerinfo2-getfunctioninfo2-method.md) .  
  
- `retvalRange`

  \[w] wskaźnik do struktury [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) , która określa lokalizację pamięci wartości zwracanej przez funkcję.

  Aby można było uzyskać dostęp do informacji zwracanej wartości, `COR_PRF_ENABLE_FUNCTION_RETVAL` należy ustawić flagę. Profiler może użyć metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) , aby ustawić flagi zdarzeń.

## <a name="remarks"></a>Uwagi  
 Wartości `func` `retvalRange` parametrów i są nieprawidłowe po `FunctionLeave2` powrocie funkcji, ponieważ wartości mogą ulec zmianie lub zostać zniszczone.  
  
 `FunctionLeave2`Funkcja jest wywołaniem zwrotnym, należy ją zaimplementować. Implementacja musi używać `__declspec` `naked` atrybutu klasy magazynu ().  
  
 Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.  
  
- We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).  
  
- Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.  
  
 Implementacja `FunctionLeave2` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych. Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych. W przypadku próby wyrzucania elementów bezużytecznych środowisko uruchomieniowe zostanie zablokowane do momentu `FunctionLeave2` powracania.  
  
 Ponadto `FunctionLeave2` Funkcja nie może wywołać kodu zarządzanego lub w jakikolwiek sposób może spowodować alokację pamięci zarządzanej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [FunctionEnter2, funkcja](functionenter2-function.md)
- [FunctionTailcall2, funkcja](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2, metoda](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)
