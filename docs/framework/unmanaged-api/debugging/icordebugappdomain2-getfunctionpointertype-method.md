---
title: ICorDebugAppDomain2::GetFunctionPointerType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2.GetFunctionPointerType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType
helpviewer_keywords:
- ICorDebugAppDomain2::GetFunctionPointerType method [.NET Framework debugging]
- GetFunctionPointerType method [.NET Framework debugging]
ms.assetid: 0aba6096-5b38-435c-a72a-86d35db4daef
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d497fd8e659a24add25df63c4ce48e710dcb0c6d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403796"
---
# <a name="icordebugappdomain2getfunctionpointertype-method"></a>ICorDebugAppDomain2::GetFunctionPointerType — Metoda
Pobiera wskaźnik do funkcji, która ma danym podpisem.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetFunctionPointerType (  
    [in] ULONG32                             nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType   *ppTypeArgs[],  
    [out] ICorDebugType                      **ppType  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nTypeArgs`  
 [in] Liczba argumentów typu dla funkcji.  
  
 `ppTypeArgs`  
 [in] Tablicy wskaźników, z których każdy wskazuje obiekt ICorDebugType, który reprezentuje typ argumentu funkcji. Pierwszy element jest typu zwracanego; Każdy z innymi elementami jest typ parametru.  
  
 `ppType`  
 [out] Wskaźnik do adresu `ICorDebugType` obiekt, który reprezentuje wskaźnik do funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
