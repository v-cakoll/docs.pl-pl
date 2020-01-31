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
ms.openlocfilehash: 3903ebf1ad35bd7eb1ba49b4f1acda9024678423
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862207"
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
 Ta metoda może nakładać się na wywołania zwrotne `JITCompilation`, takie jak Metoda [ICorProfilerCallback:: JITCompilationStarted](icorprofilercallback-jitcompilationstarted-method.md) . Zwrócone Wyliczenie zawiera wartości pola `COR_PRF_FUNCTION::reJitId`. Metoda [ICorProfilerInfo3:: EnumJITedFunctions —](icorprofilerinfo3-enumjitedfunctions-method.md) , która zastępuje tę metodę, nie wylicza identyfikatorów, które ponownie skompilowano JIT, ponieważ pole `COR_PRF_FUNCTION::reJitId` ma zawsze wartość 0. Metoda `ICorProfilerInfo4::EnumJITedFunctions` wylicza identyfikatory ponownie skompilowane JIT, ponieważ pole `COR_PRF_FUNCTION::reJitId` jest ustawione prawidłowo. Należy pamiętać, że metoda [ICorProfilerInfo4:: EnumJITedFunctions2 —](icorprofilerinfo4-enumjitedfunctions2-method.md) może wyzwolić wyrzucanie elementów bezużytecznych, natomiast [Metoda ICorProfilerInfo3:: EnumJITedFunctions —](icorprofilerinfo3-enumjitedfunctions-method.md) nie będzie.  Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EnumJITedFunctions, metoda](icorprofilerinfo3-enumjitedfunctions-method.md)
- [ICorProfilerInfo4, interfejs](icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
