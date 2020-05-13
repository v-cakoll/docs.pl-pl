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
ms.openlocfilehash: 953b7c1cb5e471072776fe03e53a46d3ff19c0ac
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379855"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames — Metoda
Zwraca tablicę ramek wewnętrznych ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) obiektów) na stosie.  
  
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
 podczas Liczba wewnętrznych ramek oczekiwanych w `ppInternalFrames` .  
  
 `pcInternalFrames`  
 określoną Wskaźnik do obiektu `ULONG32` , który zawiera liczbę ramek wewnętrznych na stosie.  
  
 `ppInternalFrames`  
 [in. out] Wskaźnik do adresu tablicy ramek wewnętrznych na stosie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Obiekt [ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) został pomyślnie utworzony.|  
|E_INVALIDARG|`cInternalFrames`nie jest zerem i `ppInternalFrames` ma wartość `null` lub `pcInternalFrames` jest `null` .|  
|HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames`jest mniejsza niż liczba ramek wewnętrznych.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Ramki wewnętrzne to struktury danych wypychane na stosie przez środowisko uruchomieniowe do przechowywania danych tymczasowych.  
  
 Podczas pierwszego wywołania `GetActiveInternalFrames` parametru należy ustawić wartość `cInternalFrames` 0 (zero), a `ppInternalFrames` parametr na wartość null. Gdy `GetActiveInternalFrames` pierwsze zwraca, `pcInternalFrames` zawiera liczbę ramek wewnętrznych na stosie.  
  
 `GetActiveInternalFrames`następnie powinna być wywoływana po raz drugi. Należy przekazać poprawną liczbę ( `pcInternalFrames` ) w `cInternalFrames` parametrze i określić wskaźnik do odpowiedniej wielkości tablicy w `ppInternalFrames` .  
  
 Użyj metody [ICorDebugStackWalk:: GetFrame](icordebugthread3-getactiveinternalframes-method.md) , aby zwrócić rzeczywiste ramki stosu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
