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
ms.openlocfilehash: 515eb0633c82c3e1386487d1866de79c9898c9cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654610"
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager — Interfejs
Udostępnia metody, które umożliwiają hosta skojarzyć zestaw zadań z identyfikatorem i przyjazną nazwę.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BeginConnection, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|Ustanawia nowego połączenia między hostem a debugera, aby skojarzyć zadania z identyfikatorem i przyjazną nazwę.|  
|[EndConnection, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|Usuwa skojarzenie między listę zadań i identyfikatora oraz przyjazną nazwę.|  
|[GetDacl, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|Ta metoda nie jest zaimplementowana.|  
|[IsDebuggerAttached, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|Pobiera wartość wskazującą, czy debuger jest dołączony do procesu.|  
|[SetConnectionTasks, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|Kojarzy listę [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpień przy użyciu identyfikatora i przyjazną nazwę.|  
|[SetDacl, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|Ta metoda nie jest zaimplementowana.|  
|[SetSymbolReadingPolicy, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|Ustawia zasady do odczytywania plików bazy danych (PDB) programu. Zasady określają, czy informacje o numery wierszy i pliki są uwzględniane w stosy wywołań.|  
  
## <a name="remarks"></a>Uwagi  
 Podczas debugowania scenariuszy, host może być grupowania zadań zgodnie z własną logikę programistyczną. Na przykład grupowanie umożliwia deweloperem wyświetlić tylko zadania, które są wymagane przez interfejsy API dla deweloperów, zamiast zobaczyć zadanie, co zostało uruchomione w procesie. `ICLRDebugManager` Zezwalaj hostowi na zaimplementować ten rodzaj grupowania.  
  
> [!IMPORTANT]
>  Trzy `ICLRDebugManager` metod `BeginConnection`, `SetConnectionTasks` i `EndConnection`, są zależne od siebie nawzajem. One musi zostać wywołany w podanej kolejności, aby działać zgodnie z oczekiwaniami.  
  
 Grupowanie i identyfikatory i przyjaznych nazw hosta, przypisuje do grupowania, nie mają znaczenia dla środowisko uruchomieniowe języka wspólnego (CLR). Środowisko CLR jedynie przekazuje informacje o wzdłuż do debugera.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
