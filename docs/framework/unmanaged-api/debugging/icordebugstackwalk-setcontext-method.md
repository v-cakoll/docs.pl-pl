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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7306ee61d750ae256c93c049819a23d3d61f7297
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116470"
---
# <a name="icordebugstackwalksetcontext-method"></a>ICorDebugStackWalk::SetContext — Metoda
Zestawy [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu w bieżącym kontekście do prawidłowego kontekstu dla wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetContext([in] CorDebugSetContextFlag flag,  
                   [in] ULONG32 contextSize,  
                   [in, size_is(contextSize)] BYTE context[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `flag`  
 [in] A [cordebugsetcontextflag —](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md) flagę, która wskazuje, czy kontekst jest z aktywną ramkę stosu lub kontekst uzyskanych przez odwijania stosu.  
  
 `contextSize`  
 [in] Przydzielony rozmiar `CONTEXT` buforu.  
  
 `context`  
 [in] `CONTEXT` Buforu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`ICorDebugStackWalk` Pomyślnie ustawiono kontekstu obiektu.|  
|E_FAIL|`ICorDebugStackWalk` Nie ustawiono kontekstu obiektu.|  
|E_INVALIDARG|Kontekst ma wartość null.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)|Buforu kontekstu jest za mały.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie zmienia bieżący kontekst wątku.  
  
 Ustawienie bieżącego kontekstu Nieprawidłowy kontekst może spowodować nieprzewidywalne skutki z walker stosu.  
  
 Bitowe dokładną kopię tego kontekstu można pobrać natychmiast wywołując [ICorDebugStackWalk::GetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-getcontext-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie — Interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
