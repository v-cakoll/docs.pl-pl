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
ms.openlocfilehash: c0daf772702ada9d426b3da6913fff0186e33564
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455654"
---
# <a name="icorprofilerfunctioncontrol-interface"></a>ICorProfilerFunctionControl — Interfejs
Udostępnia metody umożliwiające profilującego do komunikowania się z środowisko uruchomieniowe języka wspólnego (CLR), aby kontrolować sposób przy użyciu kompilatora JIT powinna generować kod ponowną kompilację określonej metody.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[SetCodegenFlags, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)|Określa jedną lub więcej flag z [cor_prf_codegen_flags —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md) funkcja ponownie kompilowana wyliczenie do kontroli generowania kodu dla just-in-time (JIT).|  
|[SetILFunctionBody, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilfunctionbody-method.md)|Zastępuje treść wspólnego języka pośredniego (CIL) metody.|  
|[SetILInstrumentedCodeMap, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md)|Ustawia mapę kodu dla funkcji określonej przy użyciu określonego wpisów map wspólnego języka pośredniego (CIL).|  
  
## <a name="remarks"></a>Uwagi  
 `ICorProfilerFunctionControl` Interfejs zawiera metody służące do sterowania generowanie kodu dla jednej funkcji ponownej kompilacji. Profiler uzyskuje wystąpienia tego interfejsu za pomocą [ICorProfilerCallback4::GetReJITParameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md) wywołania zwrotnego. Każde wystąpienie `ICorProfilerFunctionControl` steruje wszystkich wystąpień jednej funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo4, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [EnumJITedFunctions2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)
