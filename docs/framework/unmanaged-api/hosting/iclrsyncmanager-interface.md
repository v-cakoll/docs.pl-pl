---
title: "ICLRSyncManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRSyncManager
helpviewer_keywords: ICLRSyncManager interface [.NET Framework hosting]
ms.assetid: a49f9d80-1c76-4ddd-8c49-34f913a5c596
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1e47f02a5a84b909b03c6be4e0a43c7166a1ddc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrsyncmanager-interface"></a>ICLRSyncManager — Interfejs
Definiuje metody, które umożliwiają hosta, aby uzyskać informacje dotyczące zadań i wykrył zakleszczenie w jej wykonanie synchronizacji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[CreateRWLockOwnerIterator — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-createrwlockowneriterator-method.md)|Żądania, które iteratora hosta na służy do określania zestawu zadań oczekujących na blokadę zapisu czytnika utworzyć środowisko uruchomieniowe języka wspólnego (CLR).|  
|[DeleteRWLockOwnerIterator — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-deleterwlockowneriterator-method.md)|Żąda, że środowisko CLR zniszczyć iterację, która została utworzona przez wywołanie do `CreateRWLockOwnerIterator`.|  
|[GetMonitorOwner — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getmonitorowner-method.md)|Pobiera zadanie, który jest właścicielem określony monitor.|  
|[GetRWLockOwnerNext — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-getrwlockownernext-method.md)|Pobiera następne zadanie, które oczekuje na bieżącego czytnika blokadę.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.Thread>  
 [IHostSyncManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [Zarządzana i niezarządzana wątkowość](http://msdn.microsoft.com/en-us/db425c20-4b2f-4433-bf96-76071c7881e5)  
 [Hosting — interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
