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
ms.openlocfilehash: 190908c675b96b8ea2d81fb0203aa16a80d6a8b4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501407"
---
# <a name="ihosttaskmanager-interface"></a>IHostTaskManager — Interfejs
Zapewnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do pracy z zadaniami za pośrednictwem hosta zamiast korzystania ze standardowego wątku lub funkcji światłowodowych systemu operacyjnego.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[BeginDelayAbort, metoda](ihosttaskmanager-begindelayabort-method.md)|Powiadamia hosta, że kod zarządzany wprowadza okres, w którym bieżące zadanie nie może zostać przerwane.|  
|[BeginThreadAffinity, metoda](ihosttaskmanager-beginthreadaffinity-method.md)|Powiadamia hosta, że kod zarządzany wprowadza okres, w którym bieżące zadanie nie może zostać przeniesione do innego wątku systemu operacyjnego.|  
|[CallNeedsHostHook, metoda](ihosttaskmanager-callneedshosthook-method.md)|Umożliwia hostowi określenie, czy środowisko uruchomieniowe języka wspólnego może być wbudowane w określone wywołanie do niezarządzanej funkcji.|  
|[CreateTask, metoda](ihosttaskmanager-createtask-method.md)|Żąda utworzenia nowego zadania przez hosta.|  
|[EndDelayAbort, metoda](ihosttaskmanager-enddelayabort-method.md)|Powiadamia hosta, że kod zarządzany kończy okres, w którym bieżące zadanie nie może zostać przerwane, po wcześniejszym wywołaniu `BeginDelayAbort` .|  
|[EndThreadAffinity, metoda](ihosttaskmanager-endthreadaffinity-method.md)|Powiadamia hosta, że kod zarządzany kończy okres, w którym bieżące zadanie nie może zostać przeniesione do innego wątku systemu operacyjnego, po wcześniejszym wywołaniu `BeginThreadAffinity` .|  
|[EnterRuntime, metoda](ihosttaskmanager-enterruntime-method.md)|Powiadamia hosta, że wywołanie metody niezarządzanej, takie jak metoda Invoke platformy, zwraca sterowanie wykonywaniem do środowiska CLR.|  
|[GetCurrentTask, metoda](ihosttaskmanager-getcurrenttask-method.md)|Pobiera wskaźnik interfejsu do zadania, które jest aktualnie wykonywane w wątku systemu operacyjnego, z którego wykonano to wywołanie.|  
|[GetStackGuarantee, metoda](ihosttaskmanager-getstackguarantee-method.md)|Pobiera ilość miejsca na stosie, która ma być dostępna po zakończeniu operacji stosu, ale przed zamknięciem procesu.|  
|[LeaveRuntime, metoda](ihosttaskmanager-leaveruntime-method.md)|Powiadamia hosta, że kod zarządzany ma nawiązać wywołanie funkcji niezarządzanej.|  
|[ReverseEnterRuntime, metoda](ihosttaskmanager-reverseenterruntime-method.md)|Powiadamia hosta, że wywołanie jest nawiązywane w środowisku uruchomieniowym języka wspólnego (CLR) z kodu niezarządzanego.|  
|[ReverseLeaveRuntime, metoda](ihosttaskmanager-reverseleaveruntime-method.md)|Powiadamia hosta, że kontrola opuszcza środowisko CLR i wprowadza niezarządzaną funkcję, która była z kolei wywoływana z kodu zarządzanego.|  
|[SetCLRTaskManager, metoda](ihosttaskmanager-setclrtaskmanager-method.md)|Dostarcza host ze wskaźnikiem interfejsu do wystąpienia [ICLRTaskManager](iclrtaskmanager-interface.md) zaimplementowanego przez środowisko CLR.|  
|[SetLocale, metoda](ihosttaskmanager-setlocale-method.md)|Powiadamia hosta o zmianie ustawień regionalnych przez środowisko CLR w bieżącym zadaniu.|  
|[SetStackGuarantee, metoda](ihosttaskmanager-setstackguarantee-method.md)|Zarezerwowane wyłącznie do użytku wewnętrznego.|  
|[SetUILocale, metoda](ihosttaskmanager-setuilocale-method.md)|Powiadamia hosta, że ustawienia regionalne interfejsu użytkownika zostały zmienione w bieżącym zadaniu.|  
|[Sleep, metoda](ihosttaskmanager-sleep-method.md)|Powiadamia hosta, że bieżące zadanie przechodzi w stan uśpienia.|  
|[SwitchToTask, metoda](ihosttaskmanager-switchtotask-method.md)|Powiadamia hosta o konieczności przełączenia bieżącego zadania.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostTaskManager`umożliwia środowisku CLR tworzenie zadań i zarządzanie nimi, w celu zapewnienia podpunktów dla hosta do podjęcia działania podczas kontroli transferu z zarządzanego do kodu niezarządzanego i na odwrót oraz do określania pewnych akcji, które host może i nie może wykonać podczas wykonywania kodu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTask — Interfejs](iclrtask-interface.md)
- [ICLRTaskManager, interfejs](iclrtaskmanager-interface.md)
- [IHostTask, interfejs](ihosttask-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
