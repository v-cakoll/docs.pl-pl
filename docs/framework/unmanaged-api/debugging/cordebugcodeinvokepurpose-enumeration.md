---
title: Wyliczenie CorDebugCodeInvokePurpose
ms.date: 03/30/2017
api_name:
- CorDebugInvokePurpose
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b5de58caeeac5ae85402e91a1402958e68336bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967595"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a>Wyliczenie CorDebugCodeInvokePurpose
Opisuje, dlaczego wyeksportowana funkcja wywołuje kod zarządzany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|Brak lub nieznany.|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|Kod zarządzany będzie uruchamiał każdy zarządzany punkt wejścia, taki jak odwrotne wywołanie p. Każdy bardziej szczegółowy cel jest nieznany w czasie wykonywania.|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|Kod zarządzany będzie uruchamiał Konstruktor statyczny.|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|Kod zarządzany uruchomi implementację dla pewnej metody interfejsu, która została wywołana.|  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie jest używane przez metodę [Metoda ICorDebugProcess6:: GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) w celu uzyskania informacji na temat wykonywania kroków w kodzie zarządzanym.  
  
> [!NOTE]
> To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
