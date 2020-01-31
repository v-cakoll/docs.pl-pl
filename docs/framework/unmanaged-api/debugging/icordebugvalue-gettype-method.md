---
title: ICorDebugValue::GetType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
ms.openlocfilehash: 7def2bd2c0f3ab501fdb918a0e9a7ee154159b78
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791156"
---
# <a name="icordebugvaluegettype-method"></a>ICorDebugValue::GetType — Metoda
Pobiera typ pierwotny tego obiektu "ICorDebugValue".  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pType`  
 określoną Wskaźnik do wartości wyliczenia "CorElementType —", która wskazuje typ wartości.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli obiekt jest złożonym typem czasu wykonywania, ten typ może być badany za pomocą odpowiednich podklas interfejsu `ICorDebugValue`. Na przykład "ICorDebugObjectValue", który dziedziczy z `ICorDebugValue`, reprezentuje typ złożony.  
  
 Metody `GetType` i [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) każda zwracają informacje o typie wartości. Są one zastępowane przez metodę [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md) z uwzględnieniem typów ogólnych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
