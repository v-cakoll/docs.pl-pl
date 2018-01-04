---
title: "ICorDebugType::GetStaticFieldValue — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetStaticFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a6a7305017c83b539a3d5ec11fa61ccd2af90a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>ICorDebugType::GetStaticFieldValue — Metoda
Pobiera token w ramce stosu określonego wskaźnika interfejsu do obiektu ICorDebugValue, który zawiera wartość pola statycznego odwołuje się określonego pola.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fieldDef`  
 [in] `mdFieldDef` Token, który określa pola statycznego.  
  
 `pFrame`  
 [in] Wskaźnik do ICorDebugFrame, który reprezentuje ramki stosu.  
  
 `ppValue`  
 [out] Wskaźnik do adresu `ICorDebugValue` zawiera wartość pola statycznego.  
  
## <a name="remarks"></a>Uwagi  
 `GetStaticFieldValue` Metoda może być stosowana tylko wtedy, gdy typ jest po elemencie ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, wskazywany przez [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) metody.  
  
 Dla typu nieogólnego, działanie wykonywane przez `GetStaticFieldValue` jest taka sama jak wywołanie [ICorDebugClass::GetStaticFieldValue](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) dla obiektu ICorDebugClass, który jest zwracany przez [ICorDebugType::GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).  
  
 Dla typów ogólnych będzie wartość pola statycznego względem konkretnego wystąpienia. Ponadto jeśli pola statycznego może być względem wątku, kontekst lub domeny aplikacji, ramki stosu pomoże debugera określić poprawną wartość.  
  
## <a name="remarks"></a>Uwagi  
 `GetStaticFieldValue`można użyć tylko w przypadku wywołania `ICorDebugType::GetType` zwraca wartość po elemencie ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
