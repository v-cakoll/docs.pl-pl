---
title: "ICorDebugProcess::GetThreadContext — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetThreadContext
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9cb2b0be2954c041b364f9c85c40570a9f04421f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessgetthreadcontext-method"></a>ICorDebugProcess::GetThreadContext — Metoda
Pobiera kontekst dla danego wątku, w tym procesie.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadID`  
 [in] Identyfikator wątku, który można pobrać kontekstu.  
  
 `contextSize`  
 [in] Rozmiar `context` tablicy.  
  
 `context`  
 [w, out] Tablica bajtów, które opisują kontekst wątku.  
  
 Kontekst określa architektury procesora, na którym jest wykonywany wątku.  
  
## <a name="remarks"></a>Uwagi  
 Debuger powinien wywoływać tej metody zamiast Win32 `GetThreadContext` metody, ponieważ wątek faktycznie może być w stanie "hijacked", w którym zostało tymczasowo zmienione kontekst. Tej metody należy użyć tylko wtedy, gdy wątek jest w kodzie natywnym. Użyj [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) wątków w kodzie zarządzanym.  
  
 Dane zwrócone to struktura kontekst dla bieżącej platformy. Tak jak w przypadku środowiska Win32 `GetThreadContext` metody, wywołujący powinien zainicjować `context` parametru przed wywołaniem tej metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
