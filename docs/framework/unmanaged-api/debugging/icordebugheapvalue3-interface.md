---
title: ICorDebugHeapValue3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3
helpviewer_keywords:
- ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08a9bc8aa4aa70ad6b01c58abccd145ae43d8a52
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568299"
---
# <a name="icordebugheapvalue3-interface"></a>ICorDebugHeapValue3 — Interfejs
Udostępnia właściwości blokady monitora obiektów. Ten interfejs rozszerza ICorDebugHeapValue i icordebugheapvalue2 — interfejsy.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetThreadOwningMonitorLock, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|Zwraca wątków zarządzanych, który jest właścicielem blokady monitora dla tego obiektu.|  
|[GetMonitorEventWaitList, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|Udostępnia uporządkowaną listę wątków, które są umieszczane w kolejce na zdarzenia skojarzonego z blokadą monitora.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
