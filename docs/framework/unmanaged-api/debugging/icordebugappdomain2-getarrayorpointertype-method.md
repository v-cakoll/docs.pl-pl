---
title: ICorDebugAppDomain2::GetArrayOrPointerType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetArrayOrPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type:
- apiref
ms.openlocfilehash: bbf43f3936823b9a8e562cb32cfa2eef08840033
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895187"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType — Metoda
Pobiera tablicę określonego typu lub wskaźnik lub odwołanie do określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `elementType`  
 podczas Wartość wyliczenia CorElementType —, która określa odpowiedni typ natywny (tablicę, wskaźnik lub odwołanie), który ma zostać utworzony.  
  
 `nRank`  
 podczas Ranga (czyli liczba wymiarów) tablicy. Ta wartość musi być równa `elementType` 0, jeśli określa wskaźnik lub typ referencyjny.  
  
 `pTypeArg`  
 podczas Wskaźnik do obiektu ICorDebugType, który reprezentuje typ tablicy, wskaźnika lub odwołania, które mają zostać utworzone.  
  
 `ppType`  
 określoną Wskaźnik do adresu `ICorDebugType` obiektu, który reprezentuje skonstruowaną tablicę, typ wskaźnika lub typ referencyjny.  
  
## <a name="remarks"></a>Uwagi  
 Wartość *elementu ElementType* musi być jedną z następujących wartości:  
  
- ELEMENT_TYPE_PTR  
  
- ELEMENT_TYPE_BYREF  
  
- ELEMENT_TYPE_ARRAY lub ELEMENT_TYPE_SZARRAY  
  
 Jeśli wartość *elementu ElementType* jest ELEMENT_TYPE_PTR lub ELEMENT_TYPE_BYREF, *nRank* musi mieć wartość zero.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
