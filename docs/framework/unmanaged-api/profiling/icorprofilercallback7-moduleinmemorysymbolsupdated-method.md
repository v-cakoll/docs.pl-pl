---
title: Metoda ICorProfilerCallback7::ModuleInMemorySymbolsUpdated
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
ms.openlocfilehash: f33eef5c405b98b9dbf88973a8b7cafad06308b6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466456"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>Metoda ICorProfilerCallback7::ModuleInMemorySymbolsUpdated
[Obsługiwane w programie .NET Framework 4.6.1 i nowszych wersjach]  
  
 Powiadamia program profilujący, zawsze wtedy, gdy strumień symbol skojarzone z modułem w pamięci zostanie zaktualizowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 [in] `moduleId`  
 Identyfikator modułu w pamięci, w której symbol strumień zostanie zaktualizowany.  
  
## <a name="remarks"></a>Uwagi  
 To wywołanie zwrotne jest kontrolowany przez ustawienie [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) flagi maski zdarzenia podczas wywoływania [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) metody.  
  
> [!NOTE]
>  To zdarzenie nie jest inicjowane dla symboli niejawnie utworzone lub zmodyfikowane za pośrednictwem <xref:System.Reflection.Emit> interfejsów API.  
  
 Nawet gdy symbole znajdują się na początku w wywołaniu do jednego z przeciążeń zarządzaną <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> metody, które obejmuje `rawSymbolStore` argument określający symbole dla zestawu, środowisko uruchomieniowe nie może faktycznie kojarzyć dane symboliczne przy użyciu modułu do momentu po [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) wystąpiło wywołanie zwrotne. To zdarzenie zawiera nowsze możliwość zbierania symbole dla tych modułów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ModuleLoadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [ICorProfilerCallback7, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
