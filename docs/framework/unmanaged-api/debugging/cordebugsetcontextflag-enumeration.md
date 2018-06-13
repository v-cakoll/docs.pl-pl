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
ms.openlocfilehash: badd79926e8f039cf6b947dd6655e2cd679e3000
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406978"
---
# <a name="cordebugsetcontextflag-enumeration"></a>CorDebugSetContextFlag — Wyliczenie
Wskazuje, czy kontekst jest z aktywnego (lub typu liść) ramek na stosie lub został obliczony przy odwijanie od innej ramki.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|SET_CONTEXT_FLAG_UNWIND_FRAME|Kontekst został obliczony przy odwijanie od innej ramki.|  
  
## <a name="remarks"></a>Uwagi  
 `CorDebugSetContextFlag` udostępnia wartości, które są używane przez [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
