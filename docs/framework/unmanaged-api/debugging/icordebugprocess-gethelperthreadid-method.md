---
title: ICorDebugProcess::GetHelperThreadID — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHelperThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type:
- apiref
ms.openlocfilehash: fc4f4b56552c4db265d2ea123a84c7792ad53094
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213637"
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID — Metoda
Pobiera identyfikator wątku pomocnika wewnętrznego debugera w systemie operacyjnym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pThreadID`  
 określoną Wskaźnik do identyfikatora wątku systemu operacyjnego wewnętrznego wątku pomocnika debugera.  
  
## <a name="remarks"></a>Uwagi  
 Podczas debugowania zarządzanego i niezarządzanego, jest odpowiedzialny za debuger, aby upewnić się, że wątek o określonym IDENTYFIKATORze pozostaje uruchomiony, jeśli trafi punkt przerwania umieszczony przez debuger. Debuger może również chcieć ukryć ten wątek od użytkownika. Jeśli w procesie nie istnieje jeszcze wątek pomocnika, `GetHelperThreadID` Metoda zwraca zero w * `pThreadID` .  
  
 Nie można buforować wątku identyfikatora wątku pomocnika, ponieważ może on ulec zmianie w czasie. W każdym zdarzeniu zatrzymywania należy wykonać ponowne zapytanie o identyfikator wątku.  
  
 Identyfikator wątku wątku pomocnika debugera będzie poprawny w każdym niezarządzanym zdarzeniu [ICorDebugManagedCallback:: Isthreading](icordebugmanagedcallback-createthread-method.md) , dzięki czemu debuger może ustalić identyfikator wątku jego wątku pomocnika i ukryć go od użytkownika. Wątek, który jest identyfikowany jako wątek pomocnika w niezarządzanym `ICorDebugManagedCallback::CreateThread` zdarzeniu, nigdy nie będzie uruchamiał zarządzanego kodu użytkownika.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl. CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
