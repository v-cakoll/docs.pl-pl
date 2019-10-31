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
ms.openlocfilehash: f6dd10d196ffd3a653584e1bc8d1a5643850bc33
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136609"
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
 [in] `moduleId`  
 Identyfikator modułu w pamięci, którego strumień symboli został zaktualizowany.  
  
## <a name="remarks"></a>Uwagi  
 To wywołanie zwrotne jest kontrolowane przez ustawienie flagi maski zdarzeń [COR_PRF_HIGH_IN_MEMORY_SYMBOLS_UPDATED](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) podczas wywoływania metody [ICorProfilerCallback5:: SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .  
  
> [!NOTE]
> To zdarzenie nie jest obecnie wywoływane dla symboli niejawnie utworzonych lub zmodyfikowanych za pośrednictwem <xref:System.Reflection.Emit> interfejsów API.  
  
 Nawet w przypadku podania symboli przede wszystkim w wywołaniu jednego z przeciążeń zarządzanych metod <xref:System.Reflection.Assembly.Load*?displayProperty=nameWithType>, które zawierają `rawSymbolStore` argument do określenia symboli dla zestawu, środowisko uruchomieniowe może nie skojarzyć danych symbolicznych z modułem do momentu Nastąpiło wywołanie zwrotne [ModuleLoadFinished —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) . To zdarzenie umożliwia późniejsze zbieranie symboli dla takich modułów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ModuleLoadFinished, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [SetEventMask2, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
- [ICorProfilerCallback7, interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)
