---
title: ICorDebugType::GetClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: 3a895f432ed640cc35a492df0c91cece34893062
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122366"
---
# <a name="icordebugtypegetclass-method"></a>ICorDebugType::GetClass — Metoda
Pobiera wskaźnik interfejsu do ICorDebugClass, który reprezentuje typ ogólny bez wystąpień.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppClass`  
 określoną Wskaźnik do adresu interfejsu `ICorDebugClass`, który reprezentuje typ ogólny bez wystąpień.  
  
## <a name="remarks"></a>Uwagi  
 `GetClass` można wywołać tylko w określonych warunkach. Wywołaj metodę [ICorDebugType:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) przed wywołaniem `GetClass`. Jeśli `ICorDebugType::GetType` zwraca wartość CorElementType —, która jest ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, można wywołać `GetClass`, aby uzyskać typ nieskonkretyzowany dla typu ogólnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
