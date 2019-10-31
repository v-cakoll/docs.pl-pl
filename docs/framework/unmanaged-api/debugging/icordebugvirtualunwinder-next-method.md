---
title: 'ICorDebugVirtualUnwinder:: Next — Metoda'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: ed80b7a630f78002ded14a1bec206cc8712bd504
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121859"
---
# <a name="icordebugvirtualunwindernext-method"></a>ICorDebugVirtualUnwinder:: Next — Metoda
Przechodzi do kontekstu obiektu wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a>Parametry  
 Brak.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`, jeśli wystąpiło pomyślne przewinięcie lub `CORDBG_S_AT_END_OF_STACK`, jeśli nie można ukończyć operacji unwindy, ponieważ nie ma więcej ramek.  
  
 Jeśli zwracana jest niepowodzenie HRESULT, interfejsy API ICorDebug będą zwracać `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Uwagi  
 Analizator stosu powinien zapewnić, że postępuje postęp, aby ostatecznie wywołanie `Next` zwróci błąd HRESULT lub `CORDBG_S_AT_END_OF_STACK`. Zwracanie `S_OK` nieskończoność może spowodować nieskończoną pętlę.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMemoryBuffer, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
