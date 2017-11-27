---
title: "IHostTaskManager::BeginDelayAbort — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.BeginDelayAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::BeginDelayAbort
helpviewer_keywords:
- BeginDelayAbort method [.NET Framework hosting]
- IHostTaskManager::BeginDelayAbort method [.NET Framework hosting]
ms.assetid: 75f42a8b-ed68-4718-a030-a179cfba7d72
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 17af69c533c62b6a25d498fb245dfefe162690ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagerbegindelayabort-method"></a>IHostTaskManager::BeginDelayAbort — Metoda
Powiadamia hosta, którego kod zarządzany jest wprowadzanie okres, w którym nie musi być zostało przerwane bieżącego zadania.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT BeginDelayAbort ();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`BeginDelayAbort`zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
|E_UNEXPECTED|`BeginDelayAbort`została już wywołana, ale odpowiedniego wywołania [EndDelayAbort](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md) jeszcze nie został odebrany.|  
  
## <a name="remarks"></a>Uwagi  
 Host nie musi przerwać bieżącego zadania do `EndDelayAbort` jest wywoływana. Jeśli wywołanie innego `BeginDelayAbort` staje się bez interwencji wywołania do `EndDelayAbort`, hosta powinien zwrócić E_UNEXPECTED z `BeginDelayAbort`, a powinien Nie podejmuj żadnej akcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRTask — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTaskManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [IHostTaskManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
