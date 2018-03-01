---
title: "IHostTaskManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager
helpviewer_keywords:
- IHostTaskManager interface [.NET Framework hosting]
ms.assetid: 4a0b05b9-3ef1-4607-b7c8-bd4dd43647a0
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9573891a2c27a2a92eccd0522f84175effa8037a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager — Interfejs
Udostępnia metody umożliwiające środowisko uruchomieniowe języka wspólnego (CLR) do pracy z zadaniami za pośrednictwem hosta zamiast przy użyciu funkcji wątki lub włókna standardowy system operacyjny.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BeginDelayAbort, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|Powiadamia hosta, którego kod zarządzany jest wprowadzanie okres, w którym nie musi być zostało przerwane bieżącego zadania.|  
|[BeginThreadAffinity, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|Powiadamia hosta, którego kod zarządzany jest wprowadzanie okres, w którym bieżącego zadania nie muszą zostać przeniesione do innego wątku systemu operacyjnego.|  
|[CallNeedsHostHook, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|Umożliwia hosta określić, czy środowisko uruchomieniowe języka wspólnego może wbudowanego określonego wywołanie funkcji niezarządzanej.|  
|[CreateTask, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|Żądania, hosta utworzyć nowe zadanie.|  
|[EndDelayAbort, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|Powiadamia hosta, którego kod zarządzany jest zamykanie okres, w którym nie można przerwać bieżące zadanie, po wcześniejszej wywołanie `BeginDelayAbort`.|  
|[EndThreadAffinity, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|Powiadamia hosta, którego kod zarządzany jest zamykanie okres, w którym bieżącego zadania nie muszą zostać przeniesione do innego wątku systemu operacyjnego, po wcześniejszej wywołanie `BeginThreadAffinity`.|  
|[EnterRuntime, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|Powiadamia hosta, że wywołanie do metody niezarządzanych, takich jak platforma wywołania metody, zwraca Kontrola wykonywania do środowiska CLR.|  
|[GetCurrentTask, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|Pobiera wskaźnika interfejsu do zadania, które jest obecnie wykonywane w wątku systemu operacyjnego, z której dokonywane jest to wywołanie.|  
|[GetStackGuarantee, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|Pobiera ilość miejsca na stosie, który może być dostępne po zakończeniu operacji stosu, ale przed zamknięciem procesu.|  
|[LeaveRuntime, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|Powiadamia hosta, którego kod zarządzany ma wywoływania funkcji niezarządzanej.|  
|[ReverseEnterRuntime, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|Powiadamia hosta, że wywołanie odbywa się na środowisko uruchomieniowe języka wspólnego (CLR) z kodem niezarządzanym.|  
|[ReverseLeaveRuntime, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|Powiadamia hosta, czy formant jest pozostawienie środowiska CLR i wprowadzenie niezarządzanej funkcji, który z kolei wywołane z kodu zarządzanego.|  
|[SetCLRTaskManager, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|Udostępnia wskaźnik interfejsu do hosta [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) wystąpienia zaimplementowana przez środowisko CLR.|  
|[SetLocale, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|Powiadamia hosta zmiana CLR ustawień regionalnych na bieżące zadanie.|  
|[SetStackGuarantee, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|Zastrzeżone wyłącznie do użytku wewnętrznego.|  
|[SetUILocale, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|Powiadamia hosta, że ustawienia regionalne interfejsu użytkownika została zmieniona na bieżące zadanie.|  
|[Sleep, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|Powiadamia hosta, że bieżące zadanie przechodzi w stan uśpienia.|  
|[SwitchToTask, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|Powiadamia hosta, że należy przełączyć się bieżącego zadania.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostTaskManager`Umożliwia CLR tworzenie i zarządzanie nimi zadania, aby zapewnić punkty zaczepienia dla hosta podjęcie działań kontroli transferu z zarządzanego do kodu niezarządzanego lub odwrotnie, a także określić pewne akcje hosta można i nie może przyjąć podczas wykonywania kodu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
