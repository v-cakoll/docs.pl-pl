---
title: ICorProfilerCallback3::ProfilerAttachComplete — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: 8168f6f1079ec34b9fb53a485da0f32175446719
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865431"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a>ICorProfilerCallback3::ProfilerAttachComplete — Metoda
Wywoływane przez środowisko uruchomieniowe języka wspólnego (CLR), aby wskazać, że profiler może teraz wywołać metody przechwytywania [ICorProfilerInfo3:: EnumJITedFunctions —](icorprofilerinfo3-enumjitedfunctions-method.md) i [ICorProfilerInfo3:: EnumModules —](icorprofilerinfo3-enummodules-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie zwrotne `ProfilerAttachComplete` jest wydawane po wywołaniu metody [ICorProfilerCallback3:: InitializeForAttach —](icorprofilercallback3-initializeforattach-method.md) . Wskazuje następujące elementy:  
  
- Wywołania zwrotne, które zażądały Profiler w `InitializeForAttach`, zostały aktywowane.  
  
- Profiler może teraz przechwycić odpowiednie identyfikatory bez konieczności powiadamiania o brakujących powiadomieniach.  
  
 Środowisko CLR ignoruje wartość zwracaną z tego wywołania zwrotnego.  
  
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
