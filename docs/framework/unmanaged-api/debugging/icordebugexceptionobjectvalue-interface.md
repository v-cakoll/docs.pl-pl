---
title: ICorDebugExceptionObjectValue — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectValue
helpviewer_keywords:
- ICorDebugExceptionObjectValue interface [.NET Framework debugging]
ms.assetid: 43416dd5-8892-4106-9f59-f9143b19ddb4
topic_type:
- apiref
ms.openlocfilehash: fa154d0bb48f4ecd4fc6a50ce22fd13c592b7c40
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782735"
---
# <a name="icordebugexceptionobjectvalue-interface"></a>ICorDebugExceptionObjectValue — Interfejs
Rozszerza interfejs "ICorDebugObjectValue", aby dostarczyć informacje o śledzeniu stosu z obiektu wyjątku zarządzanego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumerateExceptionCallStack, metoda](icordebugexceptionobjectvalue-enumerateexceptioncallstack-method.md)|Pobiera moduł wyliczający w stosie wywołań osadzonym w obiekcie wyjątku.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie `QueryInterface` powiedzie się dla zarządzanych obiektów, które pochodzą z <xref:System.Exception?displayProperty=nameWithType>.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
