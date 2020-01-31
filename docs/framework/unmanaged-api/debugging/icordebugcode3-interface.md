---
title: ICorDebugCode3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
ms.openlocfilehash: f2f75c3c54c0fa2d55dc0179c05e4edea6e36738
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777828"
---
# <a name="icordebugcode3-interface"></a>ICorDebugCode3 — Interfejs
Zapewnia metodę, która rozszerza wartości "ICorDebugCode" i "ICorDebugCode2", aby podać informacje o zarządzanej zwracanej wartość.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetReturnValueLiveOffset, metoda](icordebugcode3-getreturnvalueliveoffset-method.md)|W przypadku określonego przesunięcia IL pobiera natywne przesunięcia, w których powinien być umieszczony punkt przerwania, aby debuger mógł uzyskać wartość zwracaną z funkcji.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugILFrame3, interfejs](icordebugilframe3-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
