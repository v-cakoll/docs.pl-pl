---
title: ICorDebugProcess::IsOSSuspended — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
ms.openlocfilehash: 21da69d4bff0f17eb607dda45fb7dbafea8c59f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128770"
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended — Metoda
Pobiera wartość wskazującą, czy określony wątek został wstrzymany w wyniku debugera zatrzymywania tego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 podczas Identyfikator wątku.  
  
 `pbSuspended`  
 określoną Wskaźnik do wartości logicznej, która jest `true`, jeśli określony wątek został zawieszony; w przeciwnym wypadku *`pbSuspended` jest `false`.  
  
## <a name="remarks"></a>Uwagi  
 Gdy określony wątek zostanie zawieszony z powodu zatrzymywania tego procesu przez debuger, licznik zawieszania Win32 określonego wątku jest zwiększany o jeden. Interfejs użytkownika debugera (UI) może chcieć zastosować te informacje w przypadku wyświetlenia przez użytkownika liczby wstrzymania wątku dla tego systemu operacyjnego.  
  
 Metoda `IsOSSuspended` ma sens tylko w kontekście debugowania niezarządzanego. Podczas debugowania zarządzanego wątki są zawieszone w trybie spółdzielni, a nie zawieszone w systemie operacyjnym.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
