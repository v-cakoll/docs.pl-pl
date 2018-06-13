---
title: ICorProfilerInfo::EndInprocDebugging — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cbf7e2e7de54b065f25f3a1873d760ab5051cc91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452614"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a>ICorProfilerInfo::EndInprocDebugging — Metoda
Zamyka w trakcie sesji debugowania. Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwProfilerContext`  
 [in] Wartość, która identyfikuje sesji debugowania. Ta wartość musi być taka sama, jak została odebrana w [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) metody.  
  
## <a name="remarks"></a>Uwagi  
 Należy wywołać [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) i `EndInprocDebugging` w ramach tej samej metody wywołania zwrotnego.  
  
 Usług debugowania środowiska CLR obsługiwane ograniczony w trakcie debugowania w wersji systemu .NET Framework 1.0 i 1.1. Debugowanie w trakcie włączone profiler do używania kontroli części interfejsu API debugowania. Jednak ze względu na opinie klientów, w trakcie debugowania ma został usunięty z programu .NET Framework w wersji 2.0 i zastąpione zestaw funkcji, która jest zgodna z interfejsu API profilowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersja platformy .NET framework:** 1.0  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
