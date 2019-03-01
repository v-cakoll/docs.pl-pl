---
title: ICorDebugHeapValue — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5263474b7b5001d561652291c23220da0a942bd1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980571"
---
# <a name="icordebugheapvalue-interface"></a>ICorDebugHeapValue — Interfejs

Podklasa klasy "ICorDebugValue", który reprezentuje obiekt, który został zebrany przez moduł odśmiecania pamięci środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateRelocBreakpoint, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|Nie zaimplementowano.|  
|[IsValid, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|Pobiera wartość wskazującą, czy obiekt reprezentowany przez ten `ICorDebugHeapValue` jest prawidłowy lub został odzyskany przez moduł odśmiecania pamięci. Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także



- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
