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
ms.openlocfilehash: b4f228d55c9ffd6b85ebd0b430a7f5db404320f6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124344"
---
# <a name="icordebugthread3getactiveinternalframes-method"></a>ICorDebugThread3::GetActiveInternalFrames — Metoda
Zwraca tablicę ramek wewnętrznych ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) obiektów) na stosie.  
  
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
 podczas Liczba wewnętrznych ramek oczekiwanych w `ppInternalFrames`.  
  
 `pcInternalFrames`  
 określoną Wskaźnik do `ULONG32`, który zawiera liczbę ramek wewnętrznych na stosie.  
  
 `ppInternalFrames`  
 [in. out] Wskaźnik do adresu tablicy ramek wewnętrznych na stosie.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Obiekt [ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) został pomyślnie utworzony.|  
|E_INVALIDARG|`cInternalFrames` nie jest zerem i `ppInternalFrames` jest `null`lub `pcInternalFrames` jest `null`.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|`ppInternalFrames` jest mniejsza niż liczba ramek wewnętrznych.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Ramki wewnętrzne to struktury danych wypychane na stosie przez środowisko uruchomieniowe do przechowywania danych tymczasowych.  
  
 Podczas pierwszego wywołania `GetActiveInternalFrames`należy ustawić parametr `cInternalFrames` na 0 (zero), a parametr `ppInternalFrames` na wartość null. Gdy `GetActiveInternalFrames` pierwsze zwraca, `pcInternalFrames` zawiera liczbę ramek wewnętrznych na stosie.  
  
 `GetActiveInternalFrames` powinna następnie być wywoływana po raz drugi. Należy przekazać poprawną liczbę (`pcInternalFrames`) w parametrze `cInternalFrames` i określić wskaźnik do odpowiedniej wielkości tablicy w `ppInternalFrames`.  
  
 Użyj metody [ICorDebugStackWalk:: GetFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md) , aby zwrócić rzeczywiste ramki stosu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
