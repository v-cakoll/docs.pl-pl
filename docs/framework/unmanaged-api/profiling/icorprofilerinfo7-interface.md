---
title: ICorProfilerInfo7, interfejs
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
ms.openlocfilehash: 0e9f76717aeff27e863245faac241927e7495076
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495492"
---
# <a name="icorprofilerinfo7-interface"></a>ICorProfilerInfo7, interfejs
[Obsługiwane w .NET Framework 4.6.1 i nowszych wersjach]  
  
 Podklasa elementu [ICorProfilerInfo6](icorprofilerinfo6-interface.md) , która zapewnia metodę zastosowania nowo zdefiniowanych metadanych do modułu i zapewnia dostęp do strumienia symboli w pamięci.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ApplyMetaData, metoda](icorprofilerinfo7-applymetadata-method.md)|Stosuje metadane nowo zdefiniowane przez `IMetadataEmit::Define*` metody do określonego modułu.|  
|[GetInMemorySymbolsLength, metoda](icorprofilerinfo7-getinmemorysymbolslength-method.md)|Zwraca długość strumienia symboli w pamięci.|  
|[ReadInMemorySymbols](icorprofilerinfo7-readinmemorysymbols.md)|Odczytuje bajty z strumienia symboli w pamięci.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorProf. idl, CorProf. h  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy profilowania](profiling-interfaces.md)
