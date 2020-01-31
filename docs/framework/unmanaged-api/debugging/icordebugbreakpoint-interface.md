---
title: ICorDebugBreakpoint, interfejs
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
ms.openlocfilehash: 53d8d219a13f2dade16a338efccf0837f8de0158
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784376"
---
# <a name="icordebugbreakpoint-interface"></a>ICorDebugBreakpoint, interfejs

Reprezentuje punkt przerwania w funkcji lub punkt obserwacji wartości.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Activate, metoda](icordebugbreakpoint-activate-method.md)|Ustawia stan aktywny tego `ICorDebugBreakpoint`.|  
|[IsActive, metoda](icordebugbreakpoint-isactive-method.md)|Pobiera wartość wskazującą, czy ta `ICorDebugBreakpoint` jest aktywna.|  
  
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

- [Debugowanie, interfejsy](debugging-interfaces.md)
