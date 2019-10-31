---
title: CorDebugSetContextFlag — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugSetContextFlag
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugSetContextFlag
helpviewer_keywords:
- CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type:
- apiref
ms.openlocfilehash: 251c96042e8e56112015fb869176c708322267f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097264"
---
# <a name="cordebugsetcontextflag-enumeration"></a>CorDebugSetContextFlag — Wyliczenie
Wskazuje, czy kontekst pochodzi z aktywnej ramki (lub liściowej) na stosie czy został obliczony przez odróżnienie od innej ramki.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|SET_CONTEXT_FLAG_ACTIVE_FRAME|Kontekst jest aktywnym kontekstem wątku.|  
|SET_CONTEXT_FLAG_UNWIND_FRAME|Kontekst został obliczony przez odwinięcia z innej ramki.|  
  
## <a name="remarks"></a>Uwagi  
 `CorDebugSetContextFlag` zawiera wartości, które są używane przez metodę [ICorDebugStackWalk:: SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
