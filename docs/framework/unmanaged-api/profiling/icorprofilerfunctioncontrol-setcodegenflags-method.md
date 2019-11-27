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
ms.openlocfilehash: 88c9f552b73af69ea4e1f64b75ed74ea762dcdfb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429941"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>ICorProfilerFunctionControl::SetCodegenFlags — Metoda
Ustawia co najmniej jedną flagę z wyliczenia [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) , aby kontrolować generowanie kodu dla funkcji rekompilowanej just-in-Time (JIT).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 podczas Co najmniej jedna flaga z wyliczenia [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) .  
  
## <a name="remarks"></a>Uwagi  
 Profiler uzyskuje wystąpienie tego interfejsu za pomocą wywołania zwrotnego [ICorProfilerCallback4:: GetReJITParameters —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) . `SetCodegenFlags` pozwala profilerowi kontrolować generowanie kodu dla ponownie skompilowanej funkcji. Podobnie jak w przypadku wszystkich innych parametrów ponownej kompilacji JIT, flagi generowania kodu stosują się do wszystkich wystąpień funkcji.  
  
 Kompilator JIT traktuje te flagi kompilacji wraz z innymi flagami określonymi przez inne źródła podczas kompilowania funkcji.  Inne źródła obejmują debuger, flagi globalne ustawiane przez profiler przy uruchamianiu przy użyciu metody [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) (z wartościami `COR_PRF_DISABLE_INLINING` i `COR_PRF_DISABLE_OPTIMIZATIONS`) i [ICorProfilerCallback:: JITInlining —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) wywołania zwrotnego.  Kompilator JIT daje pierwszeństwo dla źródła, które żąda najmniejszej ilości optymalizacji.  Na przykład, jeśli Profiler określa `COR_PRF_DISABLE_INLINING` przy uruchamianiu, ale nie określa `COR_PRF_CODEGEN_DISABLE_INLINING` w wywołaniu zwrotnym [ICorProfilerFunctionControl:: SetCodegenFlags —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) , nakreślenie jest nadal wyłączone.  Podobnie, jeśli Profiler nie określa `COR_PRF_CODEGEN_DISABLE_INLINING` w `SetCodegenFlags`, ale następnie wyłącza funkcję tworzenia konspektu przy użyciu wywołania zwrotnego [ICorProfilerCallback:: JITInlining —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) , wykreślanie jest wyłączone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerFunctionControl, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
