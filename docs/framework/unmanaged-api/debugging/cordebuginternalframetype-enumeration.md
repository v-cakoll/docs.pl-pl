---
title: CorDebugInternalFrameType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
ms.openlocfilehash: 2be827e12db765485ee889d6a4a19a982dad5d54
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778365"
---
# <a name="cordebuginternalframetype-enumeration"></a>CorDebugInternalFrameType — Wyliczenie
Identyfikuje typ ramki stosu. To wyliczenie jest używane przez metodę [ICorDebugInternalFrame:: GetFrameType](icordebuginternalframe-getframetype-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`STUBFRAME_NONE`|Wartość null. Metoda `ICorDebugInternalFrame::GetFrameType` nigdy nie zwraca tej wartości.|  
|`STUBFRAME_M2U`|Ramka klasy zarządzanej do niezarządzanej.|  
|`STUBFRAME_U2M`|Niezarządzana ramka zastępcza niezarządzana.|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|Przejście między domenami aplikacji.|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|Uproszczone wywołanie metody.|  
|`STUBFRAME_FUNC_EVAL`|Rozpoczęcie obliczania funkcji.|  
|`STUBFRAME_INTERNALCALL`|Wewnętrzne wywołanie środowiska uruchomieniowego języka wspólnego.|  
|`STUBFRAME_CLASS_INIT`|Rozpoczęcie inicjowania klasy.|  
|`STUBFRAME_EXCEPTION`|Wyjątek, który jest generowany.|  
|`STUBFRAME_SECURITY`|Ramka używana do zabezpieczenia dostępu kodu.|  
|`STUBFRAME_JIT_COMPILATION`|Środowisko uruchomieniowe to JIT-kompiluje metodę.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](debugging-enumerations.md)
