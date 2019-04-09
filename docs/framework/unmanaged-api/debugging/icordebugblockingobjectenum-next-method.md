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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 889c3bb2d5e0cd1feb9e592e667d47dedd4ede36
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171148"
---
# <a name="icordebugblockingobjectenumnext-method"></a>ICorDebugBlockingObjectEnum::Next — Metoda
Pobiera określoną liczbę [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) obiektów z wyliczenia, zaczynając od bieżącej pozycji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba obiektów do pobrania.  
  
 `values`  
 [out] Tablica wskaźników do [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) obiektów.  
  
 `pceltFetched`  
 [out] Wskaźnik do liczby obiektów, które zostały pobrane.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|S_FALSE|`pceltFetched` Nie równa się `celt`.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda funkcje, takie jak typowe wyliczający COM.  
  
 Wartości tablicy wejściowej musi wynosić co najmniej o rozmiarze `celt`. Tablica będzie wypełniona albo następnym `celt` wartości w wyliczeniu lub wszystkie pozostałe wartości w przypadku mniej niż `celt` pozostają. Po powrocie z tej metody `pceltFetched` zostaną wypełnione przy użyciu wartości, które zostały pobrane. Jeśli `values` zawiera nieprawidłowe wskaźniki lub punkty do buforu, który jest mniejszy niż `celt`, lub jeśli `pceltFetched` jest nieprawidłowego wskaźnika, wynik jest niezdefiniowany.  
  
> [!NOTE]
>  Mimo że [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury nie muszą zostać zwolnione, interfejs "ICorDebugValue" wewnątrz niej muszą zostać zwolnione.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugDataTarget — Interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
