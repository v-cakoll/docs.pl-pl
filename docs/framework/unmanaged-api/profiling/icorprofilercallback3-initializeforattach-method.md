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
ms.openlocfilehash: 047516574595f9ffcd61360f51823da73a2f9733
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439515"
---
# <a name="icorprofilercallback3initializeforattach-method"></a>ICorProfilerCallback3::InitializeForAttach — Metoda
Wywoływane przez środowisko uruchomieniowe języka wspólnego (CLR), aby Profiler mógł zainicjować swój stan po operacji dołączania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCorProfilerInfoUnk`  
 podczas Wskaźnik interfejsu dla interfejsu `ICorProfilerInfo*`.  
  
 `pvClientData`  
 podczas Wskaźnik do danych przesłany do metody [IClrProfiling:: AttachProfiler —](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) w parametrze `pvClientData`. Jeśli ten parametr ma wartość null, `cbClientData` będzie równa 0 (zero). Środowisko CLR zwalnia tę pamięć po powrocie z `InitializeForAttach`.  
  
 `cbClientData`  
 podczas Rozmiar, w bajtach, danych, do których wskazuje `pvClientData`.  
  
## <a name="remarks"></a>Uwagi  
 Wywołania CLR `InitializeForAttach`, aby dać profilerowi możliwość żądania wywołań zwrotnych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorProfilerCallback, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerInfo3, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
