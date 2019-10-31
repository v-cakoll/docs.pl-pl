---
title: CorDebugChainReason — Wyliczenie
ms.date: 03/30/2017
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
ms.openlocfilehash: 2f53e3e938f62e714bf421ee7ba0cbf0a47b9f8e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132282"
---
# <a name="cordebugchainreason-enumeration"></a>CorDebugChainReason — Wyliczenie
Wskazuje przyczynę lub przyczyny inicjacji łańcucha wywołań.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
|`CHAIN_NONE`|Nie zainicjowano łańcucha wywołań.|  
|`CHAIN_CLASS_INIT`|Łańcuch został zainicjowany przez konstruktora.|  
|`CHAIN_EXCEPTION_FILTER`|Łańcuch został zainicjowany przez filtr wyjątków.|  
|`CHAIN_SECURITY`|Łańcuch został zainicjowany przez kod, który wymusza zabezpieczenia.|  
|`CHAIN_CONTEXT_POLICY`|Łańcuch został zainicjowany przez zasady kontekstowe.|  
|`CHAIN_INTERCEPTION`|Nie używany.|  
|`CHAIN_PROCESS_START`|Nie używany.|  
|`CHAIN_THREAD_START`|Łańcuch został zainicjowany przez rozpoczęcie wykonywania wątku.|  
|`CHAIN_ENTER_MANAGED`|Łańcuch został zainicjowany przez wpis do kodu zarządzanego.|  
|`CHAIN_ENTER_UNMANAGED`|Łańcuch został zainicjowany przez wpis w kodzie niezarządzanym.|  
|`CHAIN_DEBUGGER_EVAL`|Nie używany.|  
|`CHAIN_CONTEXT_SWITCH`|Nie używany.|  
|`CHAIN_FUNC_EVAL`|Łańcuch został zainicjowany przez funkcję oceny funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Użyj metody [ICorDebugChain:: Getpowód](icordebugchain-getreason-method.md) , aby określić przyczyny inicjacji łańcucha wywołań.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](debugging-enumerations.md)
