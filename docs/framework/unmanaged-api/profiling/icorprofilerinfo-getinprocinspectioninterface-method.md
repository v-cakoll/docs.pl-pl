---
title: ICorProfilerInfo::GetInprocInspectionInterface — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c4e2a094f018b4f77423b6dbfe990925632edf9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683862"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a>ICorProfilerInfo::GetInprocInspectionInterface — Metoda
Pobiera obiekt, który może być odpytywany dla interfejsu "ICorDebugProcess". Ta metoda jest przestarzała w programie .NET Framework 2.0.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppicd`  
 [limit](/cpp/atl/iunknown) obiektu, który może być odpytywany dla `ICorDebugProcess` interfejsu.  
  
## <a name="remarks"></a>Uwagi  
 Środowisko uruchomieniowe języka wspólnego (CLR) profilowanie API obsługiwane ograniczone w trakcie debugowania w .NET Framework w wersji 1.0. Debugowanie w trakcie włączone program profilujący do użycia inspekcji części interfejsie API debugowania. W wyniku opinie klientów debugowanie wewnątrzprocesowe został usunięty z programu .NET Framework w wersji 2.0 i zastąpione zestawem funkcji, która jest tworzone są profilowania API.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersja programu .NET framework:** 1.0  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
