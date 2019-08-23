---
title: ICLRDebugManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a408995793caf879f8d5624ab727102c4859195
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959613"
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager — Interfejs
Dostarcza metody, które umożliwiają hostowi kojarzenie zestawu zadań z identyfikatorem i przyjazną nazwą.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BeginConnection, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|Ustanawia nowe połączenie między hostem i debugerem w celu kojarzenia zadań z identyfikatorem i przyjazną nazwą.|  
|[EndConnection, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|Usuwa skojarzenie między listą zadań i identyfikatorem i przyjazną nazwą.|  
|[GetDacl, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|Ta metoda nie jest zaimplementowana.|  
|[IsDebuggerAttached, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|Pobiera wartość wskazującą, czy debuger jest dołączony do procesu.|  
|[SetConnectionTasks, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|Kojarzy listę wystąpień [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) z identyfikatorem i przyjazną nazwą.|  
|[SetDacl, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|Ta metoda nie jest zaimplementowana.|  
|[SetSymbolReadingPolicy, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|Ustawia zasady odczytywania plików bazy danych programu (PDB). Zasady określają, czy informacje o numerach wierszy i plikach są zawarte w stosach wywołań.|  
  
## <a name="remarks"></a>Uwagi  
 W scenariuszach debugowania host może chcieć grupować zadania zgodnie z własną logiką programowania. Na przykład zgrupowanie zezwoli deweloperowi na wyświetlanie tylko zadań wymaganych przez interfejsy API dewelopera, a nie oglądanie wszystkich zadań uruchomionych w procesie. `ICLRDebugManager`zezwala hostowi na wdrożenie tego rodzaju grupowania.  
  
> [!IMPORTANT]
> Trzy `ICLRDebugManager` metody, `BeginConnection`, `SetConnectionTasks` i`EndConnection`, są zależne od siebie. Muszą być wywoływane w danej kolejności, aby działały zgodnie z oczekiwaniami.  
  
 Grupowanie i identyfikatory oraz przyjazne nazwy przypisywane przez hosta do grupy nie mają znaczenia dla środowiska uruchomieniowego języka wspólnego (CLR). Środowisko CLR jedynie przekazuje informacje wraz z debugerem.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** MSCorEE. h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
