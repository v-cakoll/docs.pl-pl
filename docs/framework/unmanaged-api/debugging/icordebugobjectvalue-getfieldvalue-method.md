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
ms.openlocfilehash: 72a504d23b7b15ad3de72995a632843874cc7c5f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631774"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue — Metoda
Pobiera wartość określonego pola określonej klasie dla tej wartości obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
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


