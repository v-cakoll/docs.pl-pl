---
title: Interfejs ICorDebugILCode2
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a27dbd8b5013937bb97f37113687405c988c1fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142665"
---
# <a name="icordebugilcode2-interface"></a>Interfejs ICorDebugILCode2
[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]  
  
 Rozszerza logicznie [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interfejsu podania metod, które zwracają token do funkcji lokalnej zmiennej podpisu i mapy, program profilujący instrumentowanych języka pośredniego (IL) przesuwa się do oryginalnej metody IL przesunięcia.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetInstrumentedILMap, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|Zwraca mapę z profilera Instrumentacji przesunięcia IL do oryginalnego przesunięcia IL metody dla tego wystąpienia.|  
|[GetLocalVarSigToken, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|Pobiera token metadanych dla lokalnej zmiennej podpisu dla funkcji, która jest reprezentowana przez to wystąpienie.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugILCode, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
