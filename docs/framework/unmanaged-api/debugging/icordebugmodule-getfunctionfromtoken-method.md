---
title: ICorDebugModule::GetFunctionFromToken — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 547986633172d6f5e6549ad2048833dc9fb0cef3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763467"
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a>ICorDebugModule::GetFunctionFromToken — Metoda
Pobiera funkcję, która jest określona przez token metadanych.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `methodDef`  
 [in] A `mdMethodDef` token metadanych, który odwołuje się do metadanych funkcji.  
  
 `ppFunction`  
 [out] Wskaźnik na adres obiektu interfejsu ICorDebugFunction, który reprezentuje funkcję.  
  
## <a name="remarks"></a>Uwagi  
 `GetFunctionFromToken` Metoda zwraca wartość CORDBG_E_FUNCTION_NOT_IL HRESULT, jeśli wartość przekazywana w `methodDef` nie odwołuje się do firmy Microsoft intermediate language (MSIL) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
