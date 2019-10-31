---
title: ICorDebugValue3::GetSize64 — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
ms.openlocfilehash: 72a1b6fdc40f3169500d8cf3b3028315106ecc69
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140233"
---
# <a name="icordebugvalue3getsize64-method"></a>ICorDebugValue3::GetSize64 — Metoda
Pobiera rozmiar (w bajtach) tego obiektu [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 pSize  
 określoną Wskaźnik do rozmiaru, w bajtach, tego obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli typ tej wartości jest typem referencyjnym, Metoda ta zwraca rozmiar wskaźnika, a nie rozmiar obiektu.  
  
 Metoda `ICorDebugValue3::GetSize` różni się od metody [ICorDebugValue:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md) w typie parametru wyjściowego. W [ICorDebugValue:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)parametr wyjściowy jest `ULONG32`; w `ICorDebugValue3::GetSize`jest to `ULONG64`. Dzięki temu Interfejs [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md) może raportować rozmiar tablic, które przekraczają 2 GB.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugValue3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
