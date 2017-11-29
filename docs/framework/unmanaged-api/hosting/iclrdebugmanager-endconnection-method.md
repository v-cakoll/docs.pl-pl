---
title: "ICLRDebugManager::EndConnection — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.EndConnection
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 114f2217d22fc270b03d271db4acc44f0edbcca8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugmanagerendconnection-method"></a>ICLRDebugManager::EndConnection — Metoda
Usuwa skojarzenie listę zadań przyjazną nazwę i identyfikator.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwConnectionId`  
 [in] Identyfikator specyficzne dla hosta dla połączenia i skojarzone listę typowych zadań dotyczących języka wspólnego (CLR).  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`EndConnection`zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|[BeginConnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md) nigdy nie została wywołana przy użyciu `dwConnectionId`, lub `dwConnectionId` wynosi zero.|  
  
## <a name="remarks"></a>Uwagi  
 [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) oferuje trzy metody `BeginConnection`, [SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md), i `EndConnection`, kojarzenia listy zadań z identyfikatorów i przyjazne nazwy.  
  
> [!IMPORTANT]
>  Te trzy metody należy wywołać w dowolnej kolejności dla każdego zestawu zadań. `BeginConnection`jest wywołane najpierw w celu nawiązania nowego połączenia. `SetConnectionTasks`wywoływana jest następnie podaj zestaw zadań związanych z tym połączeniem. `EndConnection`Aby usunąć skojarzenie między listy zadań identyfikator a przyjazna nazwa jest wywoływana ostatnio. Jednak wywołania dla różnych połączeń mogą być zagnieżdżone.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRControl — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [ICLRDebugManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [BeginConnection — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)  
 [SetConnectionTasks — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)  
 [IHostControl — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
