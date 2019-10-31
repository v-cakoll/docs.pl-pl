---
title: ICorDebugBreakpoint — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
ms.openlocfilehash: 29bb84341c2cb4177c43f798d25a1a6d50099aa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122799"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint — Interfejs

Reprezentuje punkt przerwania w funkcji lub punkt obserwacji wartości.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Activate, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|Ustawia stan aktywny tego `ICorDebugBreakpoint`.|  
|[IsActive, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|Pobiera wartość wskazującą, czy ta `ICorDebugBreakpoint` jest aktywna.|  
  
## <a name="remarks"></a>Uwagi  
 Punkty przerwania nie obsługują bezpośrednio wyrażeń warunkowych. Jeśli ta funkcja jest wymagana, debuger musi zaimplementować ją na `ICorDebugBreakpoint`.  
  
 Interfejs ICorDebugFunctionBreakpoint rozszerza `ICorDebugBreakpoint` do obsługi punktów przerwania w funkcjach.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
