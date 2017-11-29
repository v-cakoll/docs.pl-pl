---
title: "ICorDebugProcess5::EnumerateHandles — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHandles
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5377f4ce0571cdb1de6c338f4bbb87d6a589aaf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 `EnumerateHandles`to funkcja pomocnika obsługującą kontroli tabeli dojścia. Jest podobna do [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) metody, z wyjątkiem zamiast wypełnianie [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) kolekcji ze wszystkimi obiektami być zbierane odzyskiwanie go obejmuje tylko te obiekty, które mają uchwyty z tabeli dojścia.  
  
 `types` Parametr określa typ dojścia do uwzględnienia w kolekcji. `types`Możesz użyć dowolnej z następujących trzech elementów członkowskich [corgcreferencetype —](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) wyliczenie:  
  
-   `CorHandleStrongOnly`(dojść tylko silne odwołania).  
  
-   `CorHandleWeakOnly`(dojść tylko słabego odwołania).  
  
-   `CorHandleAll`(wszystkie dojścia).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
