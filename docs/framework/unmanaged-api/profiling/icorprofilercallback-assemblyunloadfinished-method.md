---
title: ICorProfilerCallback::AssemblyUnloadFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d757a0455992bc82ead922a5fbf4c71f11a9085
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450872"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a>ICorProfilerCallback::AssemblyUnloadFinished — Metoda
Powiadamia profilera, że zestaw został usunięty z pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a>Parametry  
 `assemblyId`  
 [in] Określa zestaw, który jest zwalniany.  
  
 `hrStatus`  
 [in] HRESULT, która wskazuje, czy zestaw został pomyślnie usunięty z pamięci.  
  
## <a name="remarks"></a>Uwagi  
 Wartość `assemblyId` jest nieprawidłowa dla żądania informacji po [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) zwraca metody.  
  
 Niektórych części zwalnianie zestaw może kontynuować po `AssemblyUnloadFinished` wywołania zwrotnego. Błąd HRESULT w `hrStatus` oznacza błąd. Jednak Powodzenie HRESULT w `hrStatus` tylko wskazuje, że pierwsza część zwalnianie zestawu zakończyła się pomyślnie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
