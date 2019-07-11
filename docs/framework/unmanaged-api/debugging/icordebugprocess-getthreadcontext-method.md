---
title: ICorDebugProcess::GetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c137a10d5da94d04509385fc97d71535d33fae93
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758737"
---
# <a name="icordebugprocessgetthreadcontext-method"></a>ICorDebugProcess::GetThreadContext — Metoda
Pobiera kontekst dla danego wątku w ramach tego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 [in] Identyfikator wątku, do których chcesz pobrać kontekstu.  
  
 `contextSize`  
 [in] Rozmiar `context` tablicy.  
  
 `context`  
 [out w] Tablica bajtów, które opisują kontekst wątku.  
  
 Kontekst określa z architekturą procesora, na którym wykonywany jest wątek.  
  
## <a name="remarks"></a>Uwagi  
 Debuger powinien wywoływać tej metody, a nie Win32 `GetThreadContext` metody, ponieważ wątek rzeczywiście może być w stanie "przejętego", w którym zostało tymczasowo zmienione kontekst. Ta metoda powinna służyć tylko wtedy, gdy wątek jest w kodzie natywnym. Użyj [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) dla wątków w kodzie zarządzanym.  
  
 Dane zwracane to struktura kontekstu dla bieżącej platformy. Podobnie jak w przypadku Win32 `GetThreadContext` obiektu wywołującego metody, należy zainicjować `context` parametru przed wywołaniem tej metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
