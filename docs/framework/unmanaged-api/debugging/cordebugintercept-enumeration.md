---
title: CorDebugIntercept — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ee2272a43d9f71cd49754a7f4233868b8bb9134
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugintercept-enumeration"></a>CorDebugIntercept — Wyliczenie
Wskazuje typy kodu, który może zostać przechwycony (tj. przeprowadził do).  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`INTERCEPT_NONE`|Żaden kod nie może zostać przechwycony.|  
|`INTERCEPT_CLASS_INIT`|Konstruktor może zostać przechwycony.|  
|`INTERCEPT_EXCEPTION_FILTER`|Może zostać przechwycona filtru wyjątków.|  
|`INTERCEPT_SECURITY`|Kod, który wymusza zabezpieczeń mogą zostać przechwycone.|  
|`INTERCEPT_CONTEXT_POLICY`|Może zostać przechwycona zasad kontekstu.|  
|`INTERCEPT_INTERCEPTION`|Nie używany.|  
|`INTERCEPT_ALL`|Cały kod może zostać przechwycony.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) metody, aby określić typy kodu, który może zostać przechwycony.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
