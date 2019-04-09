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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92bc16091abd3e21ebd226fb13dd47b55b0c9cc4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166832"
---
# <a name="icorprofilerinfo4enumjitedfunctions2-method"></a>ICorProfilerInfo4::EnumJITedFunctions2 — Metoda
Zwraca moduł wyliczający dla wszystkich funkcji, które wcześniej były skompilowane JIT i ponownie skompilowana JIT. Ta metoda zastępuje [icorprofilerinfo3::enumjitedfunctions —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) metody, która nie wyliczyć identyfikatory ponownie skompilowana JIT.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumJITedFunctions([out] ICorProfilerFunctionEnum** ppEnum);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEnum`  
 [out] Wskaźnik do [icorprofilerfunctionenum —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) modułu wyliczającego.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda może pokrywać się z `JITCompilation` wywołań zwrotnych, takie jak [icorprofilercallback::jitcompilationstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md) metody. Zwrócone wyliczenia zawiera wartości `COR_PRF_FUNCTION::reJitId` pola. [Icorprofilerinfo3::enumjitedfunctions —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) metody, która zastępuje tę metodę, wyliczyć identyfikatory ponownie skompilowana JIT, ponieważ `COR_PRF_FUNCTION::reJitId` pole jest zawsze równa 0. `ICorProfilerInfo4::EnumJITedFunctions` Metoda wyliczyć identyfikatory ponownie skompilowana JIT, ponieważ `COR_PRF_FUNCTION::reJitId` pole jest ustawione prawidłowo. Należy pamiętać, że [icorprofilerinfo4::enumjitedfunctions2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md) metody, które mogą wyzwalać wyrzucania elementów bezużytecznych, natomiast [icorprofilerinfo3::enumjitedfunctions — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) nie będzie.  Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [EnumJITedFunctions, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
- [ICorProfilerInfo4 — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
