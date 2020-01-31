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
ms.openlocfilehash: 9d98bccdfb83cec547b185693c28f25017d3225f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782800"
---
# <a name="icordebugexceptionobjectcallstackenum-interface"></a>ICorDebugExceptionObjectCallStackEnum — Interfejs
Dostarcza moduł wyliczający informacje stosu wywołań, który jest wbudowany w obiekt wyjątku. Ten interfejs jest podklasą interfejsu ICorDebugEnum.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ICorDebugExceptionObjectCallStackEnum:: Next](icordebugexceptionobjectcallstackenum-next-method.md)|Pobiera określoną liczbę obiektów [CorDebugExceptionObjectStackFrame —](cordebugexceptionobjectstackframe-structure.md) , które zawierają informacje o stosie wywołań obiektu wyjątku.|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `ICorDebugExceptionObjectCallStackEnum` implementuje interfejs ICorDebugEnum.  
  
 Wystąpienie `ICorDebugExceptionObjectCallStackEnum` jest wypełniane obiektami [CorDebugExceptionObjectStackFrame —](cordebugexceptionobjectstackframe-structure.md) przez wywołanie metody [ICorDebugExceptionObjectValue:: EnumerateExceptionCallStack —](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md) . Elementy stosu wywołań w kolekcji mogą być wyliczane przez wywołanie metody [ICorDebugExceptionObjectCallStackEnum:: Next](icordebugexceptionobjectcallstackenum-next-method.md)  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
