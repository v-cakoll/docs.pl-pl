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
ms.openlocfilehash: da921644c4d967efb0d88060ada0332c5eb63965
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138532"
---
# <a name="icordebugguidtotypeenum-interface"></a>ICorDebugGuidToTypeEnum — Interfejs
Dostarcza moduł wyliczający, który definiuje mapowanie między zestawem identyfikatorów GUID i odpowiadającymi im typami, które są reprezentowane przez wystąpienia ICorDebugType. Ten interfejs dziedziczy metody z interfejsu ICorDebugEnum.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ICorDebugGuidToTypeEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md)|Pobiera określoną liczbę wystąpień [CorDebugGuidToTypeMapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) , które MAPUJĄ identyfikatory GUID na informacje o typie.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt interfejsu `ICorDebugGuidToTypeEnum` można pobrać, wywołując metodę [ICorDebugAppDomain3:: GetCachedWinRTTypes —](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) . Debuger może wywołać [kolejną](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-next-method.md) metodę tego interfejsu, aby pobrać obiekty [CorDebugGuidToTypeMapping —](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md) reprezentujące mapowania zarządzanych reprezentacji typów środowisko wykonawcze systemu Windows załadowanych w domenie aplikacji używanej do wywołania [ ICorDebugAppDomain3:: GetCachedWinRTTypes —](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md) , metoda.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** środowisko wykonawcze systemu Windows  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
