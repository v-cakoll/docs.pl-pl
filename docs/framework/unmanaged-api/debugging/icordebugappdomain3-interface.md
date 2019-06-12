---
title: ICorDebugAppDomain3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3
helpviewer_keywords:
- ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 875ef5be-c1e7-4d95-97e9-d3a667aeaba0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 256fd900fa73948b4ca42ac6b6f21f145effc461
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025895"
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3 — Interfejs
Dostarcza metody do pobierania informacji o zarządzanych reprezentacja typów środowiska wykonawczego Windows, które obecnie załadowane w domenie aplikacji. Ten interfejs jest rozszerzeniem interfejsów ICorDebugAppDomain i ICorDebugAppDomain2.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ICorDebugAppDomain3::GetCachedWinRTTypes](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|Pobiera moduł wyliczający dla wszystkich typów środowiska wykonawczego Windows pamięci podręcznej.|  
|[ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|Pobiera moduł wyliczający dla pamięci podręcznej typów środowiska wykonawczego Windows w domenie aplikacji, w oparciu o ich identyfikatory interfejsu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest przeznaczona do użycia przez debuger w połączeniu z wywołaniem oceny funkcji `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`. Jeśli metoda pobiera identyfikatory interfejsu obsługiwane przez obiekt serwera Windows Runtime, debuger może używać metody zdefiniowane w tym interfejsie mapować je na zarządzane typy, które odnoszą się do tych interfejsów.  
  
 Uruchom, aby pobrać wystąpienie tego interfejsu `QueryInterface` w wystąpieniu ICorDebugAppDomain lub icordebugappdomain2 — interfejs.  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Środowisko wykonawcze systemu Windows  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
