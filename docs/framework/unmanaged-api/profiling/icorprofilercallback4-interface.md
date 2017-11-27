---
title: "ICorProfilerCallback4 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4
helpviewer_keywords: ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 64a26f5dfb0ad9f06bb1b9eb31dcae36f4623c4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4-interface"></a>ICorProfilerCallback4 — Interfejs
Udostępnia metody wywołania zwrotnego, używane przez środowisko uruchomieniowe języka wspólnego (CLR) do przekazywania informacji do profilera.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReJITParameters — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|Umożliwia profilującego można ustawić flagi generowania inny kod dla nowych treści metody ponownej kompilacji.|  
|[MovedReferences2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|Raporty nowy układ obiektów na stercie w wyniku kompaktowania wyrzucania elementów bezużytecznych.|  
|[ReJITCompilationFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|Powiadamia profilera zakończenie przy użyciu kompilatora just in time (JIT) kompilację funkcji.|  
|[ReJITCompilationStarted — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|Powiadamia profilera, czy można ponownie skompilować funkcję została uruchomiona przy użyciu kompilatora just in time (JIT).|  
|[ReJITError — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|Zgłasza błąd podczas przetwarzania żądania ponownej kompilacji.|  
|[SurvivingReferences2 — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|Raporty układ obiektów na stercie wyniku-kompaktowania wyrzucania elementów bezużytecznych.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorProfilerCallback2 — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerInfo — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
