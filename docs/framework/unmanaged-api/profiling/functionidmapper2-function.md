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
ms.openlocfilehash: 65c5d2d4f288d927d79c233374edfec54c0b77ae
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500653"
---
# <a name="functionidmapper2-function"></a>FunctionIDMapper2 — Funkcja
Powiadamia program profilujący, że dany identyfikator funkcji może zostać ponownie zmapowany na alternatywny identyfikator, który ma być używany w wywołaniach zwrotnych [FunctionEnter3](functionenter3-function.md), [FunctionLeave3](functionleave3-function.md)i [FunctionTailcall3](functiontailcall3-function.md), lub[FunctionEnter3WithInfo](functionenter3withinfo-function.md), [FunctionLeave3WithInfo](functionleave3withinfo-function.md)i [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) dla tej funkcji. `FunctionIDMapper2`umożliwia również profilerowi określenie, czy chce otrzymywać wywołania zwrotne dla tej funkcji.  
  
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

  \[w] identyfikator funkcji, która ma zostać ponownie zmapowana.

- `clientData`

  \[w] wskaźnik do danych, który jest używany do rozróżnienia między środowiskami uruchomieniowymi.

- `pbHookFunction`

  \[out] wskaźnik do wartości, która jest ustawiana przez profiler `true` , jeśli chce otrzymywać `FunctionEnter3` , `FunctionLeave3` , i, `FunctionTailcall3` lub, `FunctionEnter3WithInfo` i, i, i, `FunctionLeave3WithInfo` oraz `FunctionTailcall3WithInfo` wywołania zwrotne; w przeciwnym razie ta wartość jest ustawiana na `false` .

## <a name="return-value"></a>Wartość zwracana  
 Profiler zwraca wartość, którą aparat wykonywania używa jako alternatywnego identyfikatora funkcji. Zwracana wartość nie może mieć wartości null, chyba że `false` jest zwracana w `pbHookFunction` . W przeciwnym razie wartość zwracana null da nieprzewidywalne wyniki, w tym prawdopodobnie zatrzymanie procesu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda rozszerza funkcję [FunctionIDMapper](functionidmapper-function.md) z dodatkowym parametrem, który służy do przekazywania danych klienta. Dane klienta są używane do rozróżnienia między środowiskami uruchomieniowymi.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo:: SetFunctionIDMapper —](icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3:: Setfunctionidmapper2 —](icorprofilerinfo3-setfunctionidmapper2-method.md)
- [FunctionEnter3](functionenter3-function.md)
- [FunctionLeave3](functionleave3-function.md)
- [FunctionTailcall3](functiontailcall3-function.md)
- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [Profilowanie statycznych funkcji globalnych](profiling-global-static-functions.md)
