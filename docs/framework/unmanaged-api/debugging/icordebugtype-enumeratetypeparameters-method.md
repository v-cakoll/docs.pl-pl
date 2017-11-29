---
title: "ICorDebugType::EnumerateTypeParameters — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.EnumerateTypeParameters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e9dd00b0a5f28821112621a54c97551c71e1acc6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters — Metoda
Pobiera wskaźnika interfejsu do ICorDebugTypeEnum, który zawiera <xref:System.Type> parametry odwołuje się ten ICorDebugType klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppTyParEnum`  
 [out] Wskaźnik do adresu `ICorDebugTypeEnum` zawiera parametry typu.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `EnumerateTypeParameters` Jeśli CorElementType wartość zwracana przez [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) po elemencie ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, element ELEMENT_TYPE_ PTR lub ELEMENT_TYPE_FNPTR. Liczba parametrów i ich kolejność, zależy od typu:  
  
-   Po elemencie ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE: liczba parametrów typu zawartych w `ICorDebugTypeEnum` ta metoda zwraca, zależy od liczby parametrów typu formalnego dla odpowiedniej klasy. Na przykład, jeśli typ jest `class Dict<String,int32>`, następnie `EnumerateTypeParameters` zwróci `ICorDebugTypeEnum` zawierający obiekty reprezentujące `String` i `int32` w sekwencji.  
  
-   ELEMENT_TYPE_FNPTR: Liczba parametrów typu zawartych w `ICorDebugTypeEnum` będzie jeden większa niż liczba argumentów akceptowanych przez funkcję. Pierwszy parametr typu zawartych w `ICorDebugTypeEnum` jest typ zwracany funkcji i parametrów typu kolejne parametry funkcji.  
  
-   ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF lub poprawności elementu ELEMENT_TYPE_PTR: zostanie zwrócony jeden parametr typu. Na przykład, jeśli typ jest typem tablicowym `int32[]`,`EnumerateTypeParameters` zwróci `ICorDebugTypeEnum` zawiera obiekt reprezentujący `int32`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
