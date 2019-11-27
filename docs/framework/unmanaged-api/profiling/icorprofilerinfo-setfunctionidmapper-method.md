---
title: ICorProfilerInfo::SetFunctionIDMapper — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetFunctionIDMapper
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetFunctionIDMapper
helpviewer_keywords:
- ICorProfilerInfo::SetFunctionIDMapper method [.NET Framework profiling]
- SetFunctionIDMapper method [.NET Framework profiling]
ms.assetid: 1a6e5dae-d366-4497-9c02-7b5b1f43f9ec
topic_type:
- apiref
ms.openlocfilehash: 4ba3c378b93e3ae1ef288c0edabfacfcfd7070d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438672"
---
# <a name="icorprofilerinfosetfunctionidmapper-method"></a>ICorProfilerInfo::SetFunctionIDMapper — Metoda
Określa funkcję zaimplementowaną przez profiler, która zostanie wywołana w celu mapowania wartości `FunctionID` na wartości alternatywne, które są przesyłane do punktów zaczepienia wejścia/wyjścia profilera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetFunctionIDMapper (  
    [in] FunctionIDMapper *pFunc);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFunc`  
 podczas Wskaźnik do implementacji [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) , który zostanie wywołany w celu mapowania wartości `FunctionID` na ich wartości alternatywne.  
  
## <a name="remarks"></a>Uwagi  
 Alternatywy dla wartości `FunctionID` zostaną przesłane do punktów zaczepienia wejścia/wyjścia funkcji profilera ([FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)i [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)), które są określone przez metodę [ICorProfilerInfo2:: SetEnterLeaveFunctionHooks2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) .  
  
 `FunctionIDMapper` można ustawić tylko raz i zaleca się jej ustawienie w [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) wywołania zwrotnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
