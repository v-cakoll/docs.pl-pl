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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b42a7fc54af56149b602b337e4a6c853c270cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406360"
---
# <a name="cordebuginternalframetype-enumeration"></a>CorDebugInternalFrameType — Wyliczenie
Określa typ ramki stosu. To wyliczenie jest używany przez [ICorDebugInternalFrame::GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`STUBFRAME_NONE`|Wartość null. `ICorDebugInternalFrame::GetFrameType` Metody nigdy nie zwraca tę wartość.|  
|`STUBFRAME_M2U`|Ramka stub niezarządzany zarządzany.|  
|`STUBFRAME_U2M`|Ramka stub niezarządzanych do zarządzanych.|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|Przejścia między domenami aplikacji.|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|Wywołanie metody lightweight.|  
|`STUBFRAME_FUNC_EVAL`|Początek obliczania funkcji.|  
|`STUBFRAME_INTERNALCALL`|Wywoływana wewnętrznie do środowiska CLR.|  
|`STUBFRAME_CLASS_INIT`|Początek inicjowania klasy.|  
|`STUBFRAME_EXCEPTION`|Wyjątek zgłaszany.|  
|`STUBFRAME_SECURITY`|Ramka, używany do zabezpieczenia dostępu kodu.|  
|`STUBFRAME_JIT_COMPILATION`|Środowisko wykonawcze jest metoda kompilacji JIT.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
