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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd68df77adafb8b21e7684b28fe978722ca37e16
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736792"
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
 [out] Wskaźnik na adres `ICorDebugClass` interfejs, który reprezentuje typ ogólny bez wystąpień.  
  
## <a name="remarks"></a>Uwagi  
 `GetClass` może być wywoływana tylko w określonych warunkach. Wywołaj [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) przed wywołaniem `GetClass`. Jeśli `ICorDebugType::GetType` zwraca wartość corelementtype — ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, `GetClass` może być wywoływana w celu uzyskania bez wystąpień typu dla typu ogólnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
