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
ms.openlocfilehash: 23ad8882ad97e5ceaeb690dfae08a6be55b85f64
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791856"
---
# <a name="icordebugstackwalksetcontext-method"></a>ICorDebugStackWalk::SetContext — Metoda
Ustawia bieżący kontekst obiektu [ICorDebugStackWalk](icordebugstackwalk-interface.md) na prawidłowy kontekst dla wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `flag`  
 podczas Flaga [CorDebugSetContextFlag —](cordebugsetcontextflag-enumeration.md) , która wskazuje, czy kontekst pochodzi z aktywnej ramki na stosie, czy kontekst uzyskany przez odmieszczenie stosu.  
  
 `contextSize`  
 podczas Przydzielony rozmiar buforu `CONTEXT`.  
  
 `context`  
 podczas Bufor `CONTEXT`.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Kontekst obiektu `ICorDebugStackWalk` został pomyślnie ustawiony.|  
|E_FAIL|Nie ustawiono kontekstu obiektu `ICorDebugStackWalk`.|  
|E_INVALIDARG|Kontekst ma wartość null.|  
|HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)|Bufor kontekstu jest za mały.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie zmienia bieżącego kontekstu wątku.  
  
 Ustawienie bieżącego kontekstu na nieprawidłowy kontekst może spowodować nieprzewidywalne wyniki z analizatora stosu.  
  
 Możesz pobrać dokładną kopię bitową tego kontekstu, natychmiast wywołując metodę [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
