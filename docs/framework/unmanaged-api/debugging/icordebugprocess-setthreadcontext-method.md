---
title: ICorDebugProcess::SetThreadContext — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e281022cd7bc9b2095fdbd3964061b811ef60e0d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949035"
---
# <a name="icordebugprocesssetthreadcontext-method"></a>ICorDebugProcess::SetThreadContext — Metoda
Ustawia kontekst dla danego wątku w ramach tego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 [in] Identyfikator wątku, do których chcesz ustawić kontekst.  
  
 `contextSize`  
 [in] Rozmiar `context` tablicy.  
  
 `context`  
 [in] Tablica bajtów, które opisują kontekst wątku.  
  
 Kontekst określa z architekturą procesora, na którym wykonywany jest wątek.  
  
## <a name="remarks"></a>Uwagi  
 Debuger powinien wywoływać tej metody, a nie Win32 `SetThreadContext` działać, ponieważ wątek rzeczywiście może być w stanie "przejętego", w którym zostało tymczasowo zmienione kontekst. Ta metoda powinna służyć tylko wtedy, gdy wątek jest w kodzie natywnym. Użyj [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) dla wątków w kodzie zarządzanym. Nigdy nie należy modyfikować kontekst wątku podczas zdarzenia debugowania poza pasmem (OOB).  
  
 Dane przekazywane musi być strukturą kontekstu dla bieżącej platformy.  
  
 Ta metoda może uszkodzić środowisko wykonawcze, jeśli niepoprawnie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
