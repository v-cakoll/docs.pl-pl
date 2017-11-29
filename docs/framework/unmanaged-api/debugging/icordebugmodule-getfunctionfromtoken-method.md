---
title: "ICorDebugModule::GetFunctionFromToken — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetFunctionFromToken
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 96e458bc8fdcf37f572c1f45ba9c31d15311c8c6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a>ICorDebugModule::GetFunctionFromToken — Metoda
Pobiera funkcję, która jest określona przez token metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `methodDef`  
 [in] A `mdMethodDef` token metadanych, który odwołuje się do funkcji metadanych.  
  
 `ppFunction`  
 [out] Wskaźnik do adresu ICorDebugFunction obiektu interfejsu, który reprezentuje funkcję.  
  
## <a name="remarks"></a>Uwagi  
 `GetFunctionFromToken` Metoda zwróci wartość CORDBG_E_FUNCTION_NOT_IL HRESULT przypadku przekazano wartość `methodDef` nie odwołuje się do metody język pośredni (MSIL) firmy Microsoft.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
