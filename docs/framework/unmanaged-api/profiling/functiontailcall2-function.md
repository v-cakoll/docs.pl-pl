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
ms.openlocfilehash: cb7e21e0c6aad5ebb328ae5d1a993716f96e8d47
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500575"
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 — Funkcja
Powiadamia profiler, że aktualnie wykonywana funkcja ma wykonać wywołanie tail do innej funkcji i zawiera informacje na temat ramki stosu.  
  
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

  \[in) identyfikator aktualnie wykonywanej funkcji, która ma na celu wykonanie wywołania tail.

- `clientData`

  \[w] identyfikator funkcji ponownie mapowanej, który został wcześniej określony przez program [FunctionIDMapper](functionidmapper-function.md), aktualnie wykonywanej funkcji, która ma na celu wykonanie wywołania tail.
  
- `func`

  \[in) `COR_PRF_FRAME_INFO` wartość, która wskazuje na informacje o ramce stosu.

  Profiler powinien być traktowany jako nieprzezroczysty uchwyt, który można przesłać z powrotem do aparatu wykonywania w metodzie [ICorProfilerInfo2:: GetFunctionInfo2 —](icorprofilerinfo2-getfunctioninfo2-method.md) .

## <a name="remarks"></a>Uwagi  
 Funkcja Target wywołania tail będzie używać bieżącej ramki stosu i zwróci się bezpośrednio do obiektu wywołującego funkcji, która wykonał wywołanie tail. Oznacza to, że wywołanie zwrotne [FunctionLeave2](functionleave2-function.md) nie zostanie wygenerowane dla funkcji, która jest elementem docelowym wywołania tail.  
  
 Wartość `func` parametru jest nieprawidłowa po `FunctionTailcall2` powrocie funkcji, ponieważ wartość może ulec zmianie lub zostać zniszczona.  
  
 `FunctionTailcall2`Funkcja jest wywołaniem zwrotnym, należy ją zaimplementować. Implementacja musi używać `__declspec` `naked` atrybutu klasy magazynu ().  
  
 Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.  
  
- We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).  
  
- Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.  
  
 Implementacja `FunctionTailcall2` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych. Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych. W przypadku próby wyrzucania elementów bezużytecznych środowisko uruchomieniowe zostanie zablokowane do momentu `FunctionTailcall2` powracania.  
  
 Ponadto `FunctionTailcall2` Funkcja nie może wywołać kodu zarządzanego lub w jakikolwiek sposób może spowodować alokację pamięci zarządzanej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [FunctionEnter2, funkcja](functionenter2-function.md)
- [FunctionLeave2 — Funkcja](functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2, metoda](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)
