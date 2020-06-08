---
title: ICorProfilerFunctionControl::SetCodegenFlags — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
ms.openlocfilehash: a3d5527fc34ad7292974c005179e9d9cad210c94
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503123"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>ICorProfilerFunctionControl::SetCodegenFlags — Metoda
Ustawia co najmniej jedną flagę z wyliczenia [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) , aby kontrolować generowanie kodu dla funkcji rekompilowanej just-in-Time (JIT).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 podczas Co najmniej jedna flaga z wyliczenia [COR_PRF_CODEGEN_FLAGS](cor-prf-codegen-flags-enumeration.md) .  
  
## <a name="remarks"></a>Uwagi  
 Profiler uzyskuje wystąpienie tego interfejsu za pomocą wywołania zwrotnego [ICorProfilerCallback4:: GetReJITParameters —](icorprofilercallback4-getrejitparameters-method.md) . `SetCodegenFlags`umożliwia profilerowi sterowanie generowaniem kodu dla ponownie skompilowanej funkcji. Podobnie jak w przypadku wszystkich innych parametrów ponownej kompilacji JIT, flagi generowania kodu stosują się do wszystkich wystąpień funkcji.  
  
 Kompilator JIT traktuje te flagi kompilacji wraz z innymi flagami określonymi przez inne źródła podczas kompilowania funkcji.  Inne źródła obejmują debuger, flagi globalne ustawiane przez profiler przy uruchamianiu przy użyciu metody [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) (z wartościami `COR_PRF_DISABLE_INLINING` i `COR_PRF_DISABLE_OPTIMIZATIONS` ), a także wywołania zwrotnego [ICorProfilerCallback:: JITInlining —](icorprofilercallback-jitinlining-method.md) .  Kompilator JIT daje pierwszeństwo dla źródła, które żąda najmniejszej ilości optymalizacji.  Na przykład, jeśli Profiler określa `COR_PRF_DISABLE_INLINING` podczas uruchamiania, ale nie określono `COR_PRF_CODEGEN_DISABLE_INLINING` w wywołaniu zwrotnym [ICorProfilerFunctionControl:: SetCodegenFlags —](icorprofilerfunctioncontrol-setcodegenflags-method.md) , nakreślenie jest nadal wyłączone.  Podobnie, jeśli Profiler nie jest określony `COR_PRF_CODEGEN_DISABLE_INLINING` w `SetCodegenFlags` , a następnie wyłącza funkcję tworzenia konspektu przy użyciu wywołania zwrotnego [ICorProfilerCallback:: JITInlining —](icorprofilercallback-jitinlining-method.md) , wykreślenie jest wyłączone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerFunctionControl — Interfejs](icorprofilerfunctioncontrol-interface.md)
