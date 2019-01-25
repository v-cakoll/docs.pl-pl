---
title: ICorDebugMutableDataTarget Interface
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f63343b43481d1d91d1db30cd2ace3214c5590a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492302"
---
# <a name="icordebugmutabledatatarget-interface"></a>ICorDebugMutableDataTarget Interface
Rozszerza [icordebugdatatarget —](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu do obsługi danych modyfikowalnych elementów docelowych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ContinueStatusChanged, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|Zmienia stan kontynuacji dla zdarzenia debugowania oczekujących na określonego wątku.|  
|[SetThreadContext, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|Ustawia kontekst (wartości rejestru) dla wątku.|  
|[WriteVirtual, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|Zapisuje w pamięci do przestrzeni adresowej procesu docelowego.|  
  
## <a name="remarks"></a>Uwagi  
 To rozszerzenie, aby [icordebugdatatarget —](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu może być implementowany przez narzędzia debugowania, które chcesz zmodyfikować procesu docelowego (na przykład przeprowadzić inwazyjne debugowania na żywo).  
  
 Wszystkie te metody są opcjonalne, w tym sensie, że nie podstawowych na podstawie kontroli debugowania funkcji zostaną utracone, przez nie implementuje ten interfejs lub niepowodzenia wywołania tych metod.  Jakiekolwiek niepowodzenie `HRESULT` z tych metod będzie propagowania jako `HRESULT` z wywołania metody ICorDebug.  
  
 Pamiętaj, że pojedyncze wywołanie metody ICorDebug może spowodować wiele mutacji a, nie ma mechanizmu zapewniających powiązane mutacji są stosowane transakcyjnie (wymuszać).  Oznacza to, jeśli mutacji zakończy się niepowodzeniem, po inne (na tym samym wywołaniu ICorDebug) zakończyły się powodzeniem, proces docelowy może pozostać w stanie niespójnym i debugowanie może stać się niepewna.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
