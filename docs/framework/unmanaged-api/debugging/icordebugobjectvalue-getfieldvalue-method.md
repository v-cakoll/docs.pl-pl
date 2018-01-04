---
title: "ICorDebugObjectValue::GetFieldValue — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue.GetFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9fcf53610cf96ef1ab62b4768521e8a2fb7ee6c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue — Metoda
Pobiera wartość określonego pola określonej klasy wartość tego obiektu.  
  
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
 [in] Wskaźnik do obiektu "ICorDebugClass", który reprezentuje klasę, dla którego można pobrać wartości pola.  
  
 `fieldDef`  
 [in] `mdFieldDef` Token, który odwołuje się do metadanych zawierająca opis w polu.  
  
 `ppValue`  
 [out] Wskaźnik do obiektu "ICorDebugValue", który reprezentuje wartość określonego pola.  
  
## <a name="remarks"></a>Uwagi  
 Klasa określona w `pClass` parametru musi być w hierarchii klasy wartość obiektu, a pola musi należeć do tej klasy.  
  
 `GetFieldValue` Metody nadal się powieść ogólnego obiekty i klasy ogólne. Na przykład jeśli MyDictionary\<V > dziedziczy ze słownika\<ciąg znaków, V >, i wartość do obiektu jest typu MyDictionary\<int32 >, przechodzącą `ICorDebugClass` obiekt słownika\<K, V > zostanie pomyślnie Pobierz pole słownika\<ciąg, int32 >.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
    
 
