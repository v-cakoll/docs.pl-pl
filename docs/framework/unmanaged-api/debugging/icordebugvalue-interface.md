---
title: ICorDebugValue — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue
helpviewer_keywords:
- ICorDebugValue interface [.NET Framework debugging]
ms.assetid: b2f7007f-c446-4b18-aed1-a25cff8aee31
topic_type:
- apiref
ms.openlocfilehash: 77d28d8eef97a934c15ac29725f856f4bf39e6ce
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140160"
---
# <a name="icordebugvalue-interface"></a>ICorDebugValue — Interfejs
Reprezentuje wartość w debugowanym procesie. Wartość może być wartością odczytu lub zapisu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|Ta metoda nie jest obecnie zaimplementowana.|  
|[GetAddress, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|Pobiera adres tego obiektu `ICorDebugValue`, który jest w trakcie debugowania.|  
|[GetSize, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|Pobiera rozmiar (w bajtach) tego obiektu `ICorDebugValue`.|  
|[GetType, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|Pobiera typ pierwotny tego obiektu `ICorDebugValue`.|  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc, własność obiektu wartości jest przenoszona, gdy jest zwracany. Odbiorca jest odpowiedzialny za usunięcie odwołania z obiektu po zakończeniu z obiektem.  
  
 W zależności od tego, skąd została pobrana wartość, wartość może nie być ważna po wznowieniu procesu. Dlatego ogólnie rzecz biorąc wartość nie powinna być utrzymywana przez wywołanie metody [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) .  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugValue3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
