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
ms.openlocfilehash: a97c14d83f99c847bb8569a33e175ab6eb5bccd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178620"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a>ICorDebugProcess5::EnumerateGCReferences — Metoda
Pobiera moduł wyliczania dla wszystkich obiektów, które mają być zbierane śmieci w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `enumerateWeakReferences`  
 [w] Wartość logiczna, która wskazuje, czy słabe odwołania mają być również wyliczone. Jeśli `enumerateWeakReferences` `true`jest `ppEnum` , wyliczacz zawiera zarówno silne odwołania i słabe odwołania. Jeśli `enumerateWeakReferences` `false`jest , wyliczacz zawiera tylko silne odwołania.  
  
 `ppEnum`  
 [na zewnątrz] Wskaźnik do adresu [ICorDebugGCReferenceEnum,](icordebuggcreferenceenum-interface.md) który jest modułem wyliczacza dla obiektów, które mają być zbierane przez śmieci.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda umożliwia określenie pełnego łańcucha rootowania dla dowolnego obiektu zarządzanego w procesie i może służyć do określenia, dlaczego obiekt jest nadal żywy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugProcess5, interfejs](icordebugprocess5-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
