---
title: ICorProfilerInfo4::EnumJITedFunctions2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumJITedFunctions2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumJITedFunctions2
helpviewer_keywords:
- EnumJITedFunctions2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::EnumJITedFunctions2 method [.NET Framework profiling]
ms.assetid: 40e9a1be-9bd2-4fad-9921-34a84b61c1e3
topic_type:
- apiref
ms.openlocfilehash: 2c4a89d5f96ef572518f25bf58a0005454f8e3f0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496132"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a>ICorProfilerInfo4::EnumJITedFunctions2 — Metoda
Zwraca moduł wyliczający dla wszystkich funkcji, które były poprzednio skompilowane JIT i ponownie skompilowane w trybie JIT. Ta metoda zastępuje metodę [ICorProfilerInfo3:: EnumJITedFunctions —](icorprofilerinfo3-enumjitedfunctions-method.md) , która nie WYLICZA identyfikatorów JIT-ponownie kompilowanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
 określoną Wskaźnik do modułu wyliczającego [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) .  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda może nakładać się na `JITCompilation` wywołania zwrotne, takie jak Metoda [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) . Zwrócone Wyliczenie zawiera wartości dla `COR_PRF_FUNCTION::reJitId` pola. Metoda [ICorProfilerInfo3:: EnumJITedFunctions —](icorprofilerinfo3-enumjitedfunctions-method.md) , która zastępuje tę metodę, nie wylicza identyfikatorów, które ponownie skompilowano JIT, ponieważ `COR_PRF_FUNCTION::reJitId` pole jest zawsze ustawione na 0. `ICorProfilerInfo4::EnumJITedFunctions`Metoda wylicza identyfikatory ponownie skompilowane JIT, ponieważ `COR_PRF_FUNCTION::reJitId` pole jest ustawione prawidłowo. Należy pamiętać, że metoda [ICorProfilerInfo4:: EnumJITedFunctions2 —](icorprofilerinfo4-enumjitedfunctions2-method.md) może wyzwolić wyrzucanie elementów bezużytecznych, natomiast [Metoda ICorProfilerInfo3:: EnumJITedFunctions —](icorprofilerinfo3-enumjitedfunctions-method.md) nie będzie.  Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EnumJITedFunctions, metoda](icorprofilerinfo3-enumjitedfunctions-method.md)
- [ICorProfilerInfo4 — Interfejs](icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
