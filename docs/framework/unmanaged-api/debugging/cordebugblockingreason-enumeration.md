---
title: CorDebugBlockingReason — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99fcf160b3e3b2b238520e3db5ba2e74b270380a
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274140"
---
# <a name="cordebugblockingreason-enumeration"></a>CorDebugBlockingReason — Wyliczenie
Określa przyczyny, dla których wątek może zostać zablokowany dla danego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`BLOCKING_NONE`|Tylko do użytku wewnętrznego.|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|Wątek próbuje uzyskać sekcję krytyczną, która jest skojarzona z blokadą monitora dla obiektu. Zwykle zdarza się to w przypadku wywołania jednej z <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> metod lub. <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>|  
|`BLOCKING_MONITOR_EVENT`|Wątek oczekuje na zdarzenie skojarzone z blokadą monitora dla obiektu. Zwykle zdarza się to w przypadku wywołania jednej z <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` metod.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy element `BLOCKING_MONITOR_EVENT` `pBlockingObject` or jest używany w strukturze CorDebugBlockingObject, element członkowski struktury wskazuje interfejs "ICorDebugValue", który reprezentuje obiekt, który jest wprowadzany. [](cordebugblockingobject-structure.md) `BLOCKING_MONITOR_CRITICAL_SECTION` Należy również zastanowić się nad implementacją interfejsu [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** CorDebug.idl, CorDebug.h  
  
 **Biblioteki** CorGuids.lib  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](debugging-enumerations.md)
- [Debugowanie](index.md)
