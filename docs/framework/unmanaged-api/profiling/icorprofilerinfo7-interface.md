---
title: ICorProfilerInfo7, interfejs
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c33e620b861f1065f95ba9f1f732911723c16f88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54526278"
---
# <a name="icorprofilerinfo7-interface"></a>ICorProfilerInfo7, interfejs
[Obsługiwane w [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] i nowszych wersjach]  
  
 Podklasa klasy [ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md) zapewnia metody do stosowania w nowo zdefiniowane metadane do modułu i który zapewnia dostęp do strumienia symboli w pamięci.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ApplyMetaData, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|Stosuje metadane nowo zdefiniowane przez `IMetadataEmit::Define*` metody służące do określonego modułu.|  
|[GetInMemorySymbolsLength, metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|Zwraca długość strumienia symboli w pamięci.|  
|[ReadInMemorySymbols](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|Odczytuje bajtów ze strumienia symboli w pamięci.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf.idl, CorProf.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Interfejsy profilowania](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
