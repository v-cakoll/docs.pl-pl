---
title: ICorDebugVariableHomeEnum Interface
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43f63e09c654c7aab9f1da0db7587a92bee4fb79
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632039"
---
# <a name="icordebugvariablehomeenum-interface"></a>ICorDebugVariableHomeEnum Interface
Dostarcza moduł wyliczający do zmiennych lokalnych i argumenty w funkcji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Next, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)|Pobiera określoną liczbę [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpień, które zawierają informacje dotyczące zmiennych lokalnych i argumenty w funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugVariableHomeEnum` Interfejsu implementuje interfejs ICorDebugEnum.  
  
 `ICorDebugVariableHomeEnum` Wystąpień jest wypełniana przy użyciu [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpień, wywołując [ICorDebugCode4::EnumerateVariableHomes](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md) metody. Każdy [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) reprezentuje wystąpienie w kolekcji, zmienna lokalna lub argumentu dla funkcji. [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektów w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugVariableHome, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
