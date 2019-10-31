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
ms.openlocfilehash: 0b238a953fa5cd57c8b7af9a0643bfc36ee1032e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088853"
---
# <a name="icordebugappdomain3-interface"></a>ICorDebugAppDomain3 — Interfejs
Zapewnia metody do pobierania informacji o zarządzanych reprezentacjach typów środowisko wykonawcze systemu Windows aktualnie załadowanych w domenie aplikacji. Ten interfejs jest rozszerzeniem interfejsów ICorDebugAppDomain i ICorDebugAppDomain2.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ICorDebugAppDomain3:: GetCachedWinRTTypes —](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypes-method.md)|Pobiera moduł wyliczający dla wszystkich typów środowisko wykonawcze systemu Windows w pamięci podręcznej.|  
|[ICorDebugAppDomain3:: GetCachedWinRTTypesForIIDs —](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-getcachedwinrttypesforiids-method.md)|Pobiera moduł wyliczający dla buforowanych środowisko wykonawcze systemu Windows typów w domenie aplikacji w oparciu o ich identyfikatory interfejsów.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs jest przeznaczony do użycia przez debuger w połączeniu z wywołaniem oceny funkcji do `M:System.Runtime.InteropServices.Marshal.GetInspectableIIDs(System.Object)`. Gdy metoda pobiera identyfikatory interfejsów obsługiwane przez obiekt serwera środowisko wykonawcze systemu Windows, debuger może użyć metod zdefiniowanych w tym interfejsie do mapowania ich na typy zarządzane, które odpowiadają tym interfejsom.  
  
 Aby pobrać wystąpienie tego interfejsu, uruchom `QueryInterface` na wystąpieniu interfejsu ICorDebugAppDomain lub ICorDebugAppDomain2.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** środowisko wykonawcze systemu Windows  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
