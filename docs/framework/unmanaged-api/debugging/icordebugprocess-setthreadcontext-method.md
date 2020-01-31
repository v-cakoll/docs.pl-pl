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
ms.openlocfilehash: 66d544bbc0511ea76565376c8f10294f1758026b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792571"
---
# <a name="icordebugprocesssetthreadcontext-method"></a>ICorDebugProcess::SetThreadContext — Metoda
Ustawia kontekst dla danego wątku w tym procesie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 podczas Identyfikator wątku, dla którego ma zostać ustawiony kontekst.  
  
 `contextSize`  
 podczas Rozmiar tablicy `context`.  
  
 `context`  
 podczas Tablica bajtów opisująca kontekst wątku.  
  
 Kontekst określa architekturę procesora, w którym wykonywany jest wątek.  
  
## <a name="remarks"></a>Uwagi  
 Debuger powinien wywołać tę metodę, a nie funkcję Win32 `SetThreadContext`, ponieważ wątek może być w stanie "przejęte", w którym jego kontekst został tymczasowo zmieniony. Ta metoda powinna być używana tylko wtedy, gdy wątek znajduje się w kodzie natywnym. Użyj [ICorDebugRegisterSet](icordebugregisterset-interface.md) dla wątków w kodzie zarządzanym. Nie trzeba zmieniać kontekstu wątku podczas zdarzenia debugowania poza pasmem (OOB).  
  
 Przesyłane dane muszą być strukturą kontekstu dla bieżącej platformy.  
  
 Ta metoda może uszkodzić środowisko uruchomieniowe, jeśli jest używane nieprawidłowo.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
