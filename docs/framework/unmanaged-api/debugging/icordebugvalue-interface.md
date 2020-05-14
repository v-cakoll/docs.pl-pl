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
ms.openlocfilehash: b8d2e49031e59db0527de3c848d7d390095797bf
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396793"
---
# <a name="icordebugvalue-interface"></a>ICorDebugValue, interfejs
Reprezentuje wartość w debugowanym procesie. Wartość może być wartością odczytu lub zapisu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateBreakpoint — Metoda](icordebugvalue-createbreakpoint-method.md)|Ta metoda nie jest obecnie zaimplementowana.|  
|[GetAddress — Metoda](icordebugvalue-getaddress-method.md)|Pobiera adres tego `ICorDebugValue` obiektu, który jest w trakcie debugowania.|  
|[GetSize — Metoda](icordebugvalue-getsize-method.md)|Pobiera rozmiar tego obiektu w bajtach `ICorDebugValue` .|  
|[GetType, metoda](icordebugvalue-gettype-method.md)|Pobiera typ pierwotny tego `ICorDebugValue` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Ogólnie rzecz biorąc, własność obiektu wartości jest przenoszona, gdy jest zwracany. Odbiorca jest odpowiedzialny za usunięcie odwołania z obiektu po zakończeniu z obiektem.  
  
 W zależności od tego, skąd została pobrana wartość, wartość może nie być ważna po wznowieniu procesu. Dlatego ogólnie rzecz biorąc wartość nie powinna być utrzymywana przez wywołanie metody [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) .  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugValue3 — Interfejs](icordebugvalue3-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
