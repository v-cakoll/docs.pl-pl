---
title: ICorProfilerCallback7::ModuleInMemorySymbolsUpdated — metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7.ModuleInMemorySymbolsUpdated
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: f362a896-3247-4894-9727-e48dbbcd2c78
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9aa690378a32ffee2def672f02dc8b5582647a5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455817"
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
 [in] `moduleId`  
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
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ModuleLoadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)  
 [SetEventMask2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)  
 [ICorProfilerCallback7, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
