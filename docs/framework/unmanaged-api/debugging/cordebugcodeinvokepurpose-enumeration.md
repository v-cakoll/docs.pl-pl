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
ms.openlocfilehash: 858dfe9b15422680a261fef9e22d8c89d9d7fe45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61609145"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a>Wyliczenie CorDebugCodeInvokePurpose
W tym artykule opisano, dlaczego eksportowanych funkcji wywołuje kod zarządzany.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|Kod zarządzany uruchomi żadnych zarządzany punkt wejścia, takich jak p-invoke wstecznego. Wszelkie szczegółowe celem jest nieznany w czasie wykonywania.|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|Zarządzany kod będzie działał Konstruktor statyczny.|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|Zarządzany kod będzie działał implementację dla niektórych metodę interfejsu, która została wywołana.|  
  
## <a name="remarks"></a>Uwagi  
 To wyliczenie jest używane przez [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) metodę w celu udostępnienia informacji na temat krokowe wykonywanie kodu zarządzanego.  
  
> [!NOTE]
>  To wyliczenie jest przeznaczona do użytku w .NET Native tylko w scenariuszach debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
