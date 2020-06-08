---
title: ICorProfilerCallback7, interfejs
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback7
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: a0be019e-aaa1-4036-990f-565f114d4b5c
ms.openlocfilehash: 9a49d8e1ff31942c6564ab560d6726b9ede26466
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499145"
---
# <a name="icorprofilercallback7-interface"></a>ICorProfilerCallback7, interfejs
[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]  
  
 Podklasa elementu [ICorProfilerCallback6](icorprofilercallback6-interface.md) , która zapewnia metodę wywołania zwrotnego używaną przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera o aktualizacji strumienia symboli skojarzonego z modułem w pamięci.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ModuleInMemorySymbolsUpdated, metoda](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|Powiadamia program profilujący, że jest aktualizowany strumień symboli skojarzony z modułem w pamięci.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
