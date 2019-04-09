---
title: CorDebugStepReason — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ce2b23306e7e38f3982f8d5a4b377aa2f9547c4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59186254"
---
# <a name="cordebugstepreason-enumeration"></a>CorDebugStepReason — Wyliczenie
Wskazuje wynik pojedynczego kroku.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`STEP_NORMAL`|Przechodzenie krok po kroku zakończone normalnie w ramach tej samej funkcji.|  
|`STEP_RETURN`|Przechodzenie krok po kroku nadal normalnie po wartość zwrócona przez funkcję.|  
|`STEP_CALL`|Na początku nowo wywołana funkcja przechodzenie krok po kroku nadal normalnie.|  
|`STEP_EXCEPTION_FILTER`|Wyjątek został wygenerowany i formant został przekazany do filtra wyjątku.|  
|`STEP_EXCEPTION_HANDLER`|Wyjątek został wygenerowany i formant został przekazany do obsługi wyjątków.|  
|`STEP_INTERCEPT`|Formant został przekazany do interceptor.|  
|`STEP_EXIT`|Wątek został zakończony przed ukończeniem kroku.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [StepComplete, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [Debugowanie — wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
