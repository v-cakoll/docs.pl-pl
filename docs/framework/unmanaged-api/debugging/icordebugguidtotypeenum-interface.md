---
title: ICorDebugGuidToTypeEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum
helpviewer_keywords:
- ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: aa32b12b-05fc-4ea8-a904-adae25034269
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22cd08154268bdf1e819a0ec0067b05a81d60b22
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025825"
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum — Interfejs
Dostarcza moduł wyliczający, który definiuje mapowanie między zbiór identyfikatorów GUID i odpowiednie typy, które są reprezentowane przez ICorDebugType wystąpienia. Ten interfejs dziedziczy metody icordebugenum — interfejs.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ICorDebugGuidToTypeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|Pobiera określoną liczbę [cordebugguidtotypemapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) wystąpień, które mapują identyfikatory GUID do informacji o typie.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugGuidToTypeEnum` Obiektu interfejsu może być pobierany przez wywołanie [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metody. Debuger może wywołać ten interfejs [dalej](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) metodę, która pobierze [cordebugguidtotypemapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) obiekty reprezentujące mapowania zarządzanych reprezentacja typów środowiska wykonawczego Windows załadowany w Domena aplikacji używana do wywołań [ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Środowisko wykonawcze systemu Windows  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
