---
title: ICorProfilerCallback::AssemblyLoadFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 174e71fca8c59dbd4842d0fc0b84bb9a3d7b10df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763047"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a>ICorProfilerCallback::AssemblyLoadFinished — Metoda
Powiadamia program profilujący, że zespół zakończył ładowanie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a>Parametry  
 `assemblyId`  
 [in] Określa zestaw, który został załadowany.  
  
 `hrStatus`  
 [in] Wartość HRESULT, która wskazuje, czy zestaw zakończone pomyślnie ładowania.  
  
## <a name="remarks"></a>Uwagi  
 Wartość `assemblyId` jest nieprawidłowa dla żądania informacje do momentu `AssemblyLoadFinished` metoda jest wywoływana.  
  
 Niektóre części ładowania zestawu może kontynuować po `AssemblyLoadFinished` wywołania zwrotnego. Błąd HRESULT w `hrStatus` wskazuje błąd. Jednak sukcesów wartość HRESULT w `hrStatus` tylko wskazuje, czy zakończyła się pomyślnie w pierwszej części ładowania zestawu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
