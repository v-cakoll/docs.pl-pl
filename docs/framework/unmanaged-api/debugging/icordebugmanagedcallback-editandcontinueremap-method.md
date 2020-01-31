---
title: ICorDebugManagedCallback::EditAndContinueRemap — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EditAndContinueRemap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type:
- apiref
ms.openlocfilehash: 9cb956c0262fdcdb5971d049ea7b057aa4d952c0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781908"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a>ICorDebugManagedCallback::EditAndContinueRemap — Metoda
Ta metoda jest przestarzała. Powiadamia on debuger o wysłaniu zdarzenia ponownego mapowania do zintegrowanego środowiska programistycznego (IDE).  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a>Uwagi  
 Metoda `EditAndContinueRemap` jest wywoływana, gdy podjęto próbę wykonania kodu w starej wersji zaktualizowanej funkcji. Środowisko uruchomieniowe języka wspólnego wywołuje metodę `EditAndContinueRemap`, aby wysłać zdarzenie ponownego mapowania do środowiska IDE.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback, interfejs](icordebugmanagedcallback-interface.md)
