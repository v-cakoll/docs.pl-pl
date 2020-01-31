---
title: ICorProfilerInfo3::EnumJITedFunctions — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumJITedFunctions Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumJITedFunctions
helpviewer_keywords:
- ICorProfilerInfo3::EnumJITedFunctions method [.NET Framework profiling]
- EnumJITedFunctions method [.NET Framework profiling]
ms.assetid: e2847a36-f460-45e2-9b6c-b33b008f40d9
topic_type:
- apiref
ms.openlocfilehash: a22a0de9a20f32ce1c9818bbcf29222a4b331420
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862428"
---
# <a name="icorprofilerinfo3enumjitedfunctions-method"></a>ICorProfilerInfo3::EnumJITedFunctions — Metoda
Zwraca moduł wyliczający dla wszystkich funkcji, które zostały poprzednio skompilowane JIT.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
 określoną Wskaźnik do modułu wyliczającego [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda może nakładać się na wywołania zwrotne `JITCompilation`, takie jak Metoda [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) . Moduł wyliczający zwrócony przez tę metodę nie zawiera funkcji ładowanych z obrazów natywnych generowanych za pomocą programu Ngen. exe.  
  
> [!NOTE]
> Zwrócone Wyliczenie zawiera tylko wartość "0" dla wartości pola `COR_PRF_FUNCTION::reJitId`.  Jeśli wymagane są prawidłowe wartości `COR_PRF_FUNCTION::reJitId`, użyj metody [ICorProfilerInfo4:: EnumJITedFunctions2 —](icorprofilerinfo4-enumjitedfunctions2-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo3, interfejs](icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
