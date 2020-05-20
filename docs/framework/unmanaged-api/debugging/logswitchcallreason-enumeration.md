---
title: LogSwitchCallReason — Wyliczenie
ms.date: 03/30/2017
api_name:
- LogSwitchCallReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LogSwitchCallReason
helpviewer_keywords:
- LogSwitchCallReason enumeration [.NET Framework debugging]
ms.assetid: 5bbb8d1b-bbc4-47b0-b1b1-2d54cc0be291
topic_type:
- apiref
ms.openlocfilehash: 4d29bb3886ffb51e1dfb9654f4d70ef7c568fd43
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420711"
---
# <a name="logswitchcallreason-enumeration"></a>LogSwitchCallReason — Wyliczenie
Wskazuje operację wykonywaną na przełączniku debugowania/śledzenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum LogSwitchCallReason {  
    SWITCH_CREATE,  
    SWITCH_MODIFY,  
    SWITCH_DELETE  
} LogSwitchCallReason;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`SWITCH_CREATE`|Utworzono przełącznik debugowania/śledzenia.|  
|`SWITCH_MODIFY`|Zmodyfikowano przełącznik debugowania/śledzenia.|  
|`SWITCH_DELETE`|Usunięto przełącznik debugowania/śledzenia.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie — wyliczenia](debugging-enumerations.md)
