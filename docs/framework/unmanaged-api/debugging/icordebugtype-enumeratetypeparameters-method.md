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
ms.openlocfilehash: b2c381d093069f5ee86be1b19d75f5c2d69ad9fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791309"
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a>ICorDebugType::EnumerateTypeParameters — Metoda
Pobiera wskaźnik interfejsu do ICorDebugTypeEnum, który zawiera <xref:System.Type> parametry klasy, do których odwołuje się ten ICorDebugType.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppTyParEnum`  
 określoną Wskaźnik do adresu `ICorDebugTypeEnum`, który zawiera parametry typu.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć `EnumerateTypeParameters`, jeśli wartość CorElementType — zwracana przez [ICorDebugType:: GetType](icordebugtype-gettype-method.md) to ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR lub ELEMENT_TYPE_FNPTR. Liczba parametrów i ich kolejność zależy od typu:  
  
- ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE: liczba parametrów typu zawartych w `ICorDebugTypeEnum`, które ta metoda zwraca, będzie zależeć od liczby parametrów typu formalnego dla odpowiadającej klasy. Na przykład, jeśli typ to `class Dict<String,int32>`, wówczas `EnumerateTypeParameters` zwróci `ICorDebugTypeEnum`, który zawiera obiekty reprezentujące `String` i `int32` w sekwencji.  
  
- ELEMENT_TYPE_FNPTR: liczba parametrów typu zawartych w `ICorDebugTypeEnum` będzie większa niż liczba argumentów akceptowanych przez funkcję. Pierwszy parametr typu zawarty w `ICorDebugTypeEnum` jest typem zwracanym dla funkcji, a kolejne parametry typu są parametrami funkcji.  
  
- ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF lub ELEMENT_TYPE_PTR: zostanie zwrócony jeden parametr typu. Na przykład, jeśli typ jest typem tablicy, takim jak `int32[]`,`EnumerateTypeParameters` zwróci `ICorDebugTypeEnum`, który zawiera obiekt reprezentujący `int32`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
