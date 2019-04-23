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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12f91bdd264135eb0ff3a48e15611cf5a0e3c064
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59104445"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>ICorProfilerFunctionControl::SetCodegenFlags — Metoda
Ustawia flagi co najmniej jeden z [cor_prf_codegen_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) wyliczenia do sterowania generowanie kodu dla just-in-time (JIT) ponownie kompilowana funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a>Parametry  
 `flags`  
 [in] Flagi co najmniej jeden z [cor_prf_codegen_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) wyliczenia.  
  
## <a name="remarks"></a>Uwagi  
 Program profilujący uzyskuje wystąpienie ten interfejs, za pośrednictwem [icorprofilercallback4::getrejitparameters —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) wywołania zwrotnego. `SetCodegenFlags` Umożliwia profiler kontrolować generowanie kodu dla funkcji ponownej kompilacji. Podobnie jak w przypadku wszystkich innych JIT ponownej kompilacji parametrów flagi generowania kodu mają zastosowanie do wszystkich wystąpień funkcji.  
  
 Kompilator JIT uwzględnia te flagi kompilacji oraz inne flagi, określony przez inne źródła, podczas kompilowania funkcji.  Inne źródła dołączyć debuger, flagi globalnej ustawione przez profiler przy uruchamianiu przez przy użyciu [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) — metoda (z wartościami `COR_PRF_DISABLE_INLINING` i `COR_PRF_DISABLE_OPTIMIZATIONS`) i programu profilującego [ Icorprofilercallback::jitinlining —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) wywołania zwrotnego.  Kompilator JIT daje pierwszeństwo źródła, który żąda najmniejszą ilością optymalizacji.  Na przykład, jeśli program profilujący Określa `COR_PRF_DISABLE_INLINING` podczas uruchamiania, ale nie określa `COR_PRF_CODEGEN_DISABLE_INLINING` w [icorprofilerfunctioncontrol::setcodegenflags —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md) wywołanie zwrotne, wbudowanie nadal jest wyłączona.  Podobnie jeśli program profilujący nie określa `COR_PRF_CODEGEN_DISABLE_INLINING` w `SetCodegenFlags`, ale następnie wyłącza wbudowanie przy użyciu [icorprofilercallback::jitinlining —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) wywołanie zwrotne, wbudowanie jest wyłączona.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerFunctionControl, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
