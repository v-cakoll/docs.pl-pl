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
ms.openlocfilehash: a3cd62384ad87d072cd715d23d0e9ee9dac23270
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396740"
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
 Jeśli obiekt jest złożonym typem czasu wykonywania, ten typ może być badany za pomocą odpowiednich podklas `ICorDebugValue` interfejsu. Na przykład "ICorDebugObjectValue", który dziedziczy po `ICorDebugValue` , reprezentuje typ złożony.  
  
 `GetType`Metody i [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) każda zwracają informacje o typie wartości. Są one zastępowane przez metodę [ICorDebugValue2:: GetExactType](icordebugvalue2-getexacttype-method.md) z uwzględnieniem typów ogólnych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
