---
title: 'ICorDebugMutableDataTarget:: ContinueStatusChanged, Metoda'
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: abaf2d0542e16f526ecbe369370c31c225808f1f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139353"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a>ICorDebugMutableDataTarget:: ContinueStatusChanged, Metoda
Zmienia stan kontynuacji dla zaległego zdarzenia debugowania w określonym wątku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwThreadId`  
 Identyfikator wątku zdefiniowanego przez system operacyjny.  
  
 `continueStatus`  
 Wartość [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , która reprezentuje nowy żądany stan kontynuacji.  
  
## <a name="remarks"></a>Uwagi  
 Debuger wywołuje metodę `ContinueStatusChanged`, gdy wywołuje metodę ICorDebug, która wymaga, aby bieżące zdarzenie debugowania zostało obsłużone w sposób, który może się różnić w zależności od tego, w jaki sposób zwykle byłyby obsługiwane. Jeśli na przykład wystąpił wyjątek oczekujący, a debuger żąda operacji, która spowodowałaby anulowanie wyjątku (na przykład [ICorDebugILFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) lub `FuncEval`), ten interfejs API jest używany do żądania anulowania wyjątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMutableDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
