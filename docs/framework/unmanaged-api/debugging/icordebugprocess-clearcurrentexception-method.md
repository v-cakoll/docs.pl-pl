---
title: ICorDebugProcess::ClearCurrentException — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
ms.openlocfilehash: 4cfacb7f3303947ec8b11362fde82649687889d8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792666"
---
# <a name="icordebugprocessclearcurrentexception-method"></a>ICorDebugProcess::ClearCurrentException — Metoda
Czyści bieżący wyjątek niezarządzany w danym wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 podczas Identyfikator wątku, w którym zostanie wyczyszczony bieżący wyjątek niezarządzany.  
  
## <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę przed wywołaniem [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) , gdy wątek zgłosił wyjątek niezarządzany, który powinien zostać zignorowany przez debugowanego obiektu. Spowoduje to wyczyszczenie wszystkich oczekujących zdarzeń w paśmie (IB) i poza pasmem (OOB) w danym wątku. Wszystkie punkty przerwania OOB i wyjątki pojedynczego kroku są automatycznie wyczyszczone.  
  
 Użyj [ICorDebugThread2:: InterceptCurrentException —](icordebugthread2-interceptcurrentexception-method.md) , aby przechwycić bieżący wyjątek zarządzany wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
