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
ms.openlocfilehash: bed2871c46712490bc4b0520fa1ab8023dbab5cf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794424"
---
# <a name="icordebugheapenum-interface"></a>ICorDebugHeapEnum — Interfejs
Dostarcza moduł wyliczający dla obiektów na zarządzanej stercie. Ten interfejs jest podklasą interfejsu ICorDebugEnum.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next, metoda](icordebugheapenum-next-method.md)|Pobiera określoną liczbę wystąpień [COR_HEAPOBJECT](cor-heapobject-structure.md) , które zawierają informacje o obiektach na zarządzanym stosie.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorDebugHeapEnum` implementuje interfejs ICorDebugEnum.  
  
 Wystąpienie `ICorDebugHeapEnum` jest wypełniane wystąpieniami [COR_HEAPOBJECT](cor-heapobject-structure.md) przez wywołanie metody [ICorDebugProcess5:: EnumerateHeap —](icordebugprocess5-enumerateheap-method.md) . Każde wystąpienie [COR_HEAPOBJECT](cor-heapobject-structure.md) w kolekcji reprezentuje obiekt na żywo na stercie lub obiekt, który nie jest odblokowany przez żaden obiekt, ale nie został jeszcze zebrany przez moduł wyrzucania elementów bezużytecznych. [COR_HEAPOBJECT](cor-heapobject-structure.md) obiektów w kolekcji można wyliczyć, wywołując metodę [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
