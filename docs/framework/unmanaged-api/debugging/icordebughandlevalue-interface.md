---
title: ICorDebugHandleValue, interfejs
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
ms.openlocfilehash: 9a9eb63e681b47f058901b0ff002015baffe6048
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775677"
---
# <a name="icordebughandlevalue-interface"></a>ICorDebugHandleValue, interfejs

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
