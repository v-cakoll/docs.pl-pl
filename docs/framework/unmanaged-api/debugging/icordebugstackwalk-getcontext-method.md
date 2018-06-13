---
title: ICorDebugStackWalk::GetContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStackWalk.GetContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStackWalk::GetContext
helpviewer_keywords:
- GetContext method, ICorDebugStackWalk interface [.NET Framework debugging]
- ICorDebugStackWalk::GetContext method [.NET Framework debugging]
ms.assetid: 081d1c95-152b-4797-8552-18453eb7b14b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1126842a30f19831cc845bcfccc0e08f4bf5f6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422675"
---
# <a name="icordebugstackwalkgetcontext-method"></a>ICorDebugStackWalk::GetContext — Metoda
Zwraca kontekst dla bieżącej ramki [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetContext([in]  ULONG32 contextFlags,  
                   [in]  ULONG32 contextBufSize,  
                   [out] ULONG32* contextSize,  
                   [out, size_is(contextBufSize)] BYTE contextBuf[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `contextFlags`  
 [in] Flagi, które wskazują żądanej zawartości buforu kontekstu (zdefiniowane w pliku WinNT.h).  
  
 `contextBufSize`  
 [in] Przydzielony rozmiar buforu kontekstu.  
  
 `contextSize`  
 [out] Rzeczywisty rozmiar kontekstu. Ta wartość musi być większa niż rozmiar buforu kontekstu.  
  
 `contextBuf`  
 [out] Bufor kontekstu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Pomyślnie zwrócono kontekst dla bieżącej ramki.|  
|E_FAIL|Nie można zwrócić kontekstu.|  
|HRESULT_FROM_WIN32(ERROR_INSUFFICIENT BUFFER)|Bufor kontekstu jest za mały.|  
|CORDBG_E_PAST_END_OF_STACK|Wskaźnik ramki już znajduje się na końcu stosu; w związku z tym są dostępne nie dodatkowe ramki.|  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
 Ponieważ rozwinięcia przywraca tylko podzestaw rejestrów, takich jak rejestrów trwałej kontekstu nie może pasować stanu rejestru w momencie wywołania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
