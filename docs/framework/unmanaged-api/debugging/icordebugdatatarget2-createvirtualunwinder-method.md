---
title: Metoda ICorDebugDataTarget2::CreateVirtualUnwinder
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 421cff28e84106c0859889e6f9e99e870b469a98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a>Metoda ICorDebugDataTarget2::CreateVirtualUnwinder
Tworzy nowy unwinder stosu, uruchamiany rozwinięcia z kontekstu początkowej (co jest zawsze typu liść wątku).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
#### <a name="parameters"></a>Parametry  
 nativeThreadID  
 [in] Wątek macierzysty identyfikator wątku, w których stos jest za oddzielić.  
  
 contextFlags  
 [in] Flagi określające, które części kontekstu są zdefiniowane w `initialContext`.  
  
 cbContext  
 [in] Rozmiar `initialContext`.  
  
 initialContext  
 [in] Dane w tym kontekście.  
  
 ppUnwinder  
 [out] Wskaźnik do adresu icordebugvirtualunwinder — interfejs obiektu.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`w przypadku powodzenia. Inne `HRESULT` wskazuje błąd. Wszelkie niepowodzenie `HRESULT` odebranych przez mscordbi jest on traktowany jako krytyczny i powoduje, że [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metod do zwrócenia `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z platformą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejs ICorDebugDataTarget2](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
