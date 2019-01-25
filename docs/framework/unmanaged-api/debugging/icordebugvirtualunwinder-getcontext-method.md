---
title: Metoda ICorDebugVirtualUnwinder::GetContext
ms.date: 03/30/2017
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec68e36e2e5a06836d0f5d5758a230591626b03e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744105"
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>Metoda ICorDebugVirtualUnwinder::GetContext
Pobiera bieżący kontekst tego unwinder.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetContext(  
   [in] ULONG32 contextFlags,  
   [in] ULONG32 cbContextBuf,  
   [out] ULONG32* contextSize,  
   [out, size_is(cbContextBuf)] BYTE contextBuf[]  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `contextFlags`  
 [in] Flagi określające, które części kontekstu do zwrócenia (zdefiniowanej w pliku WinNT.h).  
  
 `cbContextBuf`  
 [in] Liczba bajtów w `contextBuf`.  
  
 `contextSize`  
 [out] Wskaźnik do liczby bajtów rzeczywiście zapisanych na `contextBuf`.  
  
 `contextBuf`  
 [out] Tablica bajtów, która zawiera bieżący kontekst tego unwinder.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wszelkie kończy się niepowodzeniem, wartość HRESULT odebranych przez mscordbi jest uważane za krytyczne i spowoduje, że icordebug — interfejsy API, aby zwrócić `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Uwagi  
 Ustaw wartość początkową `contextBuf` argument do buforu kontekstu zwracany przez wywołanie metody [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metody.  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
 Ponieważ odwijania maja tylko przywracanie w podzbiorze rejestrów, takich jak trwałej rejestruje tylko, kontekst może nie odpowiadają dokładnie stanu rejestru w momencie wywołania metody rzeczywistych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugMemoryBuffer, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
