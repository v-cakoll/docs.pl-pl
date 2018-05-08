---
title: ICorDebugVirtualUnwinder::Next — metoda
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4bacbd9ef11f6f6cb6d9952290c00f1b8ce50aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvirtualunwindernext-method"></a>ICorDebugVirtualUnwinder::Next — metoda
Przechodzi do kontekstu obiektu wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next();  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli unwind wystąpił pomyślnie, lub `CORDBG_S_AT_END_OF_STACK` Jeżeli nie można ukończyć unwind, ponieważ nie ma więcej ramek.  
  
 Jeśli przerwane zwrócony wynik HRESULT, interfejsy API ICorDebug zwróci `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Uwagi  
 Walkera stosu upewnić się, że postęp, tak że ostatecznie powoduje wywołanie `Next` zwróci przerwane HRESULT lub `CORDBG_S_AT_END_OF_STACK`. Zwracanie `S_OK` nieskończoność może spowodować nieskończoną pętlę.  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z platformą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugMemoryBuffer, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
