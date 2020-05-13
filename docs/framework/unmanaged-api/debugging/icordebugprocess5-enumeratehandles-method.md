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
ms.openlocfilehash: 291b384d6f0c8c1404b380c653693ec65fcfc960
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213416"
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
 podczas Bitowa kombinacja wartości [CorGCReferenceType](corgcreferencetype-enumeration.md) , która określa typ dojść do uwzględnienia w kolekcji.  
  
 `ppENum`  
 określoną Wskaźnik na adres elementu [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) , który jest modułem wyliczającym dla obiektów, które mają być zbierane jako elementy bezużyteczne.  
  
## <a name="remarks"></a>Uwagi  
 `EnumerateHandles`jest funkcją pomocnika, która obsługuje inspekcję tabeli dojścia. Jest podobna do metody [ICorDebugProcess5:: EnumerateGCReferences —](icordebugprocess5-enumerategcreferences-method.md) , z wyjątkiem tego, że zamiast wypełniania kolekcji [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) wszystkie obiekty, które mają być zbierane jako elementy bezużyteczne, zawiera tylko te obiekty, które mają uchwyty z tabeli uchwytów.  
  
 `types`Parametr określa typy dojść do uwzględnienia w kolekcji. `types`może to być dowolny z następujących trzech elementów członkowskich wyliczenia [CorGCReferenceType](corgcreferencetype-enumeration.md) :  
  
- `CorHandleStrongOnly`(obsługuje tylko silne odwołania).  
  
- `CorHandleWeakOnly`(obsługuje tylko słabe odwołania).  
  
- `CorHandleAll`(wszystkie uchwyty).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Struktury debugowania](debugging-structures.md)
- [Debugowanie](index.md)
