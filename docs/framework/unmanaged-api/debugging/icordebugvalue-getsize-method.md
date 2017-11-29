---
title: "ICorDebugValue::GetSize — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue.GetSize
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a412ec7fbc619ae01a981fefe10ce0e4f2874848
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvaluegetsize-method"></a>ICorDebugValue::GetSize — Metoda
Pobiera rozmiar w bajtach tego obiektu "ICorDebugValue".  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSize`  
 [out] Rozmiar w bajtach, ta wartość obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli typ wartości jest typem referencyjnym, ta metoda zwraca rozmiar wskaźnika niż rozmiar obiektu.  
  
 `ICorDebugValue::GetSize` Metoda zwraca `COR_E_OVERFLOW` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych. Użyj [ICorDebugValue3::GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) metody zamiast tego dla obiektów, które są większe niż 4 GB.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
    
 [GetSize64 — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
