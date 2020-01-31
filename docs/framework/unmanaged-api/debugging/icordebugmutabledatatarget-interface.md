---
title: ICorDebugMutableDataTarget, interfejs
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
ms.openlocfilehash: e4601c24194404f943c8de8f320bf704efcc553e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792858"
---
# <a name="icordebugmutabledatatarget-interface"></a>ICorDebugMutableDataTarget, interfejs
Rozszerza interfejs [ICorDebugDataTarget](icordebugdatatarget-interface.md) w celu obsługi modyfikowalnych obiektów docelowych danych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ContinueStatusChanged, metoda](icordebugmutabledatatarget-continuestatuschanged-method.md)|Zmienia stan kontynuacji dla zaległego zdarzenia debugowania w określonym wątku.|  
|[SetThreadContext, metoda](icordebugmutabledatatarget-setthreadcontext-method.md)|Ustawia kontekst (wartości rejestru) dla wątku.|  
|[WriteVirtual, metoda](icordebugmutabledatatarget-writevirtual-method.md)|Zapisuje pamięć w przestrzeni adresowej procesu docelowego.|  
  
## <a name="remarks"></a>Uwagi  
 To rozszerzenie interfejsu [ICorDebugDataTarget](icordebugdatatarget-interface.md) może zostać zaimplementowane przez narzędzia debugowania, które chcą zmodyfikować proces docelowy (na przykład w celu przeprowadzenia aktywnego debugowania).  
  
 Wszystkie te metody są opcjonalne w tym sensie, że żadne podstawowe funkcje debugowania nie są tracone przez zaimplementowanie tego interfejsu lub niepowodzenie wywołań tych metod.  Wszystkie niepowodzenia `HRESULT` z tych metod będą propagowane jako `HRESULT` z wywołania metody ICorDebug.  
  
 Należy zauważyć, że pojedyncze wywołanie metody ICorDebug może spowodować wielokrotne mutacje i że nie ma mechanizmu zapewnienia, że powiązane mutacje są stosowane transakcyjnie (wszystkie-lub-None).  Oznacza to, że jeśli mutacja nie powiedzie się po pomyślnym przejściu (dla tego samego wywołania ICorDebug), proces docelowy może pozostać w niespójnym stanie, a debugowanie może stać się niezawodne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie](index.md)
