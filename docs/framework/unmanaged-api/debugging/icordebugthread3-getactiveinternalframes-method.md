---
title: ICorDebugThread3::GetActiveInternalFrames — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread3.GetActiveInternalFrames Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3::GetActiveInternalFrames
helpviewer_keywords:
- ICorDebugThread3::GetActiveInternalFrames method [.NET Framework debugging]
- GetActiveInternalFrames method [.NET Framework debugging]
ms.assetid: d69796b4-5b6d-457c-85f6-2cf42e8a8773
topic_type:
- apiref
ms.openlocfilehash: 680af5afa3ebef5bcaf9e34580e421dcc8093aaf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178464"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames — Metoda
Zwraca tablicę ramek wewnętrznych[(Obiekty ICorDebugInternalFrame2)](icordebuginternalframe2-interface.md) na stosie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetActiveInternalFrames  
      (  
      [in] ULONG32 cInternalFrames,  
      [out] ULONG32 *pcInternalFrames,  
      [in, out,size_is(cInternalFrames), length_is(*pcInternalFrames)]  
            ICorDebugInternalFrame2 * ppInternalFrames[]  
      );  
```  
  
## <a name="parameters"></a>Parametry  
 `cInternalFrames`  
 [w] Liczba ramek wewnętrznych oczekiwanych w pliku `ppInternalFrames`.  
  
 `pcInternalFrames`  
 [na zewnątrz] Wskaźnik do, `ULONG32` który zawiera liczbę klatek wewnętrznych na stosie.  
  
 `ppInternalFrames`  
 [w, na zewnątrz] Wskaźnik do adresu tablicy ramek wewnętrznych na stosie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne HRESULTs, a także błędy HRESULT, które wskazują na niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Obiekt [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) został pomyślnie utworzony.|  
|E_invalidarg|`cInternalFrames`nie jest `ppInternalFrames` zerowa `pcInternalFrames` i `null`jest `null`, lub jest .|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames`jest mniejsza niż liczba klatek wewnętrznych.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Ramki wewnętrzne są struktury danych wypchnięte do stosu przez środowisko wykonawcze do przechowywania danych tymczasowych.  
  
 Podczas pierwszego `GetActiveInternalFrames`wywołania należy `cInternalFrames` ustawić parametr na 0 `ppInternalFrames` (zero), a parametr na wartość null. Po `GetActiveInternalFrames` pierwszym `pcInternalFrames` zwraca, zawiera liczbę ramek wewnętrznych na stosie.  
  
 `GetActiveInternalFrames`następnie należy nazwać po raz drugi. Należy przekazać właściwą`pcInternalFrames`liczbę ( `cInternalFrames` ) w parametrze i określić `ppInternalFrames`wskaźnik do tablicy o odpowiednim rozmiarze w .  
  
 Użyj [metody ICorDebugStackWalk::GetFrame,](icordebugthread3-getactiveinternalframes-method.md) aby zwrócić rzeczywiste ramki stosu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugging](index.md)
