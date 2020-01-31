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
ms.openlocfilehash: e1044386bd6251132703c4e98a0cf2ed267d34e0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791134"
---
# <a name="icordebugvalue-interface"></a>ICorDebugValue, interfejs
Reprezentuje wartość w debugowanym procesie. Wartość może być wartością odczytu lub zapisu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint, metoda](icordebugvalue-createbreakpoint-method.md)|Ta metoda nie jest obecnie zaimplementowana.|  
|[GetAddress, metoda](icordebugvalue-getaddress-method.md)|Pobiera adres tego obiektu `ICorDebugValue`, który jest w trakcie debugowania.|  
|[GetSize, metoda](icordebugvalue-getsize-method.md)|Pobiera rozmiar (w bajtach) tego obiektu `ICorDebugValue`.|  
|[GetType, metoda](icordebugvalue-gettype-method.md)|Pobiera typ pierwotny tego obiektu `ICorDebugValue`.|  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc, własność obiektu wartości jest przenoszona, gdy jest zwracany. Odbiorca jest odpowiedzialny za usunięcie odwołania z obiektu po zakończeniu z obiektem.  
  
 W zależności od tego, skąd została pobrana wartość, wartość może nie być ważna po wznowieniu procesu. Dlatego ogólnie rzecz biorąc wartość nie powinna być utrzymywana przez wywołanie metody [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) .  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugValue3, interfejs](icordebugvalue3-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
