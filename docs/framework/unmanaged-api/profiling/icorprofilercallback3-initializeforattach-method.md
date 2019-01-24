---
title: ICorProfilerCallback3::InitializeForAttach — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.InitializeForAttach Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ebdd76655124922008667898e38f873ad93598e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555599"
---
# <a name="icorprofilercallback3initializeforattach-method"></a>ICorProfilerCallback3::InitializeForAttach — Metoda
Metoda wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR), aby dać profilerowi możliwość zainicjowania jego stanu po operacji dołączania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCorProfilerInfoUnk`  
 [in] Wskaźnik interfejsu do `ICorProfilerInfo*` interfejsu.  
  
 `pvClientData`  
 [in] Wskaźnik do danych jest przekazywany do [iclrprofiling::attachprofiler —](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in Class metoda jego `pvClientData` parametru. Jeśli ten parametr ma wartość null, `cbClientData` będzie mieć wartość 0 (zero). Środowisko CLR zwalnia ta pamięć zwrócona z `InitializeForAttach`.  
  
 `cbClientData`  
 [in] Rozmiar w bajtach, danych, który `pvClientData` wskazuje.  
  
## <a name="remarks"></a>Uwagi  
 CLR wywołuje `InitializeForAttach` aby dać profilerowi możliwość na wywołania zwrotne żądania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
