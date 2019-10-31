---
title: ICorDebugObjectValue::GetFieldValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type:
- apiref
ms.openlocfilehash: 002c6cccb3ddf29b831ba5e14baa5e51f1b82433
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095878"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue — Metoda
Pobiera wartość określonego pola określonej klasy dla tej wartości obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pClass`  
 podczas Wskaźnik do obiektu "ICorDebugClass", który reprezentuje klasę, dla której ma zostać pobrana wartość pola.  
  
 `fieldDef`  
 podczas Token `mdFieldDef`, który odwołuje się do metadanych opisujących pole.  
  
 `ppValue`  
 określoną Wskaźnik do obiektu "ICorDebugValue", który reprezentuje wartość określonego pola.  
  
## <a name="remarks"></a>Uwagi  
 Klasa określona w parametrze `pClass` musi znajdować się w hierarchii klasy wartości obiektu, a pole musi być polem tej klasy.  
  
 Metoda `GetFieldValue` nadal powiedzie się dla obiektów ogólnych i klas ogólnych. Na przykład, jeśli program webdictionary\<V > dziedziczy ze słownika\<String, V >, a wartość obiektu to typu webdictionary\<Int32 >, przekazanie obiektu `ICorDebugClass` dla słownika\<K, >\<słownika, ciąg Int32 >.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
