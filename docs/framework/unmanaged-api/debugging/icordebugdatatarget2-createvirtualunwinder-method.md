---
title: Metoda ICorDebugDataTarget2::CreateVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: f9a9038bd0d268e09d8518fa50534a9959b456de
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122185"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a>Metoda ICorDebugDataTarget2::CreateVirtualUnwinder
Tworzy nowy wątek unwiatrer, który zaczyna odwracać od kontekstu początkowego (co nie musi być elementem liścia wątku).  
  
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
 podczas Identyfikator wątku natywnego wątku, którego stos ma być rozłożony.  
  
 contextFlags  
 podczas Flagi określające, które części kontekstu są zdefiniowane w `initialContext`.  
  
 cbContext  
 podczas Rozmiar `initialContext`.  
  
 initialContext  
 podczas Dane w kontekście.  
  
 ppUnwinder  
 określoną Wskaźnik do adresu obiektu interfejsu ICorDebugVirtualUnwinder.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK`, jeśli się to powiedzie. Wszystkie inne `HRESULT` wskazują niepowodzenie. Wszystkie niepowodzenie `HRESULT` odebrane przez mscordbi są uznawane za krytyczne i powoduje, że metody [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) zwracają `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugDataTarget2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
