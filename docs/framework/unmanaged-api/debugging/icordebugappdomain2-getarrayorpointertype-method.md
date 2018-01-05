---
title: "ICorDebugAppDomain2::GetArrayOrPointerType — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomain2.GetArrayOrPointerType
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomain2::GetArrayOrPointerType
helpviewer_keywords:
- GetArrayOrPointerType method [.NET Framework debugging]
- ICorDebugAppDomain2::GetArrayOrPointerType method [.NET Framework debugging]
ms.assetid: 97e493f5-3a62-4ec7-b42f-4af57bf71f57
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6beb75638ccbf81149fd7fa1682acca3e7673dc8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
