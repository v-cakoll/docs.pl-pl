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
ms.openlocfilehash: 44093f84ea644757a5f5c73da54ce5bcfa717a4e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728095"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a>ICorDebugProcess5::EnumerateGCReferences — Metoda
Pobiera moduł wyliczający dla wszystkich obiektów, które mają być jesdnostką zbierającą śmieci w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `enumerateWeakReferences`  
 [in] Wartość logiczna wskazująca, czy słabe odwołania są także do wyliczenia. Jeśli `enumerateWeakReferences` jest `true`, `ppEnum` modułu wyliczającego zawiera odwołań do silnych i słabe odwołania. Jeśli `enumerateWeakReferences` jest `false`, moduł wyliczający obejmuje tylko silne odwołania.  
  
 `ppEnum`  
 [out] Wskaźnik na adres [icordebuggcreferenceenum —](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) oznacza to moduł wyliczający dla obiektów jako zebranych elementów bezużytecznych.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zapewnia możliwość określenia pełnego łańcucha umieszczania dla dowolnego obiektu zarządzanego w procesie i może służyć do ustalenia, dlaczego obiekt jest nadal aktywne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugProcess5, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
