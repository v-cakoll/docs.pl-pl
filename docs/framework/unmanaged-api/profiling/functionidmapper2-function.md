---
title: FunctionIDMapper2 — Funkcja
ms.date: 03/30/2017
api_name:
- FunctionIDMapper2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionIDMapper2
helpviewer_keywords:
- FunctionIDMapper2 function [.NET Framework profiling]
ms.assetid: 466ad51b-8f0c-41d9-81f7-371aac3374cb
topic_type:
- apiref
ms.openlocfilehash: af0ef412395394bb660ae6ed64fb154caef41655
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866921"
---
# <a name="functionidmapper2-function"></a>FunctionIDMapper2 — Funkcja
Powiadamia program profilujący, że dany identyfikator funkcji może zostać ponownie zmapowany na alternatywny identyfikator, który ma być używany w wywołaniach zwrotnych [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)i [FunctionTailcall3](functiontailcall3-function.md), lub[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)i [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) dla tej funkcji. `FunctionIDMapper2` również umożliwia profilerowi określenie, czy chce otrzymywać wywołania zwrotne dla tej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametry

- `funcId`

  \[] identyfikator funkcji, która ma zostać ponownie zmapowana.

- `clientData`

  \[w] wskaźnik do danych, który jest używany do rozróżnienia między środowiskami uruchomieniowymi.

- `pbHookFunction`

  \[out] wskaźnik do wartości, która jest ustawiana przez profiler `true`, jeśli chce otrzymywać `FunctionEnter3`, `FunctionLeave3`i `FunctionTailcall3`, lub `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`i `FunctionTailcall3WithInfo` wywołania zwrotne; w przeciwnym razie ustawia tę wartość na `false`.

## <a name="return-value"></a>Wartość zwrócona  
 Profiler zwraca wartość, którą aparat wykonywania używa jako alternatywnego identyfikatora funkcji. Zwracana wartość nie może mieć wartości null, chyba że `false` jest zwracana w `pbHookFunction`. W przeciwnym razie wartość zwracana null da nieprzewidywalne wyniki, w tym prawdopodobnie zatrzymanie procesu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda rozszerza funkcję [FunctionIDMapper](functionidmapper-function.md) z dodatkowym parametrem, który służy do przekazywania danych klienta. Dane klienta są używane do rozróżnienia między środowiskami uruchomieniowymi.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo::SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3::SetFunctionIDMapper2](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)
