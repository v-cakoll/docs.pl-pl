---
title: ICorDebugMutableDataTarget, interfejs
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
ms.openlocfilehash: 682e927388d3392d970338314f97d46c9e57e760
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139334"
---
# <a name="icordebugmutabledatatarget-interface"></a>ICorDebugMutableDataTarget, interfejs
Rozszerza interfejs [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) w celu obsługi modyfikowalnych obiektów docelowych danych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ContinueStatusChanged, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|Zmienia stan kontynuacji dla zaległego zdarzenia debugowania w określonym wątku.|  
|[SetThreadContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|Ustawia kontekst (wartości rejestru) dla wątku.|  
|[WriteVirtual, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|Zapisuje pamięć w przestrzeni adresowej procesu docelowego.|  
  
## <a name="remarks"></a>Uwagi  
 To rozszerzenie interfejsu [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) może zostać zaimplementowane przez narzędzia debugowania, które chcą zmodyfikować proces docelowy (na przykład w celu przeprowadzenia aktywnego debugowania).  
  
 Wszystkie te metody są opcjonalne w tym sensie, że żadne podstawowe funkcje debugowania nie są tracone przez zaimplementowanie tego interfejsu lub niepowodzenie wywołań tych metod.  Wszystkie niepowodzenia `HRESULT` z tych metod będą propagowane jako `HRESULT` z wywołania metody ICorDebug.  
  
 Należy zauważyć, że pojedyncze wywołanie metody ICorDebug może spowodować wielokrotne mutacje i że nie ma mechanizmu zapewnienia, że powiązane mutacje są stosowane transakcyjnie (wszystkie-lub-None).  Oznacza to, że jeśli mutacja nie powiedzie się po pomyślnym przejściu (dla tego samego wywołania ICorDebug), proces docelowy może pozostać w niespójnym stanie, a debugowanie może stać się niezawodne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
