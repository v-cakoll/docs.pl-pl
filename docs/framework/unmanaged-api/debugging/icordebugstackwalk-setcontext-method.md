---
title: ICorDebugStackWalk::SetContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.SetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::SetContext
helpviewer_keywords:
- SetContext method [.NET Framework debugging]
- ICorDebugStackWalk::SetContext method [.NET Framework debugging]
ms.assetid: bac0b156-31a3-4e7f-be4d-ab21789c81f1
topic_type:
- apiref
ms.openlocfilehash: 90156152a2c133446dedbe22426785ab63f8dfb9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131811"
---
# <a name="icordebugstackwalksetcontext-method"></a>ICorDebugStackWalk::SetContext — Metoda
Ustawia bieżący kontekst obiektu [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) na prawidłowy kontekst dla wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `flag`  
 podczas Flaga [CorDebugSetContextFlag —](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) , która wskazuje, czy kontekst pochodzi z aktywnej ramki na stosie, czy kontekst uzyskany przez odmieszczenie stosu.  
  
 `contextSize`  
 podczas Przydzielony rozmiar buforu `CONTEXT`.  
  
 `context`  
 podczas Bufor `CONTEXT`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Kontekst obiektu `ICorDebugStackWalk` został pomyślnie ustawiony.|  
|E_FAIL|Nie ustawiono kontekstu obiektu `ICorDebugStackWalk`.|  
|E_INVALIDARG|Kontekst ma wartość null.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|Bufor kontekstu jest za mały.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie zmienia bieżącego kontekstu wątku.  
  
 Ustawienie bieżącego kontekstu na nieprawidłowy kontekst może spowodować nieprzewidywalne wyniki z analizatora stosu.  
  
 Możesz pobrać dokładną kopię bitową tego kontekstu, natychmiast wywołując metodę [ICorDebugStackWalk:: GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
