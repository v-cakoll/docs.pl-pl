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
ms.openlocfilehash: d5962de8cc2762f6ecf4864c5255da0fe83918e4
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396533"
---
# <a name="icordebugvariablehomeenum-interface"></a>ICorDebugVariableHomeEnum, interfejs
Dostarcza moduł wyliczający do zmiennych lokalnych i argumentów w funkcji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next — Metoda](icordebugvariablehomeenum-next-method.md)|Pobiera określoną liczbę wystąpień [ICorDebugVariableHome](icordebugvariablehome-interface.md) , które zawierają informacje o zmiennych lokalnych i argumentach w funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugVariableHomeEnum`Interfejs implementuje interfejs ICorDebugEnum.  
  
 `ICorDebugVariableHomeEnum`Wystąpienie jest wypełniane wystąpieniami [ICorDebugVariableHome](icordebugvariablehome-interface.md) przez wywołanie metody [ICorDebugCode4:: EnumerateVariableHomes](icordebugcode4-enumeratevariablehomes-method.md) . Każde wystąpienie [ICorDebugVariableHome](icordebugvariablehome-interface.md) w kolekcji reprezentuje zmienną lokalną lub argument w funkcji. Obiekty [ICorDebugVariableHome](icordebugvariablehome-interface.md) w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugVariableHomeEnum:: Next](icordebugvariablehomeenum-next-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugVariableHome, interfejs](icordebugvariablehome-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
