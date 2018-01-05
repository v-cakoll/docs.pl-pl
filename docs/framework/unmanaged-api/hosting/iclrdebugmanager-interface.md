---
title: "ICLRDebugManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager
helpviewer_keywords: ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e712f22156e96cfc58e9c1a835077ba21ecd184
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager — Interfejs
Udostępnia metody umożliwiające hosta do skojarzenia z identyfikatorem i przyjazną nazwę zestawu zadań.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BeginConnection, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|Ustanawia nowego połączenia między hostem a debugera, aby skojarzyć zadania z identyfikatorem i przyjazną nazwę.|  
|[EndConnection, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|Usuwa skojarzenie listę zadań przyjazną nazwę i identyfikator.|  
|[GetDacl, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|Ta metoda nie jest zaimplementowana.|  
|[IsDebuggerAttached, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|Pobiera wartość wskazującą, czy debuger jest dołączony do procesu.|  
|[SetConnectionTasks, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|Kojarzy listę [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia o identyfikatorze i przyjazną nazwę.|  
|[SetDacl, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|Ta metoda nie jest zaimplementowana.|  
|[SetSymbolReadingPolicy, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|Ustawia zasady do odczytywania plików programu (PDB) bazy danych. Zasady określa, czy informacje dotyczące numerów wierszy i pliki są uwzględniane w stosy wywołań.|  
  
## <a name="remarks"></a>Uwagi  
 W scenariuszach debugowania hosta może być grupy zadań zgodnie z jego własnej logiki programowania. Na przykład grupa umożliwia deweloperom wyświetlane zadania wymagane przez projektanta interfejsów API, zamiast każdego zadania uruchomione w procesie. `ICLRDebugManager`Umożliwia hosta do wdrożenia tego rodzaju grupowania.  
  
> [!IMPORTANT]
>  Trzy `ICLRDebugManager` metod, `BeginConnection`, `SetConnectionTasks` i `EndConnection`, są zależne od siebie nawzajem. One musi zostać wywołany w podanej kolejności będzie działać zgodnie z oczekiwaniami.  
  
 Grupowanie oraz identyfikatorów i przyjaznych nazw hosta przypisuje się do nieistniejącego grupowania mają znaczenia w przypadku środowisko uruchomieniowe języka wspólnego (CLR). Środowisko CLR jedynie przekazuje informacje o wzdłuż do debugera.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
