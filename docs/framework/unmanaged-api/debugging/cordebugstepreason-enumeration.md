---
title: "CorDebugStepReason — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugStepReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugStepReason
helpviewer_keywords: CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 32892a14de820e8add38654cef92aa44930aec62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
|`STEP_NORMAL`|Wykonywanie krok po kroku zwykle zakończona w ramach tej samej funkcji.|  
|`STEP_RETURN`|Wykonywanie krok po kroku nadal normalnie, po wartość zwrócona przez funkcję.|  
|`STEP_CALL`|Wykonywanie krok po kroku nadal normalnie na początku nowo wywołanej funkcji.|  
|`STEP_EXCEPTION_FILTER`|Wyjątek został wygenerowany i formant został przekazany do filtru wyjątków.|  
|`STEP_EXCEPTION_HANDLER`|Wyjątek został wygenerowany i formant został przekazany do obsługi wyjątków.|  
|`STEP_INTERCEPT`|Formant został przekazany do interceptora.|  
|`STEP_EXIT`|Wątek został zakończony przed ukończeniem kroku.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [StepComplete — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)  
 [Debugowanie — wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
