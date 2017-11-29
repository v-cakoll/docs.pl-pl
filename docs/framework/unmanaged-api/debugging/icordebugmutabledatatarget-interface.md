---
title: Interfejs ICorDebugMutableDataTarget
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef1c0b7a56f6bd1f7e87650b72dfe8b1411ef7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatarget-interface"></a>Interfejs ICorDebugMutableDataTarget
Rozszerza [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejs do obsługi danych modyfikowalne elementy docelowe.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ContinueStatusChanged — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|Zmienia stan kontynuacji dla zdarzenia debugowania oczekujących na określony wątek.|  
|[SetThreadContext — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|Ustawia kontekst wątku (wartości rejestru).|  
|[WriteVirtual — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|Zapisuje pamięci do przestrzeni adresowej procesu docelowego.|  
  
## <a name="remarks"></a>Uwagi  
 To rozszerzenie do [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu może być zaimplementowany przez narzędzia debugowania, które chcesz zmodyfikować procesu docelowego (na przykład, aby wykonać inwazyjne debugowania na żywo).  
  
 Wszystkie te metody są opcjonalne, w tym sensie, że nie core kontroli funkcje oparte na debugowania nie są tracone przez nie implementuje ten interfejs lub Niepowodzenie wywołania tych metod.  Jakiekolwiek niepowodzenie `HRESULT` z tych metod rozpropaguje się jako `HRESULT` w wywołaniu metody ICorDebug.  
  
 Uwaga przez jednego wywołania metody ICorDebug może spowodować wiele mutacji, oraz że nie istnieje mechanizm zapewniających powiązane mutacji są stosowane transakcyjnie (wykonywanie).  To oznacza, że jeśli mutacja nie powiedzie się po innych (na to samo wywołanie ICorDebug) zakończyło się pomyślnie, proces docelowy może pozostać w stanie niespójnym, a debugowania mogą stać się niepewna.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie](../../../../docs/framework/unmanaged-api/debugging/index.md)
