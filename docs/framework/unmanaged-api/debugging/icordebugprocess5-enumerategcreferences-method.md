---
title: ICorDebugProcess5::EnumerateGCReferences — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b5f66099eb4b1cb84d9911567cac4255bf20480
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421401"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a>ICorDebugProcess5::EnumerateGCReferences — Metoda
Pobiera moduł wyliczający dla wszystkich obiektów, które mają być zbierane pamięci w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `enumerateWeakReferences`  
 [in] Wartość logiczna wskazująca, czy słabe odwołania są również mają zostać wyliczone. Jeśli `enumerateWeakReferences` jest `true`, `ppEnum` modułu wyliczającego zawiera odwołań silne i słabe odwołania. Jeśli `enumerateWeakReferences` jest `false`, moduł wyliczający zawiera tylko silne odwołania.  
  
 `ppEnum`  
 [out] Wskaźnik do adresu [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) czyli moduł wyliczający dla obiektów być zbierane z pamięci.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zapewnia możliwość określenia całego łańcucha umieszczania na dowolnym obiektem zarządzanym w procesie i może służyć do ustalenia, dlaczego obiektu jest nadal aktywna.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugProcess5, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
