---
title: COR_ACTIVE_FUNCTION — Struktura
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50dd4acece43628b20b6bc50a539ee197e865855
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274156"
---
# <a name="cor_active_function-structure"></a>COR_ACTIVE_FUNCTION — Struktura
Zawiera informacje o funkcjach, które są obecnie aktywne w ramkach wątku. Ta struktura jest używana przez metodę [ICorDebugThread2:: GetActiveFunctions —](icordebugthread2-getactivefunctions-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`pAppDomain`|Wskaźnik do właściciela `ilOffset` domeny aplikacji pola.|  
|`pModule`|Wskaźnik do właściciela `ilOffset` modułu pola.|  
|`pFunction`|Wskaźnik do właściciela `ilOffset` funkcji pola.|  
|`ilOffset`|Przesunięcie języka pośredniego (MSIL) firmy Microsoft dla ramki.|  
|`flags`|Zarezerwowane do użytku w przyszłości.|  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)
