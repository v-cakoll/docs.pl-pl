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
ms.openlocfilehash: d0dc301c67d09ebb15bf47cef15e642fb7c78fb9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792607"
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
 Podczas debugowania zarządzanego i niezarządzanego, jest odpowiedzialny za debuger, aby upewnić się, że wątek o określonym IDENTYFIKATORze pozostaje uruchomiony, jeśli trafi punkt przerwania umieszczony przez debuger. Debuger może również chcieć ukryć ten wątek od użytkownika. Jeśli żaden wątek pomocnika nie istnieje jeszcze w procesie, Metoda `GetHelperThreadID` zwraca zero w *`pThreadID`.  
  
 Nie można buforować wątku identyfikatora wątku pomocnika, ponieważ może on ulec zmianie w czasie. W każdym zdarzeniu zatrzymywania należy wykonać ponowne zapytanie o identyfikator wątku.  
  
 Identyfikator wątku wątku pomocnika debugera będzie poprawny w każdym niezarządzanym zdarzeniu [ICorDebugManagedCallback:: Isthreading](icordebugmanagedcallback-createthread-method.md) , dzięki czemu debuger może ustalić identyfikator wątku jego wątku pomocnika i ukryć go od użytkownika. Wątek, który jest identyfikowany jako wątek pomocnika w niezarządzanym zdarzeniu `ICorDebugManagedCallback::CreateThread` nigdy nie będzie uruchamiał zarządzanego kodu użytkownika.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl. CorDebug.h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
