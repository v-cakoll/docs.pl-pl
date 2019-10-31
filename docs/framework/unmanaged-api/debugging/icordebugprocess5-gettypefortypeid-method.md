---
title: ICorDebugProcess5::GetTypeForTypeID — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
ms.openlocfilehash: 39f5c1813b08f4d72c610820b1434e29eb4aec8e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121273"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a>ICorDebugProcess5::GetTypeForTypeID — Metoda
Konwertuje identyfikator typu na wartość ICorDebugType.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 podczas Identyfikator typu.  
  
 `ppType`  
 określoną Wskaźnik do adresu obiektu ICorDebugType.  
  
## <a name="remarks"></a>Uwagi  
 W niektórych przypadkach metody, które zwracają identyfikator typu, mogą zwracać wartość null `COR_TYPEID`. Jeśli ta wartość jest przenoszona jako argument `id`, Metoda `GetTypeForTypeID` zakończy się niepowodzeniem i zwróci `E_FAIL`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugProcess5, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
