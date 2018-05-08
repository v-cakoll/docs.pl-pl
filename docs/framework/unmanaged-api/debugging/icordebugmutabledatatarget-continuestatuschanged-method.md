---
title: ICorDebugMutableDataTarget::ContinueStatusChanged — metoda
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb07c519743c41a7a31994e42d2fdc5220e5e2ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a>ICorDebugMutableDataTarget::ContinueStatusChanged — metoda
Zmienia stan kontynuacji dla zdarzenia debugowania oczekujących na określony wątek.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwThreadId`  
 Identyfikator wątku zdefiniowane przez system operacyjny.  
  
 `continueStatus`  
 A[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)wartość, która reprezentuje nowe żądanie kontynuacji stanu.  
  
## <a name="remarks"></a>Uwagi  
 Wywołań debugera `ContinueStatusChanged` metody, gdy wywołuje metodę ICorDebug wymaga bieżącego zdarzenia debugowania mają zostać obsłużone w sposób zapewniający potencjalnie różni się od sposób, w którym go zwykle może być obsługiwane. Na przykład, jeśli istnieje oczekujące wyjątek i debuger żądań operację, która spowoduje anulowanie wyjątek (takich jak [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) lub `FuncEval`), ten interfejs API jest używany do żądania, aby był wyjątek anulowane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugMutableDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
