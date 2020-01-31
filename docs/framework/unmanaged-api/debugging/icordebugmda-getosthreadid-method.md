---
title: ICorDebugMDA::GetOSThreadId — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
ms.openlocfilehash: d9efefb26ee175fa60e7cc4516ff3f8444968f31
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793219"
---
# <a name="icordebugmdagetosthreadid-method"></a>ICorDebugMDA::GetOSThreadId — Metoda
Pobiera identyfikator wątku systemu operacyjnego, na którym jest wykonywany Asystent debugowania zarządzanego (MDA) reprezentowany przez [ICorDebugMDA](icordebugmda-interface.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pOsTid`  
 określoną Wskaźnik do identyfikatora wątku systemu operacyjnego.  
  
## <a name="remarks"></a>Uwagi  
 Wątek systemu operacyjnego jest używany zamiast ICorDebugThread, aby umożliwić sytuacje, w których zdarzenie MDA jest wywoływane w wątku macierzystym lub w zarządzanym wątku, które nie podano jeszcze kodu zarządzanego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMDA, interfejs](icordebugmda-interface.md)
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
