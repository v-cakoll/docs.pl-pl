---
title: Metoda ICorDebugProcess6::ProcessStateChanged
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: b6665df550a2d07a3fa84c3f2b6bf07f459cd713
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792202"
---
# <a name="icordebugprocess6processstatechanged-method"></a>Metoda ICorDebugProcess6::ProcessStateChanged
Powiadamia [ICorDebug](icordebug-interface.md) o tym, że proces jest uruchomiony.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a>Parametry  
 `change`  
 podczas Składowa wyliczenia [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)  
  
## <a name="remarks"></a>Uwagi  
 Debuger wywołuje tę metodę, aby powiadomić [ICorDebug](icordebug-interface.md) , że proces jest uruchomiony.  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess6, interfejs](icordebugprocess6-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
