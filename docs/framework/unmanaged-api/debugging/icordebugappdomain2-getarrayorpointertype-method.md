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
ms.openlocfilehash: 6cc38ef23a8b802d674a7a6dc4807371e432f73d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593515"
---
# <a name="icordebugappdomain2getarrayorpointertype-method"></a>ICorDebugAppDomain2::GetArrayOrPointerType — Metoda
Pobiera tablicę elementów określonego typu lub wskaźnik lub odwołanie do określonego typu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetArrayOrPointerType (  
    [in]  CorElementType    elementType,  
    [in]  ULONG32           nRank,  
    [in]  ICorDebugType     *pTypeArg,  
    [out] ICorDebugType     **ppType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `elementType`  
 [in] Wartość corelementtype — wyliczenie, określający typ podstawowy natywnego (tablicy, wskaźnika lub odwołania) ma zostać utworzony.  
  
 `nRank`  
 [in] Ranga (oznacza to, że liczba wymiarów) tablicy. Ta wartość musi wynosić 0, jeśli `elementType` Określa typ wskaźnika lub odwołania.  
  
 `pTypeArg`  
 [in] Wskaźnik do obiektu ICorDebugType, który reprezentuje typ tablicy, wskaźnika lub odwołania do utworzenia.  
  
 `ppType`  
 [out] Wskaźnik na adres `ICorDebugType` typ obiektu, który reprezentuje zbudowany tablicy, typ wskaźnika lub odwołania.  
  
## <a name="remarks"></a>Uwagi  
 Wartość *elementType* musi mieć jedną z następujących czynności:  
  
- ELEMENT_TYPE_PTR  
  
- POLE  
  
- ELEMENT_TYPE_ARRAY lub ELEMENT_TYPE_SZARRAY  
  
 Jeśli wartość *elementType* ELEMENT_TYPE_PTR lub pole, *nRank* musi mieć wartość zero.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
