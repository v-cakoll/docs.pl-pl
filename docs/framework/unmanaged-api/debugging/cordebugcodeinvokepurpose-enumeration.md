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
ms.openlocfilehash: f1d4a1e08a63665a532c7aa3572f1e3f9c106ba6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179240"
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
  
|Członek|Opis|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|Brak lub nieznany.|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|Kod zarządzany uruchomi dowolny zarządzany punkt wejścia, taki jak reverse p-invoke. Każdy bardziej szczegółowy cel jest nieznany przez środowisko wykonawcze.|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|Kod zarządzany uruchomi konstruktora statycznego.|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|Kod zarządzany uruchomi implementację dla niektórych metod interfejsu, który został wywołany.|  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie jest używane przez [metodę ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) w celu zapewnienia informacji o przechodzeniu przez kod zarządzany.  
  
> [!NOTE]
> To wyliczenie jest przeznaczone do użycia tylko w scenariuszach debugowania natywnego platformy .NET.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Debugging](../../../../docs/framework/unmanaged-api/debugging/index.md)
