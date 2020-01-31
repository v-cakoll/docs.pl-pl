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
ms.openlocfilehash: 6cd35c180b8a322b3402b050c6d6840073010b1f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866986"
---
# <a name="functionenter2-function"></a>FunctionEnter2 — Funkcja
Powiadamia profiler, że sterowanie jest przesyłane do funkcji i zawiera informacje na temat ramki stosu i argumentów funkcji. Ta funkcja zastępuje funkcję [FunctionEnter —](functionenter-function.md) .  
  
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

  \[in) identyfikator funkcji, do której jest przenoszona kontrola.

- `clientData`

  \[w] ponownie mapowany identyfikator funkcji, który został wcześniej określony przez profiler przy użyciu funkcji [FunctionIDMapper](functionidmapper-function.md) .
  
- `func`

  \[w] `COR_PRF_FRAME_INFO` wartość, która wskazuje na informacje o ramce stosu.
  
  Profiler powinien być traktowany jako nieprzezroczysty uchwyt, który można przesłać z powrotem do aparatu wykonywania w metodzie [ICorProfilerInfo2:: GetFunctionInfo2 —](icorprofilerinfo2-getfunctioninfo2-method.md) .  
  
- `argumentInfo`

  \[w] wskaźnik do struktury [COR_PRF_FUNCTION_ARGUMENT_INFO](cor-prf-function-argument-info-structure.md) , która określa lokalizacje w pamięci argumentów funkcji.

  Aby można było uzyskać dostęp do informacji o argumencie, należy ustawić flagę `COR_PRF_ENABLE_FUNCTION_ARGS`. Profiler może użyć metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) , aby ustawić flagi zdarzeń.

## <a name="remarks"></a>Uwagi  
 Wartości parametrów `func` i `argumentInfo` są nieprawidłowe po powrocie funkcji `FunctionEnter2`, ponieważ wartości mogą ulec zmianie lub zostać zniszczone.  
  
 Funkcja `FunctionEnter2` jest wywołaniem zwrotnym; należy zaimplementować go. Implementacja musi używać atrybutu klasy magazynu `__declspec`(`naked`).  
  
 Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.  
  
- We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).  
  
- Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.  
  
 Implementacja `FunctionEnter2` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych. Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych. Jeśli zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu, `FunctionEnter2` zwraca.  
  
 Ponadto funkcja `FunctionEnter2` nie może wywoływać w kodzie zarządzanym lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [FunctionLeave2, funkcja](functionleave2-function.md)
- [FunctionTailcall2, funkcja](functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2, metoda](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)
