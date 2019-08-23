---
title: ICorDebugValue, interfejs
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3bb2f6333f306c8a19c8b2f67986b23819b74ee0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966861"
---
# <a name="icordebugvalue-interface"></a>ICorDebugValue, interfejs
Reprezentuje wartość w debugowanym procesie. Wartość może być wartością odczytu lub zapisu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-createbreakpoint-method.md)|Ta metoda nie jest obecnie zaimplementowana.|  
|[GetAddress, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)|Pobiera adres tego `ICorDebugValue` obiektu, który jest w trakcie debugowania.|  
|[GetSize, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)|Pobiera rozmiar tego `ICorDebugValue` obiektu w bajtach.|  
|[GetType, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md)|Pobiera typ pierwotny tego `ICorDebugValue` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc, własność obiektu wartości jest przenoszona, gdy jest zwracany. Odbiorca jest odpowiedzialny za usunięcie odwołania z obiektu po zakończeniu z obiektem.  
  
 W zależności od tego, skąd została pobrana wartość, wartość może nie być ważna po wznowieniu procesu. Dlatego ogólnie rzecz biorąc wartość nie powinna być utrzymywana przez wywołanie metody [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) .  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugValue3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
