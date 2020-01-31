---
title: 'ICorDebugVariableSymbol:: GetSlotIndex, Metoda'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: 3510daffb55bdb22aa5f835bf27157e7c8428509
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790892"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a>ICorDebugVariableSymbol:: GetSlotIndex, Metoda
Pobiera indeks gniazda zarządzanego zmiennej lokalnej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pSlotIndex`  
 określoną Wskaźnik do indeksu gniazda zmiennej lokalnej.  
  
## <a name="return-value"></a>Wartość zwrócona  
 `S_OK`, jeśli się to powiedzie. `E_FAIL`, jeśli zmienna jest argumentem funkcji.  
  
## <a name="remarks"></a>Uwagi  
 Do pobrania informacji o metadanych zmiennej można użyć indeksu gniazda zarządzanego zmiennej lokalnej.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugVariableSymbol, interfejs](icordebugvariablesymbol-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
