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
ms.openlocfilehash: 9ff7128f55236ae4d0c3a9067a279c496cfb6798
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396750"
---
# <a name="icordebugvaluegetsize-method"></a>ICorDebugValue::GetSize — Metoda
Pobiera rozmiar tego obiektu "ICorDebugValue" w bajtach.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pSize`  
 określoną Rozmiar (w bajtach) tego obiektu wartości.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli typ wartości jest typem referencyjnym, Metoda ta zwraca rozmiar wskaźnika, a nie rozmiar obiektu.  
  
 `ICorDebugValue::GetSize`Metoda zwraca `COR_E_OVERFLOW` dla obiektów, które są większe niż 4 GB na platformach 64-bitowych. Zamiast obiektów, które są większe niż 4 GB, użyj metody [ICorDebugValue3:: GetSize64 —](icordebugvalue3-getsize64-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [GetSize64, metoda](icordebugvalue3-getsize64-method.md)
