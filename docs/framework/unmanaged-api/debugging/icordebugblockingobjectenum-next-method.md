---
title: ICorDebugBlockingObjectEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type:
- apiref
ms.openlocfilehash: 3a1c4a931a61186c4737aada47ceb861e7848e7b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122829"
---
# <a name="icordebugblockingobjectenumnext-method"></a>ICorDebugBlockingObjectEnum::Next — Metoda
Pobiera określoną liczbę obiektów [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) z wyliczenia, rozpoczynając od bieżącego położenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba obiektów do pobrania.  
  
 `values`  
 określoną Tablica wskaźników do obiektów [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .  
  
 `pceltFetched`  
 określoną Wskaźnik do liczby obiektów, które zostały pobrane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|S_FALSE|`pceltFetched` nie jest równe `celt`.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda działa jak typowy moduł wyliczający COM.  
  
 Wartości tablicy wejściowej muszą mieć co najmniej rozmiar `celt`. Tablica zostanie wypełniona przy użyciu następnych wartości `celt` w wyliczeniu lub dla wszystkich pozostałych wartości, jeśli pozostanie mniej niż `celt`. Gdy ta metoda zostanie zwrócona, `pceltFetched` zostanie wypełniony liczbą pobieranych wartości. Jeśli `values` zawiera nieprawidłowe wskaźniki lub wskazuje bufor, który jest mniejszy niż `celt`lub jeśli `pceltFetched` jest nieprawidłowym wskaźnikiem, wynik jest niezdefiniowany.  
  
> [!NOTE]
> Mimo że struktura [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) nie musi zostać wydana, należy wydać interfejs "ICorDebugValue" wewnątrz niego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
