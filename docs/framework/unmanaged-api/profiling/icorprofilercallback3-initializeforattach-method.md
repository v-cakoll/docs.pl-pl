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
ms.openlocfilehash: d0219751987b1f2d78ee37a1553b323014c1ccfe
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865691"
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
 podczas Wskaźnik do danych przesłany do metody [IClrProfiling:: AttachProfiler —](iclrprofiling-attachprofiler-method.md) w parametrze `pvClientData`. Jeśli ten parametr ma wartość null, `cbClientData` będzie równa 0 (zero). Środowisko CLR zwalnia tę pamięć po powrocie z `InitializeForAttach`.  
  
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

- [ICorProfilerCallback, interfejs](icorprofilercallback-interface.md)
- [ICorProfilerInfo3, interfejs](icorprofilerinfo3-interface.md)
- [Interfejsy profilowania](profiling-interfaces.md)
- [Profilowanie](index.md)
