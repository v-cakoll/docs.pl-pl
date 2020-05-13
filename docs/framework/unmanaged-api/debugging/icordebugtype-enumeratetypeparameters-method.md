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
ms.openlocfilehash: dc6bf4f02c49788e640c6e230f864e3ca8e71b0d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380006"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters — Metoda
Pobiera wskaźnik interfejsu do ICorDebugTypeEnum zawierającego <xref:System.Type> Parametry klasy, do której odwołuje się ten ICorDebugType.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppTyParEnum`  
 określoną Wskaźnik na adres `ICorDebugTypeEnum` , który zawiera parametry typu.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `EnumerateTypeParameters` , jeśli wartość CorElementType — zwrócona przez [ICorDebugType:: GetType](icordebugtype-gettype-method.md) ma ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR lub ELEMENT_TYPE_FNPTR. Liczba parametrów i ich kolejność zależy od typu:  
  
- ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE: liczba parametrów typu zawartych w `ICorDebugTypeEnum` tej metodzie, która zwraca wartość, będzie zależeć od liczby parametrów typu formalnego dla odpowiadającej klasy. Na przykład, jeśli typ to, zwróci wartość zawierającą `class Dict<String,int32>` `EnumerateTypeParameters` `ICorDebugTypeEnum` obiekty reprezentujące `String` i `int32` w kolejności.  
  
- ELEMENT_TYPE_FNPTR: liczba parametrów typu zawartych w elemencie `ICorDebugTypeEnum` będzie większa niż liczba argumentów akceptowanych przez funkcję. Pierwszy parametr typu zawarty w elemencie `ICorDebugTypeEnum` jest typem zwracanym dla funkcji, a kolejne parametry typu są parametrami funkcji.  
  
- ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF lub ELEMENT_TYPE_PTR: zostanie zwrócony jeden parametr typu. Na przykład, jeśli typ jest typem tablicowym, na przykład `int32[]` , zwróci `EnumerateTypeParameters` element `ICorDebugTypeEnum` zawierający obiekt reprezentujący `int32` .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
