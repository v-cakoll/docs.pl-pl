---
title: ICorDebugCode4, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugCode4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4
helpviewer_keywords:
- ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type:
- apiref
ms.openlocfilehash: 373df8a47bdcbc833ffaea05bb205a63b5f583ec
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777771"
---
# <a name="icordebugcode4-interface"></a>ICorDebugCode4, interfejs
Zapewnia metodę, która umożliwia debugerowi Wyliczenie zmiennych lokalnych i argumentów w funkcji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateVariableHomes, metoda](icordebugcode4-enumeratevariablehomes-method.md)|Pobiera moduł wyliczający do zmiennych lokalnych i argumentów w funkcji.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugCode3, interfejs](icordebugcode3-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
