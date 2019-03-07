---
title: ICorDebugProcess5::EnumerateHandles — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHandles
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d031754c22a62cb8d37cd5f591619d985773727
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498864"
---
# <a name="icordebugprocess5enumeratehandles-method"></a>ICorDebugProcess5::EnumerateHandles — Metoda
Pobiera moduł wyliczający dla obiektu uchwytów w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a>Parametry  
 `types`  
 [in] Bitowa kombinacja [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wartości, które określa typ dojścia do uwzględnienia w kolekcji.  
  
 `ppENum`  
 [out] Wskaźnik na adres [icordebuggcreferenceenum —](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) oznacza to moduł wyliczający dla obiektów jako zebranych elementów bezużytecznych.  
  
## <a name="remarks"></a>Uwagi  
 `EnumerateHandles` jest funkcja pomocnicza, która obsługuje inspekcji tabelę uchwytów. Jest on podobny do [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) metody, chyba że zamiast wypełnianie [icordebuggcreferenceenum —](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) kolekcji ze wszystkimi obiektami jako zebranych elementów bezużytecznych go zawiera tylko te obiekty, które mają dojścia stałe od tabelę uchwytów.  
  
 `types` Parametr określa typ dojścia do uwzględnienia w kolekcji. `types` może być dowolną z następujących trzech członków [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wyliczenia:  
  
-   `CorHandleStrongOnly` (obsługuje tylko silne odwołania).  
  
-   `CorHandleWeakOnly` (obsługuje wyłącznie słabe odwołania).  
  
-   `CorHandleAll` (wszystkie uchwyty).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
