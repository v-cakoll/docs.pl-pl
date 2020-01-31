---
title: ICorDebugController::EnumerateThreads — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.EnumerateThreads
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::EnumerateThreads
helpviewer_keywords:
- ICorDebugController::EnumerateThreads method [.NET Framework debugging]
- EnumerateThreads method [.NET Framework debugging]
ms.assetid: 73f536f6-4668-4a4a-b3e4-ac7df862d5be
topic_type:
- apiref
ms.openlocfilehash: 815dc63a2dedecc613506b0f98702f58d6e7bd04
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783789"
---
# <a name="icordebugcontrollerenumeratethreads-method"></a>ICorDebugController::EnumerateThreads — Metoda
Pobiera moduł wyliczający dla aktywnych wątków zarządzanych w procesie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumerateThreads (  
    [out] ICorDebugThreadEnum **ppThreads  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppThreads`  
 określoną Wskaźnik do adresu obiektu "ICorDebugThreadEnum", który reprezentuje moduł wyliczający dla wszystkich zarządzanych wątków, które są aktywne w procesie.  
  
## <a name="remarks"></a>Uwagi  
 Wątek jest uznawany za aktywny po wysłaniu wywołania zwrotnego [ICorDebugManagedCallback:: Onthreading](icordebugmanagedcallback-createthread-method.md) i przed wysłaniem wywołania zwrotnego [ICorDebugManagedCallback:: ExitThread —](icordebugmanagedcallback-exitthread-method.md) . Wątek zarządzany nie musi mieć żadnych zarządzanych ramek na stosie. Wątki można wyliczyć nawet przed wywołaniem zwrotnym [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) . Wyliczenie będzie w naturalny sposób puste.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
