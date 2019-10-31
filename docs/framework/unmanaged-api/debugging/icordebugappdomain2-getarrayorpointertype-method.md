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
ms.openlocfilehash: 166f6bb50849df8550871958d7034fdf2a841abb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089113"
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
 podczas Ranga (czyli liczba wymiarów) tablicy. Ta wartość musi być równa 0, jeśli `elementType` określa wskaźnik lub typ referencyjny.  
  
 `pTypeArg`  
 podczas Wskaźnik do obiektu ICorDebugType, który reprezentuje typ tablicy, wskaźnika lub odwołania, które mają zostać utworzone.  
  
 `ppType`  
 określoną Wskaźnik do adresu obiektu `ICorDebugType`, który reprezentuje skonstruowaną tablicę, typ wskaźnika lub typ referencyjny.  
  
## <a name="remarks"></a>Uwagi  
 Wartość *elementu ElementType* musi być jedną z następujących wartości:  
  
- ELEMENT_TYPE_PTR  
  
- ELEMENT_TYPE_BYREF  
  
- ELEMENT_TYPE_ARRAY lub ELEMENT_TYPE_SZARRAY  
  
 Jeśli wartość *elementu ElementType* to ELEMENT_TYPE_PTR lub ELEMENT_TYPE_BYREF, *nRank* musi mieć wartość zero.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
