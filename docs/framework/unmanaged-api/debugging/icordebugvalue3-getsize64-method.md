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
ms.openlocfilehash: 6eb26de83a6cdce47477e6cb3dffd6a94d889975
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397022"
---
# <a name="icordebugvalue3getsize64-method"></a>ICorDebugValue3::GetSize64 — Metoda
Pobiera rozmiar (w bajtach) tego obiektu [ICorDebugValue3](icordebugvalue3-interface.md) .  
  
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
  
 `ICorDebugValue3::GetSize`Metoda różni się od metody [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md) w typie parametru wyjściowego. W [ICorDebugValue:: GetSize](icordebugvalue-getsize-method.md)parametr wyjściowy to a `ULONG32` ; w `ICorDebugValue3::GetSize` , jest to `ULONG64` . Dzięki temu Interfejs [ICorDebugValue3](icordebugvalue3-interface.md) może raportować rozmiar tablic, które przekraczają 2 GB.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugValue3 — Interfejs](icordebugvalue3-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
