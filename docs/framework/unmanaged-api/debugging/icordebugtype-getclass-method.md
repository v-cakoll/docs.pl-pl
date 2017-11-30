---
title: "ICorDebugType::GetClass — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: be9999cd0dd8db5439dd41e51429841666597b16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypegetclass-method"></a>ICorDebugType::GetClass — Metoda
Pobiera wskaźnika interfejsu do ICorDebugClass, który reprezentuje bez wystąpień typu ogólnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppClass`  
 [out] Wskaźnik do adresu `ICorDebugClass` interfejs, który reprezentuje bez wystąpień typu ogólnego.  
  
## <a name="remarks"></a>Uwagi  
 `GetClass`może zostać wywołany tylko w niektórych warunkach. Wywołanie [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) przed wywołaniem `GetClass`. Jeśli `ICorDebugType::GetType` zwraca wartość CorElementType po elemencie ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, `GetClass` można wywołać w celu uzyskania bez wystąpień typu dla typu ogólnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
