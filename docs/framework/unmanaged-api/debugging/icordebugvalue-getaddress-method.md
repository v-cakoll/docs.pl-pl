---
title: ICorDebugValue::GetAddress — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5dc29663153f837b660262eae51b6f032617d027
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765068"
---
# <a name="icordebugvaluegetaddress-method"></a>ICorDebugValue::GetAddress — Metoda
Pobiera adres tego obiektu "ICorDebugValue", który jest w trakcie debugowania.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAddress`  
 [out] Wskaźnik do `CORDB_ADDRESS` obiekt, który określa adres obiektu tej wartości.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli wartość jest niedostępna, zwracany jest 0 (zero). To może się zdarzyć, jeśli wartość wynosi co najmniej częściowo w rejestrach ani przechowywane na uchwyt modułu odśmiecania pamięci (`GCHandle`).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
