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
ms.openlocfilehash: 0791a59e0325668960dcfc98816920db55bcfb87
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199937"
---
# <a name="cordebugintercept-enumeration"></a>CorDebugIntercept — Wyliczenie
Określa typy kodu, która może zostać przechwycona (który jest zmieniana do).  
  
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
|`INTERCEPT_NONE`|Brak kodu mogą zostać przechwycone.|  
|`INTERCEPT_CLASS_INIT`|Konstruktor mogą zostać przechwycone.|  
|`INTERCEPT_EXCEPTION_FILTER`|Mogą zostać przechwycone filtra wyjątku.|  
|`INTERCEPT_SECURITY`|Kod, który wymusza zabezpieczeń mogą zostać przechwycone.|  
|`INTERCEPT_CONTEXT_POLICY`|Zasady kontekstu może zostać przechwycone.|  
|`INTERCEPT_INTERCEPTION`|Nie używany.|  
|`INTERCEPT_ALL`|Cały kod może zostać przechwycone.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj [ICorDebugStepper::SetInterceptMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md) metodę, aby określić typy kodu, która może zostać przechwycona.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie — wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
