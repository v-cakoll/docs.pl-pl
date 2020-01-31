---
title: Metoda ICorDebugDataTarget2::CreateVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
ms.openlocfilehash: 9fc4facda6253d0c68dcf89b2a1b06e639734efe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788856"
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
  
## <a name="return-value"></a>Wartość zwrócona  
 `S_OK`, jeśli się to powiedzie. Wszystkie inne `HRESULT` wskazują niepowodzenie. Wszystkie niepowodzenie `HRESULT` odebrane przez mscordbi są uznawane za krytyczne i powoduje, że metody [ICorDebug](icordebug-interface.md) zwracają `CORDBG_E_DATA_TARGET_ERROR`.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugDataTarget2, interfejs](icordebugdatatarget2-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
