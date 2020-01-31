---
title: 'ICorDebugVirtualUnwinder:: Next — Metoda'
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: 06d5377ef123cc3f9c91fbfbcf0b0f17a14eb629
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790819"
---
# <a name="icordebugvirtualunwindernext-method"></a>ICorDebugVirtualUnwinder:: Next — Metoda
Przechodzi do kontekstu obiektu wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a>Parametry  
 Brak.  
  
## <a name="return-value"></a>Wartość zwrócona  
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

- [ICorDebugMemoryBuffer, interfejs](icordebugmemorybuffer-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
