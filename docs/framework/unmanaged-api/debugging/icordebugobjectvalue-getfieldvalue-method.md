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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fc65f5b55082970a0cd59a6850aaaa6779d0821
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766409"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue — Metoda
Pobiera wartość określonego pola określonej klasie dla tej wartości obiektu.  
  
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
 [in] Wskaźnik do obiektu "ICorDebugClass", który reprezentuje klasę, dla którego należy pobrać wartości pola.  
  
 `fieldDef`  
 [in] `mdFieldDef` Token, który odwołuje się do metadanych opisujących pola.  
  
 `ppValue`  
 [out] Wskaźnik do obiektu "ICorDebugValue", który reprezentuje wartość określonego pola.  
  
## <a name="remarks"></a>Uwagi  
 Klasa określona w `pClass` parametru musi być w hierarchii klasy wartości obiektu, a pole musi być polem tej klasy.  
  
 `GetFieldValue` Metoda zakończy się powodzeniem dla ogólnych obiektów i klas ogólnych. Na przykład jeśli MyDictionary\<V > dziedziczy ze słownika\<ciągu V >, i wartość obiektu jest typu MyDictionary\<int32 >, przekazując `ICorDebugClass` obiekt słownika\<K, V > będzie pomyślnie pobrać polem słownika\<ciąg, int32 >.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
