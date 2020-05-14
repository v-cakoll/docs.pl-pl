---
title: ICorDebugValue3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
ms.openlocfilehash: 9f521eb942f37b8cf1d00bcc672071a69692b876
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396647"
---
# <a name="icordebugvalue3-interface"></a>ICorDebugValue3 — Interfejs
Rozszerza interfejsy "ICorDebugValue" i "ICorDebugValue2", aby zapewnić obsługę tablic o rozmiarze większym niż 2 GB.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetSize64, metoda](icordebugvalue3-getsize64-method.md)|Pobiera rozmiar tego obiektu w bajtach `ICorDebugValue3` .|  
  
## <a name="remarks"></a>Uwagi  
 Metoda [ICorDebugValue:: GetSize](icordebugvalue3-getsize64-method.md) zwraca rozmiar obiektu, który mieści się w zakresie od 0 do 2 147 483 647 bajtów. W .NET Framework 4,5 rozmiar tablic może przekroczyć 2 GB. `ICorDebugValue3`Interfejs umożliwia określenie rozmiaru tych tablic.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
