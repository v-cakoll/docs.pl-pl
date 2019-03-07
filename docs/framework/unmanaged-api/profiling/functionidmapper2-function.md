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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71c7dcc5d337e7585e380981cc2ec4b5192e5151
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481732"
---
# <a name="functionidmapper2-function"></a>FunctionIDMapper2 — Funkcja
Powiadamia program profilujący, że identyfikator danej funkcji może być ponownie mapowany do alternatywnego Identyfikatora do użycia w [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), i [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), lub[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), i [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) wywołań zwrotnych tej funkcji. `FunctionIDMapper2` Umożliwia także profilującemu wskazanie, czy chce odbierać wywołania zwrotne do tej funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
UINT_PTR __stdcall FunctionIDMapper2 (  
    [in]  FunctionID  funcId,  
    [in]  void * clientData,  
    [out] BOOL       *pbHookFunction  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `funcId`  
 [in] Identyfikator funkcji ma być ponownie mapowany.  
  
 `clientData`  
 [in] Wskaźnik do danych, który służy do rozróżniać wśród modułów wykonawczych.  
  
 `pbHookFunction`  
 [out] Wskaźnik do wartości, która ustawia program profilujący `true` jeśli chce otrzymać `FunctionEnter3`, `FunctionLeave3`, i `FunctionTailcall3`, lub `FunctionEnter3WithInfo`, `FunctionLeave3WithInfo`, i `FunctionTailcall3WithInfo` wywołań zwrotnych; w przeciwnym wypadku ustawia tę wartość, aby `false`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Program profilujący zwraca wartość, której używa silnik wykonawczy jako identyfikatora alternatywnej funkcji. Zwracana wartość nie może mieć wartości null Jeśli nie `false` jest zwracany w `pbHookFunction`. W przeciwnym razie zwracana wartość null produkuje nieoczekiwanych rezultatów, w tym ewentualnie powstrzymanie procesu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest rozszerzeniem [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) funkcję o dodatkowy parametr, który jest używany do przekazania danych klienta. Dane klienta są używane do rozróżniać wśród modułów wykonawczych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3::SetFunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)
- [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [Profilowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
