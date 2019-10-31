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
ms.openlocfilehash: bc488e55bf64468eb62e2dc6eaedca62ebde3310
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098984"
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
|`BLOCKING_MONITOR_CRITICAL_SECTION`|Wątek próbuje uzyskać sekcję krytyczną, która jest skojarzona z blokadą monitora dla obiektu. Zwykle zdarza się to w przypadku wywołania jednej z <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> lub <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> metod.|  
|`BLOCKING_MONITOR_EVENT`|Wątek oczekuje na zdarzenie skojarzone z blokadą monitora dla obiektu. Zwykle zdarza się to w przypadku wywołania jednej z metod `Wait` <xref:System.Threading.Monitor?displayProperty=nameWithType>.|  
  
## <a name="remarks"></a>Uwagi  
 Gdy element członkowski `BLOCKING_MONITOR_CRITICAL_SECTION` lub `BLOCKING_MONITOR_EVENT` jest używany w strukturze [CorDebugBlockingObject](cordebugblockingobject-structure.md) , `pBlockingObject` element członkowski struktury wskazuje interfejs "ICorDebugValue", który reprezentuje obiekt, który jest wprowadzany. Należy również zastanowić się nad implementacją interfejsu [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](debugging-enumerations.md)
- [Debugowanie](index.md)
