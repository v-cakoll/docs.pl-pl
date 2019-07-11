---
title: ICorProfilerInfo::BeginInprocDebugging — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 618be7482616ea155798973d02a90f32d46164db
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780266"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a>ICorProfilerInfo::BeginInprocDebugging — Metoda
Inicjuje obsługę debugowania w procesie. Ta metoda jest przestarzała w programie .NET Framework 2.0.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a>Parametry  
 `fThisThreadOnly`  
 [in] Ustaw tę wartość na `true` zainicjować obsługę debugowania tylko bieżącego wątku; ustaw ją na `false` zainicjować obsługę debugowania dla wszystkich wątków.  
  
 `pdwProfilerContext`  
 [out] Wskaźnik do zwrócona wartość, która identyfikuje sesji debugowania.  
  
## <a name="remarks"></a>Uwagi  
 Usług debugowania środowiska CLR obsługiwane, debugowanie wewnątrzprocesowe ograniczone w .NET Framework w wersji 1.0 i 1.1. Debugowanie w trakcie włączone program profilujący do użycia inspekcji części interfejsie API debugowania. Jednak ze względu na opinie klientów, debugowanie wewnątrzprocesowe ma zostały usunięte z programu .NET Framework w wersji 2.0 i zastąpione zestawem funkcji, która jest tworzone są profilowania API.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersja programu .NET framework:** 1.0  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerInfo, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
