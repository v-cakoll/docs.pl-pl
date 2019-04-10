---
title: ICorProfilerFunctionControl — Interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl
helpviewer_keywords:
- ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: 4e3d3141-4662-4166-8f05-bc857c1b4216
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 721ee27522b316a561e2f64a322c225cb85a44c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211442"
---
# <a name="icorprofilerfunctioncontrol-interface"></a>ICorProfilerFunctionControl — Interfejs
Udostępnia metody, które umożliwiają programowi profilującemu kodu komunikacji plików wykonywalnych języka wspólnego (CLR) do kontrolowania, jak kompilator JIT ma generować kod ponownej kompilacji określonej metody.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[SetCodegenFlags, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|Ustawia flagi co najmniej jeden z [cor_prf_codegen_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) wyliczenia do sterowania generowanie kodu dla just-in-time (JIT) ponownie kompilowana funkcji.|  
|[SetILFunctionBody, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|Zastępuje treść wspólnego języka pośredniego (CIL) metody.|  
|[SetILInstrumentedCodeMap, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|Ustawia mapę kodu dla określonej funkcji przy użyciu określonego wpisy mapy wspólny język pośredni (CIL).|  
  
## <a name="remarks"></a>Uwagi  
 `ICorProfilerFunctionControl` Interfejs zapewnia metody umożliwiają sterowanie generowanie kodu dla jednej funkcji ponownej kompilacji. Program profilujący uzyskuje wystąpienie ten interfejs, za pośrednictwem [icorprofilercallback4::getrejitparameters —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) wywołania zwrotnego. Każde wystąpienie `ICorProfilerFunctionControl` kontroluje wszystkie wystąpienia elementu jednej funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo4 — Interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumJITedFunctions2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)
