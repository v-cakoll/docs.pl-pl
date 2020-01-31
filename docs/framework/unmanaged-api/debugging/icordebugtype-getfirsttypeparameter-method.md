---
title: ICorDebugType::GetFirstTypeParameter — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
ms.openlocfilehash: 1a02190b595fb01bdc2df46182bfa64bfe638db4
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791289"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a>ICorDebugType::GetFirstTypeParameter — Metoda
Pobiera wskaźnik interfejsu do ICorDebugType, który reprezentuje pierwszy parametr <xref:System.Type> typu reprezentowanego przez ten `ICorDebugType`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `value`  
 określoną Wskaźnik do adresu obiektu `ICorDebugType`, który reprezentuje pierwszy parametr.  
  
## <a name="remarks"></a>Uwagi  
 `GetFirstTypeParameter` można wywołać w przypadkach, gdy dodatkowe informacje o typie obejmują, co najwyżej jeden parametr typu. W szczególności można go użyć, jeśli typ jest ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF lub ELEMENT_TYPE_PTR, zgodnie z opisem przez metodę [ICorDebugType:: GetType](icordebugtype-gettype-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
