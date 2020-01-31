---
title: ICorProfilerInfo7, interfejs
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: f80f310c10bae33583cb7cd2048ede4f5efbe14c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861752"
---
# <a name="icorprofilerinfo7-interface"></a>ICorProfilerInfo7, interfejs
[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]  
  
 Podklasa elementu [ICorProfilerInfo6](icorprofilerinfo6-interface.md) , która zapewnia metodę zastosowania nowo zdefiniowanych metadanych do modułu i zapewnia dostęp do strumienia symboli w pamięci.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ApplyMetaData, metoda](icorprofilerinfo7-applymetadata-method.md)|Stosuje metadane nowo zdefiniowane przez metody `IMetadataEmit::Define*` do określonego modułu.|  
|[GetInMemorySymbolsLength, metoda](icorprofilerinfo7-getinmemorysymbolslength-method.md)|Zwraca długość strumienia symboli w pamięci.|  
|[ReadInMemorySymbols](icorprofilerinfo7-readinmemorysymbols.md)|Odczytuje bajty z strumienia symboli w pamięci.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
