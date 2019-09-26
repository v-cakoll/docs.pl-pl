---
title: CorDebugBlockingObject — Struktura
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57de11c1c40c05befcf3c99c31c2e07e1ecaec5a
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273973"
---
# <a name="cordebugblockingobject-structure"></a>CorDebugBlockingObject — Struktura
Definiuje obiekt, który blokuje wątek i konkretną przyczynę zablokowania wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`pBlockingObject`|Obiekt, na którym jest blokowany wątek. Ten obiekt jest prawidłowy tylko dla czasu trwania bieżącego zsynchronizowanego stanu. Jeśli dwa wątki blokują ten sam obiekt w tym samym stanie zsynchronizowanym, można oczekiwać, że metoda [ICorDebugValue:: GetAddress](icordebugvalue-getaddress-method.md) zwraca tę samą wartość. Jednak interfejsy mogą lub nie mogą być odpowiednikami wskaźnika.|  
|`dwTimeout`|Liczba milisekund przed upływem limitu czasu operacji blokowania lub wartość NIESKOŃCZONość, która wskazuje, że nie przekroczy limitu czasu. Wartość limitu czasu określa łączny czas trwania operacji blokowania, a nie czas, który jest nadal pozostały.|  
|`blockingReason`|Przyczyna blokowania wątku dla tego obiektu.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)
