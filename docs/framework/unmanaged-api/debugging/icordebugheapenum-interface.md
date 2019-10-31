---
title: ICorDebugHeapEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum
helpviewer_keywords:
- ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 99cbc1eb-d539-4f76-a0d8-b93348112f14
topic_type:
- apiref
ms.openlocfilehash: e8d1948a7d0ff23410ba8670628424a4067fb47d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138487"
---
# <a name="icordebugheapenum-interface"></a>ICorDebugHeapEnum — Interfejs
Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie. Ten interfejs jest podklasą interfejsu ICorDebugEnum.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md)|Pobiera określoną liczbę wystąpień [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , które zawierają informacje o obiektach na zarządzanym stosie.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorDebugHeapEnum` implementuje interfejs ICorDebugEnum.  
  
 Wystąpienie `ICorDebugHeapEnum` jest wypełniane wystąpieniami [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) przez wywołanie metody [ICorDebugProcess5:: EnumerateHeap —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) . Każde wystąpienie [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) w kolekcji reprezentuje obiekt na żywo na stercie lub obiekt, który nie jest odblokowany przez żaden obiekt, ale nie został jeszcze zebrany przez moduł wyrzucania elementów bezużytecznych. Obiekty [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugHeapEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
