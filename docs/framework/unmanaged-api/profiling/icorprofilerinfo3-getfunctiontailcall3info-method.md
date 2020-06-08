---
title: ICorProfilerInfo3::GetFunctionTailcall3Info — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
ms.openlocfilehash: e4d0d9ed07c707e51e5833483b71079f2c330505
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496532"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a>ICorProfilerInfo3::GetFunctionTailcall3Info — Metoda
Udostępnia ramkę stosu funkcji, która jest raportowana do profilera przez funkcję [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md) . Tę metodę można wywołać tylko w trakcie `FunctionTailcall3WithInfo` wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetFunctionTailcall3Info(
            [in]  FunctionID functionId,
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 podczas `FunctionID`Funkcja, która zwraca.  
  
 `eltInfo`  
 podczas Nieprzezroczyste dojście, które reprezentuje informacje o danej klatce stosu. Profiler powinien zapewnić taki sam `eltInfo` , który został przekazany do profilera przez `FunctionTailcall3WithInfo` funkcję.  
  
 `pFrameInfo`  
 określoną Nieprzezroczyste dojście reprezentujące ogólne informacje dotyczące danej ramki stosu. To dojście jest prawidłowe tylko `FunctionTailcall3WithInfo` w przypadku wywołania zwrotnego, w którym Profiler nazywa `GetFunctionTailcall3Info` metodę.  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [FunctionEnter3WithInfo](functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3, interfejs](icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
