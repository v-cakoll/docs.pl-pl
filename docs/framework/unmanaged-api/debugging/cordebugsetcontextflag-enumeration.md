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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e959ce7a77ad6ceb7f2fc848193cbd9fff028279
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739617"
---
# <a name="cordebugsetcontextflag-enumeration"></a>CorDebugSetContextFlag — Wyliczenie
Wskazuje, czy kontekst jest z aktywnej (lub liścia) ramek na stosie lub obliczeniu, odwijanie od innej ramki.  
  
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
|SET_CONTEXT_FLAG_ACTIVE_FRAME|Kontekst jest aktywny kontekst wątku.|  
|SET_CONTEXT_FLAG_UNWIND_FRAME|Kontekst ma zostać obliczone przez odwijanie od innej ramki.|  
  
## <a name="remarks"></a>Uwagi  
 `CorDebugSetContextFlag` zawiera wartości, które są używane przez [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
