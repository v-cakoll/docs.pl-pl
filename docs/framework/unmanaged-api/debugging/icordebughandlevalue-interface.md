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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6dddc1665dff5c1a0629d25aa99066ce6eeca94a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981442"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue — Interfejs

Podklasa klasy ICorDebugReferenceValue, która reprezentuje wartość odniesienia, do której debuger utworzył procedurę obsługi do wyrzucania elementów bezużytecznych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Dispose, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-dispose-method.md)|Zwalnia dojście przywoływane przez to `ICorDebugHandleValue` obiektu bez jawnie zwalniania wskaźnika interfejsu.|  
|[GetHandleType, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-gethandletype-method.md)|Pobiera wartość cordebughandletype —, która opisuje typ dojścia przywoływane przez to `ICorDebugHandleValue`.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugReferenceValue` Obiektu zostaje unieważniony przez przerwy podczas wykonywania debugowanego kodu. `ICorDebugHandleValue` Przechowuje swoje odwołanie do podziału i kontynuacji, do jego jawnego zwolnienia.  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
