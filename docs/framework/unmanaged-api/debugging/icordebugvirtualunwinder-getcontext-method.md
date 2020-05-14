---
title: 'ICorDebugVirtualUnwinder:: GetContext — Metoda'
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
ms.openlocfilehash: e203db78b40bf4305316046cfcd679f3d10d1876
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396436"
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
 podczas Liczba bajtów w `contextBuf` .  
  
 `contextSize`  
 określoną Wskaźnik do liczby bajtów, które są w rzeczywistości zapisywane `contextBuf` .  
  
 `contextBuf`  
 określoną Tablica bajtów, która zawiera bieżący kontekst tego elementu unwiatrer.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wszystkie niepowodzenie wartości HRESULT otrzymanej przez mscordbi jest uznawane za krytyczne i spowoduje zwrócenie interfejsów API ICorDebug `CORDBG_E_DATA_TARGET_ERROR` .  
  
## <a name="remarks"></a>Uwagi  
 Ustawiasz początkową wartość `contextBuf` argumentu dla buforu kontekstu zwracanego przez wywołanie metody [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
 Ponieważ rozwinięcia może przywrócić tylko podzestaw rejestrów, takich jak tylko rejestry nielotne, kontekst może nie być dokładnie zgodny z stanem rejestru w chwili rzeczywistego wywołania metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMemoryBuffer, interfejs](icordebugmemorybuffer-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
