---
title: 'ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated, Metoda'
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
ms.openlocfilehash: 860ecde22dead112a42b6ac868e34f0e9cd3531d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916199"
---
# <a name="icorprofilercallback7moduleinmemorysymbolsupdated-method"></a>ICorProfilerCallback7:: ModuleInMemorySymbolsUpdated, Metoda
[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]  
  
 Powiadamia profiler za każdym razem, gdy zostanie zaktualizowany strumień symboli skojarzony z modułem w pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ModuleInMemorySymbolsUpdated(  
     ModuleID moduleId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 podczas`moduleId`  
 Identyfikator modułu w pamięci, którego strumień symboli został zaktualizowany.  
  
## <a name="remarks"></a>Uwagi  
 To wywołanie zwrotne jest kontrolowane przez ustawienie flagi maski zdarzeń [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) podczas wywoływania metody [ICorProfilerCallback5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .  
  
> [!NOTE]
> To zdarzenie nie jest obecnie wywoływane dla symboli niejawnie utworzonych lub zmodyfikowanych za pośrednictwem <xref:System.Reflection.Emit> interfejsów API.  
  
 Nawet jeśli symbole są dostarczane z góry w wywołaniu jednego z przeciążeń metod zarządzanych <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType> , które `rawSymbolStore` zawierają argument, aby określić symbole dla zestawu, środowisko uruchomieniowe może w rzeczywistości nie skojarzyć danych symbolicznych z modułem do momentu wystąpienia wywołania zwrotnego [ModuleLoadFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) . To zdarzenie umożliwia późniejsze zbieranie symboli dla takich modułów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorProf. idl, CorProf. h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ModuleLoadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [ICorProfilerCallback7, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
