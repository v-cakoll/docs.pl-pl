---
title: ICorDebugProcess8 — interfejs
ms.date: 03/30/2017
ms.assetid: 7ab1a70f-ec11-46ff-8869-cd8ca679cc51
ms.openlocfilehash: 813afc047f9fda060f1cf1af780336ff8b7c18be
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792157"
---
# <a name="icordebugprocess8-interface"></a>ICorDebugProcess8 — interfejs
[Obsługiwane w .NET Framework 4,6 i nowszych wersjach]  
  
 Logicznie rozszerza interfejs ICorDebugProcess w celu włączenia lub wyłączenia niektórych typów wywołań zwrotnych wyjątków [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnableExceptionCallbacksOutsideOfMyCode, metoda](icordebugprocess8-enableexceptioncallbacksoutsideofmycode-method.md)|Włącza lub wyłącza określone typy wywołań zwrotnych wyjątków [ICorDebugManagedCallback2](icordebugmanagedcallback2-interface.md) .|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
