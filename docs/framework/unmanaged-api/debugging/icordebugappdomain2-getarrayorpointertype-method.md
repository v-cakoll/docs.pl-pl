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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb3f0ca6d930b22f30fe9bbc5b5a04bf1e034f34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405828"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType — Metoda
Pobiera tablicę określonego typu lub wskaźnik lub odwołanie do określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `elementType`  
 [in] Wartość wyliczenia CorElementType określający typ podstawowy natywnego (tablicy, wskaźnika lub odwołania) ma zostać utworzony.  
  
 `nRank`  
 [in] Ranga (to znaczy, że liczba wymiarów) tablicy. Ta wartość musi wynosić 0, jeśli `elementType` Określa typ wskaźnika lub odwołania.  
  
 `pTypeArg`  
 [in] Wskaźnik do obiektu ICorDebugType, który reprezentuje typ tablicy, wskaźnika lub odwołania do utworzenia.  
  
 `ppType`  
 [out] Wskaźnik do adresu `ICorDebugType` typu obiektu, który reprezentuje skonstruowane tablicy, typ wskaźnika lub odwołania.  
  
## <a name="remarks"></a>Uwagi  
 Wartość *elementType* musi mieć jedną z następujących czynności:  
  
-   POPRAWNOŚCI ELEMENTU ELEMENT_TYPE_PTR  
  
-   ELEMENT_TYPE_BYREF  
  
-   ELEMENT_TYPE_ARRAY lub ELEMENT_TYPE_SZARRAY  
  
 Jeśli wartość *elementType* poprawności elementu ELEMENT_TYPE_PTR lub ELEMENT_TYPE_BYREF, *nRank* musi mieć wartość zero.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
