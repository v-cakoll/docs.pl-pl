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
ms.openlocfilehash: e61f6a104b8b9613db32ed6912395fd07c18dcff
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864820"
---
# <a name="icorprofilercallback7-interface"></a>ICorProfilerCallback7, interfejs
[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]  
  
 Podklasa elementu [ICorProfilerCallback6](icorprofilercallback6-interface.md) , która zapewnia metodę wywołania zwrotnego używaną przez środowisko uruchomieniowe języka wspólnego do powiadamiania profilera o aktualizacji strumienia symboli skojarzonego z modułem w pamięci.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ModuleInMemorySymbolsUpdated, metoda](icorprofilercallback7-moduleinmemorysymbolsupdated-method.md)|Powiadamia program profilujący, że jest aktualizowany strumień symboli skojarzony z modułem w pamięci.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
