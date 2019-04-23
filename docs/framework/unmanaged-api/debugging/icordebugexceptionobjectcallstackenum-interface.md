---
title: ICorDebugExceptionObjectCallStackEnum — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 39dffa18-c71b-48c4-b11d-e814631ab1e9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7ed6c04a46a767ed122e54df0695429cf923b8a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126207"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a>ICorDebugExceptionObjectCallStackEnum — Interfejs
Dostarcza moduł wyliczający informacje stosu wywołań, który jest wbudowany w obiekt wyjątku. Ten interfejs jest podklasą icordebugenum — interfejs.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md)|Pobiera określoną liczbę [cordebugexceptionobjectstackframe —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) obiektów, które zawierają informacje o stosie wywołań obiekt wyjątku.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugExceptionObjectCallStackEnum` Interfejsu implementuje interfejs ICorDebugEnum.  
  
 `ICorDebugExceptionObjectCallStackEnum` Wystąpień jest wypełniana przy użyciu [cordebugexceptionobjectstackframe —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) obiektów, wywołując [ICorDebugExceptionObjectValue::EnumerateExceptionCallStack](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) metody. Elementy stosu wywołań w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugExceptionObjectCallStackEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-next-method.md) — metoda  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
