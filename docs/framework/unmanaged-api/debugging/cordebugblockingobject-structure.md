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
ms.openlocfilehash: 49521e4b4ff5f8c364827b233759e163aca43e39
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542664"
---
# <a name="cordebugblockingobject-structure"></a>CorDebugBlockingObject — Struktura
Definiuje obiekt, który blokuje wątek i powód, że wątek jest zablokowany.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`pBlockingObject`|Obiekt, na którym blokuje wątek. Ten obiekt jest prawidłowy tylko na czas trwania bieżącego stanu zsynchronizowane. Jeśli dwa wątki są przeszkodą w ten sam obiekt w ramach zsynchronizowane takiego samego stanu, mogą oczekiwać [ICorDebugValue::GetAddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md) metody zwracają taką samą wartość. Jednak interfejsy mogą lub nie może być wskaźnik równoważne.|  
|`dwTimeout`|Liczba milisekund, przed wykonaniem operacji blokowania będzie limit czasu lub wartości NIESKOŃCZONE, co oznacza, że będą wykonywane następujące czynności nie przekraczają limit czasu. Wartość limitu czasu określa długość całkowity czas blokowania operacji, nie jest jeszcze pozostało czasu.|  
|`blockingReason`|Powód, że wątek jest zablokowany dla tego obiektu.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
