---
title: "ICorDebugProcess::GetHelperThreadID — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess.GetHelperThreadID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess::GetHelperThreadID
helpviewer_keywords:
- GetHelperThreadID method [.NET Framework debugging]
- ICorDebugProcess::GetHelperThreadID method [.NET Framework debugging]
ms.assetid: 84e1e605-37c1-49a5-8e12-35db85654622
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 092e99cb1d5534cee56db08b5a2eedaaa2fc4724
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugprocessgethelperthreadid-method"></a>ICorDebugProcess::GetHelperThreadID — Metoda
Pobiera identyfikator wątku systemu operacyjnego (OS) debugera wewnętrzny wątek pomocniczy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetHelperThreadID (  
    [out] DWORD *pThreadID  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pThreadID`  
 [out] Wskaźnik do systemu operacyjnego wątku identyfikator debugera wewnętrzny wątek pomocniczy.  
  
## <a name="remarks"></a>Uwagi  
 Podczas debugowania zarządzane i niezarządzane, odpowiada debugera upewnij się, z określonym Identyfikatorem wątku jest uruchomiona, jeśli jego trafienia punktu przerwania, umieszczonych przez debuger. Debuger może również chcesz ukryć ten wątek od użytkownika. Jeśli istnieje jeszcze w procesie nie wątek pomocniczy `GetHelperThreadID` metoda zwraca zero w *`pThreadID`.  
  
 Identyfikator wątku wątek pomocniczy nie może buforować, ponieważ może ulec zmianie. Identyfikator wątku, w każdym zdarzeniu zatrzymywania musi ponownie zapytanie.  
  
 Identyfikator wątku wątek pomocniczy debugera jest poprawny w każdym niezarządzane [ICorDebugManagedCallback::CreateThread](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-createthread-method.md) zdarzeń, dzięki czemu debugera do określenia Identyfikatora wątku jego wątek pomocniczy i Ukryj go przez użytkownika. Wątek, który jest rozpoznawany jako wątek pomocniczy podczas niezarządzane `ICorDebugManagedCallback::CreateThread` zdarzeń nigdy nie uruchomi kod zarządzany użytkownika.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl. CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
