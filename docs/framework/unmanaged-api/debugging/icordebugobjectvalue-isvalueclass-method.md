---
title: ICorDebugObjectValue::IsValueClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.IsValueClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::IsValueClass
helpviewer_keywords:
- ICorDebugObjectValue::IsValueClass method [.NET Framework debugging]
- IsValueClass method [.NET Framework debugging]
ms.assetid: 13d89a4a-5d9d-4a79-9600-5e2a98c3d166
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 932d4ecbf34a636d37a60af0ba11f3fc149ffcea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649651"
---
# <a name="icordebugobjectvalueisvalueclass-method"></a>ICorDebugObjectValue::IsValueClass — Metoda
Pobiera wartość wskazującą, czy wartość tego obiektu jest typem wartości.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsValueClass (  
    [out] BOOL               *pbIsValueClass  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbIsValueClass`  
 [out] Wskaźnik na wartość logiczną, która jest `true` Jeśli wartość obiektu reprezentowanego przez ten "ICorDebugObjectValue", jest typem wartości, a nie typu referencyjnego; w przeciwnym razie `pbIsValueClass` jest `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także


