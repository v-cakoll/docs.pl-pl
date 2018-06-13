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
ms.openlocfilehash: 2f2177702c6c5999033d0852a932e52c0725fb8a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422662"
---
# <a name="icordebugprocess5enumeratehandles-method"></a>ICorDebugProcess5::EnumerateHandles — Metoda
Pobiera moduł wyliczający dla obiekt dojść w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
#### <a name="parameters"></a>Parametry  
 `types`  
 [in] Bitowe połączenie [corgcreferencetype —](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wartości, które określają typ dojścia do uwzględnienia w kolekcji.  
  
 `ppENum`  
 [out] Wskaźnik do adresu [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) czyli moduł wyliczający dla obiektów być zbierane z pamięci.  
  
## <a name="remarks"></a>Uwagi  
 `EnumerateHandles` to funkcja pomocnika obsługującą kontroli tabeli dojścia. Jest podobna do [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) metody, z wyjątkiem zamiast wypełnianie [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) kolekcji ze wszystkimi obiektami być zbierane odzyskiwanie go obejmuje tylko te obiekty, które mają uchwyty z tabeli dojścia.  
  
 `types` Parametr określa typ dojścia do uwzględnienia w kolekcji. `types` Możesz użyć dowolnej z następujących trzech elementów członkowskich [corgcreferencetype —](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wyliczenie:  
  
-   `CorHandleStrongOnly` (dojść tylko silne odwołania).  
  
-   `CorHandleWeakOnly` (dojść tylko słabego odwołania).  
  
-   `CorHandleAll` (wszystkie dojścia).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
