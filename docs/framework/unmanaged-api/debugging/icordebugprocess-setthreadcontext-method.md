---
title: "ICorDebugProcess::SetThreadContext — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a7d40d455ea17b8df2acd77a1222ac6b080116c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocesssetthreadcontext-method"></a>ICorDebugProcess::SetThreadContext — Metoda
Ustawia kontekst dla danego wątku, w tym procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadID`  
 [in] Identyfikator wątku, który można ustawić kontekstu.  
  
 `contextSize`  
 [in] Rozmiar `context` tablicy.  
  
 `context`  
 [in] Tablica bajtów, które opisują kontekst wątku.  
  
 Kontekst określa architektury procesora, na którym jest wykonywany wątku.  
  
## <a name="remarks"></a>Uwagi  
 Debuger powinien wywoływać tej metody zamiast Win32 `SetThreadContext` działać, ponieważ wątek faktycznie może być w stanie "hijacked", w którym zostało tymczasowo zmienione kontekst. Tej metody należy użyć tylko wtedy, gdy wątek jest w kodzie natywnym. Użyj [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) wątków w kodzie zarządzanym. Nigdy nie powinien konieczne zmodyfikowanie kontekst wątku podczas zdarzenia debugowania poza pasmem (OOB).  
  
 Dane przekazane musi być strukturą kontekst dla bieżącej platformy.  
  
 Ta metoda może uszkodzić środowiska uruchomieniowego, użycie nieprawidłowo.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
