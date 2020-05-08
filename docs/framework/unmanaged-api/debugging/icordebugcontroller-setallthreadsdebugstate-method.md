---
title: ICorDebugController::SetAllThreadsDebugState — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
ms.openlocfilehash: c2e8aaa2774e3e2699a73c40804391ca245047b1
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976593"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a>ICorDebugController::SetAllThreadsDebugState — Metoda
Ustawia stan debugowania wszystkich zarządzanych wątków w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `state`  
 podczas Wartość wyliczenia "CorDebugThreadState —", która określa stan wątku na potrzeby debugowania.  
  
 `pExceptThisThread`  
 podczas Wskaźnik do obiektu "ICorDebugThread", który reprezentuje wątek, który ma zostać wykluczony z ustawienia stanu debugowania. Jeśli ta wartość jest równa null, żaden wątek nie jest wykluczony.  
  
## <a name="remarks"></a>Uwagi  
 Metoda może mieć wpływ na wątki, które nie są widoczne za pośrednictwem [metody EnumerateThreads —](icordebugcontroller-enumeratethreads-method.md), więc wątki, `SetAllThreadsDebugState` które zostały zawieszone przy użyciu metody, muszą `SetAllThreadsDebugState` zostać wznowione przy użyciu metody. `SetAllThreadsDebugState`  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też
