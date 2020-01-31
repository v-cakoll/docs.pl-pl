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
ms.openlocfilehash: 30008d6cc98f7d0d0501d67e18703ed5a344d43a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794366"
---
# <a name="icordebugilcode2-interface"></a>Interfejs ICorDebugILCode2
[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]  
  
 Logicznie rozszerza interfejs [ICorDebugILCode](icordebugilcode-interface.md) w celu zapewnienia metod, które zwracają token dla sygnatury zmiennej lokalnej funkcji, i mapuje przesunięcia języka pośredniego (IL) narzędzia profilera do oryginalnej metody do przesunięcia Il.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetInstrumentedILMap, metoda](icordebugilcode2-getinstrumentedilmap-method.md)|Zwraca mapę z przesunięć Instrumentacji IL do metody oryginalnej dla tego wystąpienia.|  
|[GetLocalVarSigToken, metoda](icordebugilcode2-getlocalvarsigtoken-method.md)|Pobiera token metadanych lokalnej zmiennej sygnatury dla funkcji reprezentowanej przez to wystąpienie.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugILCode, interfejs](icordebugilcode-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
