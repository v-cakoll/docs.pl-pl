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
ms.openlocfilehash: 660bc13e8109994f59444c0adebbc97f54de0b43
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207592"
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
 podczas `mdFieldDef`Token, który odwołuje się do metadanych opisujących pole.  
  
 `ppValue`  
 określoną Wskaźnik do obiektu "ICorDebugValue", który reprezentuje wartość określonego pola.  
  
## <a name="remarks"></a>Uwagi  
 Klasa określona w `pClass` parametrze musi znajdować się w hierarchii klasy wartości obiektu, a pole musi być polem tej klasy.  
  
 `GetFieldValue`Metoda będzie nadal powiodła się dla obiektów ogólnych i klas ogólnych. Na przykład jeśli program webdictionary \<> dziedziczy od ciągu słownika \< ,> v, a wartość obiektu jest typu, \< Int32 słownika>, przekazanie `ICorDebugClass` obiektu dla słownika \< K, a program V> pomyślnie pobierze pole \< ciągu słownika, Int32>.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też
