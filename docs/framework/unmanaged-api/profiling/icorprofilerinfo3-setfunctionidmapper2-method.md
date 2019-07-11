---
title: ICorProfilerInfo3::SetFunctionIDMapper2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetFunctionIDMapper2 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetFunctionIDMapper2
helpviewer_keywords:
- SetFunctionIDMapper2 method [.NET Framework profiling]
- ICorProfilerInfo3::SetFunctionIDMapper2 method [.NET Framework profiling]
ms.assetid: 8cdb1188-952a-4ba8-9f05-bfebc18cdd29
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 186e85bffbc94b4dd9cdf7add010a0af5b383804
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780894"
---
# <a name="icorprofilerinfo3setfunctionidmapper2-method"></a>ICorProfilerInfo3::SetFunctionIDMapper2 — Metoda
Określa funkcję implementowany przez program profilujący zostanie wywołana w celu mapowania `FunctionID` wartości alternatywne wartości, które są przekazywane do programu profilującego funkcji punktów zaczepienia wejścia/wyjścia. Ta metoda jest rozszerzeniem [icorprofilerinfo::setfunctionidmapper —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) metody z parametrem dodatkowe dane profilowania może używać w celu rozróżniać wśród modułów wykonawczych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetFunctionIDMapper2(  
       [in] FunctionIDMapper2 *pFunc,  
       [in] void *clientData);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFunc`  
 [in] Wskaźnik do [functionidmapper2 —](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) implementację, która zostanie wywołana w celu mapowania `FunctionID` wartości w celu ich alternatywne wartości.  
  
 `clientData`  
 [in] Wskaźnik, który jest przekazywany do każdej [functionidmapper2 —](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md) wywołania funkcji przez bieżącego środowiska uruchomieniowego. Profiler można użyć tych informacji aby rozróżniać wśród modułów wykonawczych.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Alternatywy dla wartości FunctionID zostaną przekazane do programu profilującego funkcja wejścia/wyjścia w punkty zaczepienia ([FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), i [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) ; lub [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), i [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)) które są określone przez [ Setenterleavefunctionhooks3 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md) lub [setenterleavefunctionhooks3withinfo —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) metody.  
  
 `FunctionIDMapper2` Metody można ustawić tylko raz; zalecamy ustawienie [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)
- [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
