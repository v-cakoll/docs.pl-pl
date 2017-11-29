---
title: "ICorDebugValue::GetAddress — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue.GetAddress
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7018dcb41f46d5407549f5c3d3029716781014e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvaluegetaddress-method"></a>ICorDebugValue::GetAddress — Metoda
Pobiera adres tego obiektu "ICorDebugValue", który jest w trakcie debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAddress`  
 [out] Wskaźnik do `CORDB_ADDRESS` obiektu, który określa adres tego obiektu wartości.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość jest niedostępna, zwracany jest 0 (zero). To może się zdarzyć, jeśli wartość jest co najmniej częściowo w rejestrach lub przechowywane w uchwytu modułu zbierającego elementy bezużyteczne (`GCHandle`).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 
