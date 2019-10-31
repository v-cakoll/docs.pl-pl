---
title: Metoda ICorDebugDebugEvent::GetThread
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: 66b4abc4bebfbbde2e6a6b25d2bc0e88839a363f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136644"
---
# <a name="icordebugdebugeventgetthread-method"></a>Metoda ICorDebugDebugEvent::GetThread
Pobiera wątek, w którym wystąpiło zdarzenie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a>Parametry  
 ppThread  
 określoną Wskaźnik do adresu obiektu ICorDebugThread, który reprezentuje wątek, w którym wystąpiło zdarzenie.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugDebugEvent, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
