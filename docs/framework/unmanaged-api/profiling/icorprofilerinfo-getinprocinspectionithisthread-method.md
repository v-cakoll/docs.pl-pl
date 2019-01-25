---
title: ICorProfilerInfo::GetInprocInspectionIThisThread — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 019a85d6d58c99adb7c16be5cc3b31b029b0312d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513155"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a>ICorProfilerInfo::GetInprocInspectionIThisThread — Metoda
Pobiera obiekt, który może być odpytywany icordebugthread — interfejs. Ta metoda jest przestarzała w programie .NET Framework 2.0.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppicd`  
 [limit](/cpp/atl/iunknown) obiektu, który może być odpytywany dla `ICorDebugThread` interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego (CLR) debugowanie usług obsługiwane ograniczone w trakcie debugowania w .NET Framework w wersji 1.0. Debugowanie w trakcie włączone program profilujący do użycia inspekcji części interfejsie API debugowania. W wyniku opinie klientów debugowanie wewnątrzprocesowe został usunięty z programu .NET Framework w wersji 2.0 i zastąpione zestawem funkcji, która jest tworzone są profilowania API.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersja programu .NET framework:** 1.0  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
