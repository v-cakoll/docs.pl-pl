---
title: FunctionTailcall — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
ms.openlocfilehash: bd03eccc923049c4a49062d18bd11659f3316e8a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866826"
---
# <a name="functiontailcall-function"></a>FunctionTailcall — Funkcja
Powiadamia profiler, że aktualnie wykonywana funkcja ma wykonać wywołanie tail do innej funkcji.  
  
> [!NOTE]
> Funkcja `FunctionTailcall` jest przestarzała w .NET Framework wersji 2,0. Będzie ona nadal działała, ale nastąpi spadek wydajności. Zamiast tego użyj funkcji [FunctionTailcall2](functiontailcall2-function.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>Parametry

- `funcID`

  \[in) identyfikator aktualnie wykonywanej funkcji, która ma na celu wykonanie wywołania tail.

## <a name="remarks"></a>Uwagi  
 Funkcja Target wywołania tail będzie używać bieżącej ramki stosu i zwróci się bezpośrednio do obiektu wywołującego funkcji, która wykonał wywołanie tail. Oznacza to, że wywołanie zwrotne [FunctionLeave —](functionleave-function.md) nie zostanie wygenerowane dla funkcji, która jest elementem docelowym wywołania tail.  
  
 Funkcja `FunctionTailcall` jest wywołaniem zwrotnym; należy zaimplementować go. Implementacja musi używać atrybutu klasy magazynu `__declspec`(`naked`).  
  
 Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.  
  
- We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).  
  
- Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.  
  
 Implementacja `FunctionTailcall` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych. Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych. Jeśli zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu, `FunctionTailcall` zwraca.  
  
 Ponadto funkcja `FunctionTailcall` nie może wywoływać w kodzie zarządzanym lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:** 1,1, 1,0  
  
## <a name="see-also"></a>Zobacz także

- [FunctionEnter2, funkcja](functionenter2-function.md)
- [FunctionLeave2, funkcja](functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2, metoda](icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)
