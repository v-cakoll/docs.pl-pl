---
title: IHostTask — Interfejs
ms.date: 03/30/2017
api_name:
- IHostTask
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask
helpviewer_keywords:
- IHostTask interface [.NET Framework hosting]
ms.assetid: a71dbbd5-64b8-47eb-9f03-8e8c85fbe2bc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d862c02e96487049fb88f80665d32caf6939ed1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555947"
---
# <a name="ihosttask-interface"></a>IHostTask — Interfejs
Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do komunikacji z hostem, do zarządzania zadaniami.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Alert, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)|Żądania, czy host wznawiania zadania, reprezentowane przez bieżącą `IHostTask` wystąpienie, dlatego zadanie może zostało przerwane.|  
|[GetPriority, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-getpriority-method.md)|Pobiera poziom priorytetu wątku zadania, reprezentowane przez bieżącą `IHostTask` wystąpienia.|  
|[Join, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md)|Blokuje wywołującym je zadaniem i do zadań, reprezentowane przez bieżącą `IHostTask` ukończenia wystąpienia, przez określony interwał czasu upłynie, lub [ihosttask::alert —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md) jest wywoływana.|  
|[SetCLRTask, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setclrtask-method.md)|Kojarzy [iclrtask — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) wystąpienia z bieżącymi `IHostTask` wystąpienia.|  
|[SetPriority, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-setpriority-method.md)|Na poziomie żądania, czy host zmienić priorytet wątku dla zadania, reprezentowane przez bieżącą `IHostTask` wystąpienia.|  
|[Start, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttask-start-method.md)|Żądania, że host move — zadanie, reprezentowane przez bieżącą `IHostTask` wystąpienia ze stanu wstrzymania Państwu na żywo, w którym można wykonywać kodu.|  
  
## <a name="remarks"></a>Uwagi  
 Środowisko CLR wywołuje metody zdefiniowane przez `IHostTask` można uruchomić zadania, ustaw jego priorytetu wątku poziom, i tak dalej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
