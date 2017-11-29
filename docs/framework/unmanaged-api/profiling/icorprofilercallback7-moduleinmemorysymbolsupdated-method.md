---
title: "ICorProfilerCallback7::ModuleInMemorySymbolsUpdated — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorProfiler7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 088749195165039639f58f4eb6444fb640ab4cec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>ICorProfilerCallback7::ModuleInMemorySymbolsUpdated — metoda
[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]  
  
 Powiadamia profilera przy każdej aktualizacji strumienia symbol skojarzone z modułu w pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleId`  
 Identyfikator modułu w pamięci, których strumienia symbol jest aktualizowany.  
  
## <a name="remarks"></a>Uwagi  
 To wywołanie zwrotne jest kontrolowany przez ustawienie [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) flagi Maska zdarzenia podczas wywoływania metody [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.  
  
> [!NOTE]
>  To zdarzenie nie jest wywoływane dla symboli niejawnie utworzone lub zmodyfikowane za pośrednictwem <xref:System.Reflection.Emit> interfejsów API.  
  
 Nawet gdy symbole znajdują się na początku w wywołaniu do jednego z przeciążeń zarządzanej <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> metod, które obejmuje `rawSymbolStore` argument zawierać symboli dla zestawu środowiska wykonawczego nie może faktycznie powiązania danych symboliczne z modułu dopóki po [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) podczas wywołania zwrotnego. To zdarzenie zawiera nowsze możliwość zbierania symbole dla tych modułów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ModuleLoadFinished — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [Metoda SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)  
 [Interfejs ICorProfilerCallback7](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
