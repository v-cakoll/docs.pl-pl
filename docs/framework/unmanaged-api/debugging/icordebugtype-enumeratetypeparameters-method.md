---
title: ICorDebugType::EnumerateTypeParameters — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.EnumerateTypeParameters
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16cf17d43fcad3c4f7a710678bbdc056f840eaca
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736808"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters — Metoda
Pobiera wskaźnik interfejsu do icordebugtypeenum —, który zawiera <xref:System.Type> parametrów klasy odwołuje się ten ICorDebugType.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppTyParEnum`  
 [out] Wskaźnik na adres `ICorDebugTypeEnum` zawierający parametry typu.  
  
## <a name="remarks"></a>Uwagi  
 Możesz użyć `EnumerateTypeParameters` Jeśli corelementtype — wartość zwracana przez [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) jest ELEMENT_TYPE_CLASS ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, pole, element ELEMENT_TYPE_ PTR lub ELEMENT_TYPE_FNPTR. Liczba parametrów i ich kolejność, zależy od typu:  
  
- ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE: Liczba parametrów typu zawarte w `ICorDebugTypeEnum` , ta metoda zwraca, będzie zależeć od liczby parametrów formalnych typu dla odpowiedniej klasy. Na przykład, jeśli typ jest `class Dict<String,int32>`, następnie `EnumerateTypeParameters` zwróci `ICorDebugTypeEnum` zawierający obiekty reprezentujące `String` i `int32` w sekwencji.  
  
- ELEMENT_TYPE_FNPTR: Liczba parametrów typu zawarte w `ICorDebugTypeEnum` będzie jedną większa niż liczba argumentów akceptowanych przez funkcję. Pierwszy parametr typu zawarte w `ICorDebugTypeEnum` jest typ zwracany dla funkcji i parametrów typu kolejne parametry funkcji.  
  
- ELEMENT_TYPE_ARRAY ELEMENT_TYPE_SZARRAY, pole lub ELEMENT_TYPE_PTR: Zostanie zwrócony jeden parametr typu. Na przykład, jeśli typ jest typem tablicowym `int32[]`,`EnumerateTypeParameters` zwróci `ICorDebugTypeEnum` zawiera obiekt reprezentujący `int32`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
