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
ms.openlocfilehash: e0e68dba1f4d9ac5fa618aa842b823dcc046e70e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129682"
---
# <a name="icordebugprocess5enumeratehandles-method"></a>ICorDebugProcess5::EnumerateHandles — Metoda
Pobiera moduł wyliczający dla dojść do obiektów w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a>Parametry  
 `types`  
 podczas Bitowa kombinacja wartości [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) , która określa typ dojść do uwzględnienia w kolekcji.  
  
 `ppENum`  
 określoną Wskaźnik na adres elementu [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) , który jest modułem wyliczającym dla obiektów, które mają być zbierane jako elementy bezużyteczne.  
  
## <a name="remarks"></a>Uwagi  
 `EnumerateHandles` jest funkcją pomocnika, która obsługuje inspekcję tabeli dojścia. Jest podobna do metody [ICorDebugProcess5:: EnumerateGCReferences —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) , z wyjątkiem tego, że zamiast wypełniania kolekcji [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) ze wszystkimi obiektami, które mają być zbierane jako elementy bezużyteczne, zawiera tylko te obiekty, które mają uchwyty tabela dojścia.  
  
 `types` parametr określa typy dojść do uwzględnienia w kolekcji. `types` może być jednym z trzech następujących elementów członkowskich wyliczenia [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) :  
  
- `CorHandleStrongOnly` (obsługuje tylko silne odwołania).  
  
- `CorHandleWeakOnly` (obsługuje tylko słabe odwołania).  
  
- `CorHandleAll` (wszystkie uchwyty).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
