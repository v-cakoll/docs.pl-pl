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
ms.openlocfilehash: 144bdb1b4e479c1e75f89911ad5002e2650e405d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098123"
---
# <a name="cordebugintercept-enumeration"></a>CorDebugIntercept — Wyliczenie
Wskazuje typy kodu, które mogą być przechwytywane (to jest, w trakcie).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
|`INTERCEPT_NONE`|Kod nie może być przechwytywany.|  
|`INTERCEPT_CLASS_INIT`|Konstruktor może być przechwytywany.|  
|`INTERCEPT_EXCEPTION_FILTER`|Filtr wyjątku może być przechwytywany.|  
|`INTERCEPT_SECURITY`|Kod, który wymusza zabezpieczenia, może być przechwytywany.|  
|`INTERCEPT_CONTEXT_POLICY`|Zasady kontekstu mogą być przechwytywane.|  
|`INTERCEPT_INTERCEPTION`|Nie używany.|  
|`INTERCEPT_ALL`|Cały kod może być przechwytywany.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj metody [ICorDebugStepper:: SetInterceptMask —](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) , aby określić typy kodu, które mogą być przechwytywane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
