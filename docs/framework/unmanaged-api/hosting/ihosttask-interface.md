---
title: "IHostTask — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTask
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTask
helpviewer_keywords: IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbffe2a171c112d4e9650b2c1b2a9ce1f010f382
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttask-interface"></a>IHostTask — Interfejs
Udostępnia metody umożliwiające środowisko uruchomieniowe języka wspólnego (CLR) do komunikacji z hostem, do zarządzania zadaniami.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Alert, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|Żądania, że host wake reprezentowany przez bieżące zadanie `IHostTask` wystąpienia, zadania można zostało przerwane.|  
|[GetPriority, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|Pobiera poziom priorytetu wątku zadania reprezentowany przez bieżący `IHostTask` wystąpienia.|  
|[Join, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|Blokuje wywoływania zadań dopóki reprezentowany przez bieżące zadanie `IHostTask` zakończeniu wystąpienia, upłynie określony interwał, lub [IHostTask::Alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) jest wywoływana.|  
|[SetCLRTask, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|Kojarzy [ICLRTask — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia z bieżącym `IHostTask` wystąpienia.|  
|[SetPriority, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|Żądania, że host dostosować priorytetu wątku poziomu reprezentowanego przez bieżącego zadania `IHostTask` wystąpienia.|  
|[Start, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|Żądania, że host move — zadanie reprezentowany przez bieżący `IHostTask` wystąpienie ze stanu wstrzymania do aktywnego stanu, w którym można wykonywać kodu.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR wywołuje metody zdefiniowane przez `IHostTask` można uruchomić zadania, jego priorytetu wątku ustaw poziom itd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
