---
title: ICorDebugHandleValue — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugHandleValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHandleValue
helpviewer_keywords:
- ICorDebugHandleValue interface [.NET Framework debugging]
ms.assetid: 66fcd2b8-ac66-414b-83a8-75a925e17772
topic_type:
- apiref
ms.openlocfilehash: 94472e84b73cdffe09505088b1e7fbc20a209bc3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138483"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue — Interfejs

Podklasa elementu ICorDebugReferenceValue, która reprezentuje wartość odniesienia, do której debuger utworzył dojście do wyrzucania elementów bezużytecznych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dispose, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|Zwalnia dojście, do którego odwołuje się ten obiekt `ICorDebugHandleValue` bez jawnego zwalniania wskaźnika interfejsu.|  
|[GetHandleType, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|Pobiera wartość CorDebugHandleType —, która opisuje rodzaj dojścia, do którego odwołuje się ten `ICorDebugHandleValue`.|  
  
## <a name="remarks"></a>Uwagi  
 Obiekt `ICorDebugReferenceValue` jest unieważniony przez przerwanie w trakcie wykonywania debugowanego kodu. `ICorDebugHandleValue` utrzymuje odwołanie poprzez przerwy i kontynuacje, dopóki nie zostanie jawnie wydane.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
