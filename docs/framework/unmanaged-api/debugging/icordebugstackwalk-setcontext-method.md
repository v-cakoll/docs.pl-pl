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
ms.openlocfilehash: 896e797acc76e8d8034bd964e488317a62eed97b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378775"
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
 podczas Przydzielony rozmiar `CONTEXT` buforu.  
  
 `context`  
 podczas `CONTEXT`Bufor.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`ICorDebugStackWalk`Kontekst obiektu został pomyślnie ustawiony.|  
|E_FAIL|`ICorDebugStackWalk`Nie ustawiono kontekstu obiektu.|  
|E_INVALIDARG|Kontekst ma wartość null.|  
|HRESULT_FROM_WIN32 (ERROR_INSUFFICIENT_BUFFER)|Bufor kontekstu jest za mały.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie zmienia bieżącego kontekstu wątku.  
  
 Ustawienie bieżącego kontekstu na nieprawidłowy kontekst może spowodować nieprzewidywalne wyniki z analizatora stosu.  
  
 Możesz pobrać dokładną kopię bitową tego kontekstu, natychmiast wywołując metodę [ICorDebugStackWalk:: GetContext](icordebugstackwalk-getcontext-method.md) .  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
