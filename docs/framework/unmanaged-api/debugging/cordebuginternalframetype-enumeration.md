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
ms.openlocfilehash: 05184ceb3b32eb003951fff5cfdfbfb813992552
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216057"
---
# <a name="cordebuginternalframetype-enumeration"></a>CorDebugInternalFrameType — Wyliczenie
Określa typ ramki stosu. To wyliczenie jest używane przez [ICorDebugInternalFrame::GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) metody.  
  
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
|`STUBFRAME_NONE`|Wartość null. `ICorDebugInternalFrame::GetFrameType` Metoda nigdy nie zwraca tę wartość.|  
|`STUBFRAME_M2U`|Ramki zarządzane do niezarządzanego wycinka.|  
|`STUBFRAME_U2M`|Ramka niezarządzane do zarządzanego wycinka.|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|Przejście między domenami aplikacji.|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|Wywołanie metody uproszczone.|  
|`STUBFRAME_FUNC_EVAL`|Początek Obliczanie funkcji.|  
|`STUBFRAME_INTERNALCALL`|Wewnętrzny wywołać środowiska uruchomieniowego języka wspólnego.|  
|`STUBFRAME_CLASS_INIT`|Początek inicjowania klasy.|  
|`STUBFRAME_EXCEPTION`|Wyjątek, który jest generowany.|  
|`STUBFRAME_SECURITY`|Ramka, używany do zabezpieczenia dostępu kodu.|  
|`STUBFRAME_JIT_COMPILATION`|Środowisko uruchomieniowe jest metodą kompilacji JIT.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
