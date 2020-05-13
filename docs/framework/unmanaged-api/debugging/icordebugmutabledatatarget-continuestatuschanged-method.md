---
title: 'ICorDebugMutableDataTarget:: ContinueStatusChanged, Metoda'
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: 49f517c0c09771ce86e43b801f6d7fce695d907a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213312"
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
 Wartość [COREDB_CONTINUE_STATUS](../common-data-types-unmanaged-api-reference.md) , która reprezentuje nowy żądany stan kontynuacji.  
  
## <a name="remarks"></a>Uwagi  
 Debuger wywołuje metodę, `ContinueStatusChanged` gdy wywołuje metodę ICorDebug, która wymaga, aby bieżące zdarzenie debugowania zostało obsłużone w sposób, który może się różnić od sposobu, w jaki zwykle jest obsługiwany. Na przykład jeśli wystąpi wyjątek, a debuger żąda operacji, która spowodowałaby anulowanie wyjątku (na przykład [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) lub `FuncEval` ), ten interfejs API jest używany do żądania anulowania wyjątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugMutableDataTarget, interfejs](icordebugmutabledatatarget-interface.md)
- [Debugowanie — Interfejsy](debugging-interfaces.md)
