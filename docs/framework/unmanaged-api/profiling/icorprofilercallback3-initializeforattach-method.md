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
ms.openlocfilehash: 50fe7399896c35c1d6595b2d7214280e3009fab5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455804"
---
# <a name="icorprofilercallback3initializeforattach-method"></a>ICorProfilerCallback3::InitializeForAttach — Metoda
Wywoływane przez środowisko uruchomieniowe języka wspólnego (CLR), aby zapewnić możliwość zainicjować stanu po operacji dołączania profilera.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCorProfilerInfoUnk`  
 [in] Wskaźnik interfejsu dla `ICorProfilerInfo*` interfejsu.  
  
 `pvClientData`  
 [in] Wskaźnik do danych przekazany do [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metody w jego `pvClientData` parametru. Jeśli ten parametr ma wartość null, `cbClientData` będzie równa 0 (zero). Środowisko CLR zwalnia pamięć taka zwrócona z `InitializeForAttach`.  
  
 `cbClientData`  
 [in] Rozmiar w bajtach danych który `pvClientData` wskazuje.  
  
## <a name="remarks"></a>Uwagi  
 Wywołania CLR `InitializeForAttach` zapewnienie profilera możliwość wywołania zwrotne żądania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
