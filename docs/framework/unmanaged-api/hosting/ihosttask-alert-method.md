---
title: IHostTask::Alert — Metoda
ms.date: 03/30/2017
api_name:
- IHostTask.Alert
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Alert
helpviewer_keywords:
- IHostTask::Alert method [.NET Framework hosting]
- Alert method, IHostTask interface [.NET Framework hosting]
ms.assetid: 5245d4b5-b6c3-48df-9cb9-8caf059f43fb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a5e3b82645456ffa574f63931abbf60a2194540
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764537"
---
# <a name="ihosttaskalert-method"></a>IHostTask::Alert — Metoda
Żądania, czy host wznawiania zadania, reprezentowane przez bieżącą [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) wystąpienie, dlatego zadanie może zostało przerwane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Alert ();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda zwróciła pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 CLR wywołuje `Alert` metody podczas <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> jest wywoływana z kodu użytkownika, lub gdy <xref:System.AppDomain> skojarzone z bieżącym <xref:System.Threading.Thread> zamyka. Host musi zwracać natychmiast, ponieważ połączenie jest nawiązywane asynchronicznie. Jeśli host nie może od razu alert zadania, jego wznawiania przy następnym go przechodzi do stanu, w którym można otrzymywać alerty.  
  
> [!NOTE]
>  `Alert` dotyczy tylko tych zadań, dla których minął środowiska uruchomieniowego [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartość WAIT_ALERTABLE metody takie jak [Dołącz](../../../../docs/framework/unmanaged-api/hosting/ihosttask-join-method.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
