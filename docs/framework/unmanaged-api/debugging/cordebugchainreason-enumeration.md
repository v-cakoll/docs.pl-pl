---
title: "CorDebugChainReason — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugChainReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugChainReason
helpviewer_keywords:
- CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1951983c9d167862169bd6178dc65693d724dc0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugchainreason-enumeration"></a>CorDebugChainReason — Wyliczenie
Wskazuje powód lub powody rozpoczęcia łańcuch wywołań.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`CHAIN_NONE`|Żaden łańcuch wywołań została zainicjowana.|  
|`CHAIN_CLASS_INIT`|Łańcuch został zainicjowany przez Konstruktor.|  
|`CHAIN_EXCEPTION_FILTER`|Łańcuch zostało zainicjowane przez filtru wyjątków.|  
|`CHAIN_SECURITY`|Łańcuch zostało zainicjowane przez kod, który wymusza zabezpieczeń.|  
|`CHAIN_CONTEXT_POLICY`|Łańcuch została zainicjowana przy użyciu zasad kontekstu.|  
|`CHAIN_INTERCEPTION`|Nie używany.|  
|`CHAIN_PROCESS_START`|Nie używany.|  
|`CHAIN_THREAD_START`|Łańcuch została zainicjowana przy rozpoczęciu wykonywania wątku.|  
|`CHAIN_ENTER_MANAGED`|Łańcuch zostało zainicjowane przez wejścia kodu zarządzanego.|  
|`CHAIN_ENTER_UNMANAGED`|Łańcuch zostało zainicjowane przez wejścia kodu niezarządzanego.|  
|`CHAIN_DEBUGGER_EVAL`|Nie używany.|  
|`CHAIN_CONTEXT_SWITCH`|Nie używany.|  
|`CHAIN_FUNC_EVAL`|Łańcuch zostało zainicjowane przez Obliczanie funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) metodę, aby ustalić przyczyny rozpoczęcia łańcuch wywołań.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
