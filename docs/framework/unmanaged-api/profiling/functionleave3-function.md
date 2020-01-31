---
title: FunctionLeave3 — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionLeave3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionLeave3
helpviewer_keywords:
- FunctionLeave3 function [.NET Framework profiling]
ms.assetid: 5d798088-7992-48a0-ae55-d2a7ee31913f
topic_type:
- apiref
ms.openlocfilehash: 32d86f19e9c50694c7d113195e6967645b710666
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866872"
---
# <a name="functionleave3-function"></a>FunctionLeave3 — Funkcja
Powiadamia profiler, że formant jest zwracany przez funkcję.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
void __stdcall FunctionLeave3(FunctionOrRemappedID functionOrRemappedID);  
```  
  
## <a name="parameters"></a>Parametry  

- `functionOrRemappedID`

  \[in) identyfikator funkcji, z której jest zwracany formant.
  
## <a name="remarks"></a>Uwagi  
 Funkcja wywołania zwrotnego `FunctionLeave3` powiadamia profiler w miarę wywoływania funkcji, ale nie obsługuje inspekcji wartości zwracanej. Użyj [metody ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3 —](icorprofilerinfo3-setenterleavefunctionhooks3-method.md) , aby zarejestrować implementację tej funkcji.  
  
 Funkcja `FunctionLeave3` jest wywołaniem zwrotnym; należy zaimplementować go. Implementacja musi używać atrybutu klasy magazynu `__declspec(naked)`.  
  
 Aparat wykonywania nie zapisuje żadnych rejestrów przed wywołaniem tej funkcji.  
  
- We wpisie należy zapisać wszystkie używane rejestry, w tym te w jednostce zmiennoprzecinkowej (FPU).  
  
- Po zakończeniu należy przywrócić stos, usuwanie wyłączyć wszystkie parametry, które zostały wypchnięte przez jego obiekt wywołujący.  
  
 Implementacja `FunctionLeave3` nie powinna być blokowana, ponieważ spowoduje opóźnienie wyrzucania elementów bezużytecznych. Implementacja nie powinna podejmować próby wyrzucania elementów bezużytecznych, ponieważ stos może nie znajdować się w stanie przyjaznym do wyrzucania elementów bezużytecznych. Jeśli zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu, `FunctionLeave3` zwraca.  
  
 Funkcja `FunctionLeave3` nie może wywoływać kodu zarządzanego lub spowodować alokacji pamięci zarządzanej w jakikolwiek sposób.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [FunctionEnter3](functionenter3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functiontailcall3-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [SetEnterLeaveFunctionHooks3](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [SetEnterLeaveFunctionHooks3WithInfo](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [Setfunctionidmapper2 —](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)
