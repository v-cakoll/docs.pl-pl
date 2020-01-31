---
title: 'ICorDebugVirtualUnwinder:: GetContext — Metoda'
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: ff5e5bdd66ec44a0931b51212f07485718507576
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790844"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>ICorDebugVirtualUnwinder:: GetContext — Metoda
Pobiera bieżący kontekst tego elementu unwiatrer.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `contextFlags`  
 podczas Flagi określające, które części kontekstu mają być zwracane (zdefiniowane w WinNT. h).  
  
 `cbContextBuf`  
 podczas Liczba bajtów w `contextBuf`.  
  
 `contextSize`  
 określoną Wskaźnik do liczby bajtów, które faktycznie Zapisano do `contextBuf`.  
  
 `contextBuf`  
 określoną Tablica bajtów, która zawiera bieżący kontekst tego elementu unwiatrer.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Wszystkie niepowodzenie wartości HRESULT otrzymanej przez mscordbi jest uznawane za krytyczne i spowoduje, że interfejsy API ICorDebug zwracają `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Uwagi  
 Należy ustawić początkową wartość argumentu `contextBuf` w buforze kontekstu zwracanym przez wywołanie metody [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
 Ponieważ rozwinięcia może przywrócić tylko podzestaw rejestrów, takich jak tylko rejestry nielotne, kontekst może nie być dokładnie zgodny z stanem rejestru w chwili rzeczywistego wywołania metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMemoryBuffer, interfejs](icordebugmemorybuffer-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
