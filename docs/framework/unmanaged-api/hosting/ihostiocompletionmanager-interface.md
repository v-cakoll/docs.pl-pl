---
title: IHostIoCompletionManager — Interfejs
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager
helpviewer_keywords:
- IHostIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c28d1983-83f7-46e2-990f-dbb9dc07c818
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 186f5618cce7a70bc4fab55616a0f8b08025a81f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542540"
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager — Interfejs
Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do interakcji z portów We/Wy udostępniane przez hosta.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Bind, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|Wiąże dojścia do portu ukończenia operacji We/Wy.|  
|[CloseIoCompletionPort, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|Zamyka port, który został utworzony przy użyciu wcześniejszego wywołania funkcji `CreateIoCompletionPort`.|  
|[CreateIoCompletionPort, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|Żądania, że host tworzą nowy port wykonywania operacji We/Wy.|  
|[GetAvailableThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|Pobiera liczbę wątków zakończenia operacji We/Wy, które nie są obecnie przetwarza żądania.|  
|[GetHostOverlappedSize, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|Pobiera rozmiar danych niestandardowych, aby dołączyć do żądań We/Wy przez hosta.|  
|[GetMaxThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|Pobiera maksymalną liczbę wątków, które można przyznać hosta do obsługi żądań We/Wy.|  
|[GetMinThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|Pobiera minimalną liczbę wątków, udostępnianych przez hosta do obsługi żądań We/Wy.|  
|[InitializeHostOverlapped, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|Zapewnia możliwość zainicjowania wszelkie niestandardowe dane dotyczące żądania We/Wy hosta.|  
|[SetCLRIoCompletionManager, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|Udostępnia wskaźnik interfejsu do hosta [iclriocompletionmanager —](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) wystąpienia implementowane przez środowisko CLR.|  
|[SetMaxThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|Ustawia maksymalną liczbę wątków, które spowoduje przyznanie hosta do obsługi żądań We/Wy.|  
|[SetMinThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|Ustawia minimalną liczbę wątków, które należy przyznać hosta do zakończenia operacji We/Wy.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostIoCompletionManager` odnosi się do `ICLRIoCompletionManager` interfejs implementowany przez środowisko CLR. Środowisko CLR wywołuje metody `IHostIoCompletionManager` powiązać porty, które zapewnia hosta, a host wywołuje metody uchwytów `ICLRIoCompletionManager` zgłosić realizacji żądań We/Wy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
