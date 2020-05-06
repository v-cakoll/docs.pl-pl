---
title: CorDebugIlToNativeMappingTypes — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugIlToNativeMappingTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIlToNativeMappingTypes
helpviewer_keywords:
- CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type:
- apiref
ms.openlocfilehash: 808fc70a308eff1b05aa49ea2bb89fe53377c973
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795849"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a>CorDebugIlToNativeMappingTypes — Wyliczenie
Wskazuje, czy konkretny zakres instrukcji macierzystych, reprezentowany przez wystąpienie struktury COR_DEBUG_IL_TO_NATIVE_MAP, odpowiada specjalnemu regionowi kodu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`NO_MAPPING`|Zakres instrukcji natywnych nie odpowiada żadnemu specjalnemu regionowi kodu.|  
|`PROLOG`|Zakres natywnych instrukcji odpowiada prologu.|  
|`EPILOG`|Zakres instrukcji natywnych odpowiada epilogu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetILToNativeMapping — Metoda](icordebugcode-getiltonativemapping-method.md)
- [Debugowanie — wyliczenia](debugging-enumerations.md)
