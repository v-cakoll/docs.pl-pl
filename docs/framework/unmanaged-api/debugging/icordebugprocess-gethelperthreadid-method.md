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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cd5e30d08e667dcd5a8be1f9502462f28290068e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987743"
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID — Metoda
Pobiera identyfikator wątku systemu operacyjnego (OS) debugera wewnętrzny wątek pomocniczy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pThreadID`  
 [out] Wskaźnik do systemu operacyjnego wątku identyfikator wątku wewnętrznego Pomocnik debugera.  
  
## <a name="remarks"></a>Uwagi  
 Podczas debugowania zarządzanych i niezarządzanych, jest debugera ponosić odpowiedzialność za zapewnienie wątku z określonym Identyfikatorem jest uruchomiona, w przypadku trafienia punktu przerwania umieszczone przez debuger. Debuger może również chcesz ukryć ten wątek od użytkownika. Jeśli wątek pomocniczy, nie istnieje w procesie jeszcze `GetHelperThreadID` metoda zwraca zero w *`pThreadID`.  
  
 Identyfikator wątku wątek pomocniczy nie może buforować, ponieważ czasem ulec zmianie. Identyfikator wątku na każde zdarzenie zatrzymywanie musi ponownie zapytania.  
  
 Identyfikator wątku wątek pomocniczy debugera będzie prawidłowy w każdy niezarządzany [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) zdarzenia, dzięki czemu debugera określić identyfikator wątku wątku pomocnika i Ukryj go przez użytkownika. Wątek, który jest identyfikowany jako wątek pomocniczy podczas niezarządzanych `ICorDebugManagedCallback::CreateThread` zdarzeń nigdy nie spowoduje uruchomienia kodu zarządzanego użytkownika.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl. CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
