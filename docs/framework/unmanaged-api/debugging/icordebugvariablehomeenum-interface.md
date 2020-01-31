---
title: ICorDebugVariableHomeEnum, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum
helpviewer_keywords:
- ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: c312ae6d-c8dc-48d6-9f1e-ead515c88fdf
topic_type:
- apiref
ms.openlocfilehash: 74b3c7bed54f3735efbd5d2c56962d427518f71a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790949"
---
# <a name="icordebugvariablehomeenum-interface"></a>ICorDebugVariableHomeEnum, interfejs
Dostarcza moduł wyliczający do zmiennych lokalnych i argumentów w funkcji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next, metoda](icordebugvariablehomeenum-next-method.md)|Pobiera określoną liczbę wystąpień [ICorDebugVariableHome](icordebugvariablehome-interface.md) , które zawierają informacje o zmiennych lokalnych i argumentach w funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorDebugVariableHomeEnum` implementuje interfejs ICorDebugEnum.  
  
 Wystąpienie `ICorDebugVariableHomeEnum` jest wypełniane wystąpieniami [ICorDebugVariableHome](icordebugvariablehome-interface.md) przez wywołanie metody [ICorDebugCode4:: EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) . Każde wystąpienie [ICorDebugVariableHome](icordebugvariablehome-interface.md) w kolekcji reprezentuje zmienną lokalną lub argument w funkcji. Obiekty [ICorDebugVariableHome](icordebugvariablehome-interface.md) w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugVariableHomeEnum:: Next](icordebugvariablehomeenum-next-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugVariableHome, interfejs](icordebugvariablehome-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
