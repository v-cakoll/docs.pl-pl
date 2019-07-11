---
title: Metoda ICorDebugDataTarget2::CreateVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a983561f34bee96f5de1e05d608bff930c7ec8c0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750233"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a>Metoda ICorDebugDataTarget2::CreateVirtualUnwinder
Tworzy nowy unwinder stosu, który rozpoczyna się odwijanie od początkowego kontekstu, (które niekoniecznie liścia wątku).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a>Parametry  
 nativeThreadID  
 [in] Identyfikator wątku natywnych wątku, którego stosu, które ma być rozwinięty.  
  
 contextFlags  
 [in] Flagi określające, części kontekstu, które są zdefiniowane w `initialContext`.  
  
 cbContext  
 [in] Rozmiar `initialContext`.  
  
 initialContext  
 [in] Dane w kontekście.  
  
 ppUnwinder  
 [out] Wskaźnik na adres obiektu interfejsu ICorDebugVirtualUnwinder.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli to się powiedzie. Inne `HRESULT` wskazuje błąd. Wszelkie niepowodzenia `HRESULT` odebranych przez mscordbi jest uważane za krytyczne i powoduje, że [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metody, aby zwrócić `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ta metoda jest tylko dostępne z architekturą .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugDataTarget2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
