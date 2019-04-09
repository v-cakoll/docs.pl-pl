---
title: IHostTaskManager — Interfejs
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da30e75bf4a58e66bb0dd8210368b162cf14c3f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091268"
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager — Interfejs
Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do pracy z zadaniami za pośrednictwem hosta, zamiast korzystać z funkcji wątki lub włókna standardowy system operacyjny.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BeginDelayAbort, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-begindelayabort-method.md)|Powiadamia hosta, którego kod zarządzany wchodzi okres, w którym musi nie przerwane bieżącego zadania.|  
|[BeginThreadAffinity, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-beginthreadaffinity-method.md)|Powiadamia hosta, którego kod zarządzany wchodzi okres, w którym bieżące zadanie musi nie można przenieść na inny wątek systemu operacyjnego.|  
|[CallNeedsHostHook, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-callneedshosthook-method.md)|Umożliwia hosta określić, czy środowisko uruchomieniowe języka wspólnego może wbudowane określone wywołanie do niezarządzanej funkcji.|  
|[CreateTask, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-createtask-method.md)|Żądania, że host Utwórz nowe zadanie.|  
|[EndDelayAbort, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enddelayabort-method.md)|Powiadamia hosta, którego kod zarządzany jest kończone okres, w której nie można przerwać bieżące zadanie, zgodnie z wcześniejszym wywołaniem `BeginDelayAbort`.|  
|[EndThreadAffinity, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)|Powiadamia hosta, którego kod zarządzany jest kończone okres, w którym bieżące zadanie musi nie można przenieść na inny wątek systemu operacyjnego, zgodnie z wcześniejszym wywołaniem `BeginThreadAffinity`.|  
|[EnterRuntime, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-enterruntime-method.md)|Powiadamia hosta, że wywołanie metody niezarządzanego, takie jak metody wywołania platformy zwraca Kontrola wykonywania do środowiska CLR.|  
|[GetCurrentTask, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getcurrenttask-method.md)|Pobiera wskaźnik interfejsu do zadania, które jest obecnie wykonywany w wątku systemu operacyjnego, w którym wykonano to wywołanie.|  
|[GetStackGuarantee, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-getstackguarantee-method.md)|Pobiera ilość miejsca stosu, który może być dostępna po zakończeniu operacji stosu, ale przed zamknięciem procesu.|  
|[LeaveRuntime, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-leaveruntime-method.md)|Powiadamia hosta, którego kod zarządzany ma wykonać wywołanie do niezarządzanej funkcji.|  
|[ReverseEnterRuntime, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseenterruntime-method.md)|Powiadamia hosta, że wywołanie odbywa się na środowisko uruchomieniowe języka wspólnego (CLR) z kodem niezarządzanym.|  
|[ReverseLeaveRuntime, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-reverseleaveruntime-method.md)|Powiadamia hosta, że formant jest pozostawienie środowiska CLR i wprowadzenie niezarządzanej funkcji, która z kolei wywoływana z kodu zarządzanego.|  
|[SetCLRTaskManager, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setclrtaskmanager-method.md)|Udostępnia wskaźnik interfejsu do hosta [iclrtaskmanager —](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) wystąpienia implementowane przez środowisko CLR.|  
|[SetLocale, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)|Powiadamia hosta, że środowisko CLR zmienił ustawienia regionalne na bieżące zadanie.|  
|[SetStackGuarantee, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setstackguarantee-method.md)|Zarezerwowana tylko do użytku wewnętrznego.|  
|[SetUILocale, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)|Powiadamia hosta, że ustawienia regionalne interfejsu użytkownika został zmieniony na bieżące zadanie.|  
|[Sleep, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)|Powiadamia hosta, że bieżące zadanie przechodzi w stan uśpienia.|  
|[SwitchToTask, metoda](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)|Powiadamia hosta, że powinni przełączyć się do bieżącego zadania.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostTaskManager` Umożliwia środowisku CLR utworzyć i zarządzać zadaniami, aby zapewnić punkty zaczepienia dla hosta podjąć działania, gdy formant przesyła z zarządzanego do kodu niezarządzanego i na odwrót i określić pewne akcje, host może i nie można przyjąć podczas wykonywania kodu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTask — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask — Interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [Hosting — Interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
