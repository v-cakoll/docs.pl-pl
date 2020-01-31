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
ms.openlocfilehash: be7fce700756d7120e0853446b7b307ec77c2080
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783760"
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
 Metoda `SetAllThreadsDebugState` może mieć wpływ na wątki, które nie są widoczne za pośrednictwem [metody EnumerateThreads —](icordebugcontroller-enumeratethreads-method.md), więc wątki, które zostały zawieszone przy użyciu metody `SetAllThreadsDebugState`, muszą zostać wznowione przy użyciu metody `SetAllThreadsDebugState`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
