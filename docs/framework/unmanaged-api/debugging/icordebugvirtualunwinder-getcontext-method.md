---
title: "ICorDebugVirtualUnwinder::GetContext — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: fe502a76-3068-47e5-a0a0-85ccb72dfac3
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45a914005e84d33b39d72fce96679e275b921d3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvirtualunwindergetcontext-method"></a>ICorDebugVirtualUnwinder::GetContext — metoda
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
 [out] Wskaźnik do liczba bajtów zapisywanych faktycznie `contextBuf`.  
  
 `contextBuf`  
 [out] Tablica bajtów zawierającą bieżący kontekst tego unwinder.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wszelkie niepowodzenia wartość HRESULT odebranych przez mscordbi jest on traktowany jako krytyczny i spowoduje, że ICorDebug interfejsów API powrócić `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Uwagi  
 Ustaw wartość początkową z `contextBuf` argument do buforu kontekstu zwrócony przez wywołanie metody [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metody.  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z platformą .NET Native.  
  
 Ponieważ odwijaniem może tylko restore a podzestawu rejestrów, takich jak trwałej rejestruje tylko, kontekst nie może pasować stanu rejestru w momencie wywołania metody rzeczywistych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
