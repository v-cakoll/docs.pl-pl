---
title: ICorDebugValue::GetSize — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0023b8ad815b9204ed56791698c7242dfe90bec4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421661"
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
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
    
 [GetSize64, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
