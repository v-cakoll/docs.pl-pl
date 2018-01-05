---
title: "ICorDebugValue::GetType — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue.GetType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a79ef332361fdaa3a23cc4e13daa8b4a8303d2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluegettype-method"></a>ICorDebugValue::GetType — Metoda
Pobiera pierwotny typ obiektu "ICorDebugValue".  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pType`  
 [out] Wskaźnik do wartości wyliczenia "CorElementType", który wskazuje typ tej wartości.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli obiekt jest typem złożonym czasu wykonywania, tego typu mogą być zbadane za pomocą odpowiednich podklasy `ICorDebugValue` interfejsu. Na przykład "ICorDebugObjectValue", która dziedziczy od `ICorDebugValue`, reprezentuje typ złożony.  
  
 `GetType` i [ICorDebugObjectValue::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) metody każdego zwracają informacje o typie wartości. Zostały one zarówno zastąpione ogólne aware [ICorDebugValue2::GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 
