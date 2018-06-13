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
ms.openlocfilehash: 194dcec6ea484e9cd2d3a17093c1eceb16c8f6c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440219"
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager — Interfejs
Udostępnia metody umożliwiające środowisko uruchomieniowe języka wspólnego (CLR) do interakcji z portów We/Wy dostarczone przez hosta.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Bind, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|Wiąże dojścia do portu zakończenia We/Wy.|  
|[CloseIoCompletionPort, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|Zamyka port, który został utworzony za pomocą wcześniejszych wywołania do `CreateIoCompletionPort`.|  
|[CreateIoCompletionPort, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|Żądania, hosta utworzyć nowego portu zakończenia We/Wy.|  
|[GetAvailableThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|Pobiera liczbę wątków zakończenia We/Wy, które nie są aktualnie przetwarza żądania.|  
|[GetHostOverlappedSize, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|Pobiera rozmiar niestandardowych danych, aby dołączyć do żądania operacji We/Wy przez hosta.|  
|[GetMaxThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|Pobiera maksymalną liczbę wątków, które można przyznać hosta do obsługi żądań We/Wy.|  
|[GetMinThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|Pobiera minimalną liczbę wątków, które zapewnia hosta do obsługi żądań We/Wy.|  
|[InitializeHostOverlapped, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|Zapewnia możliwość zainicjować wszelkie niestandardowe dane o żądaniu we/wy hosta.|  
|[SetCLRIoCompletionManager, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|Udostępnia wskaźnik interfejsu do hosta [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) wystąpienia zaimplementowana przez środowisko CLR.|  
|[SetMaxThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|Ustawia maksymalną liczbę wątków, które spowoduje przyznanie hosta do obsługi żądań We/Wy.|  
|[SetMinThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|Ustawia minimalną liczbę wątków, które należy przyznać hosta do zakończenia operacji We/Wy.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostIoCompletionManager` odpowiada `ICLRIoCompletionManager` interfejsu zaimplementowanego przez środowisko CLR. Środowisko CLR wywołuje metody `IHostIoCompletionManager` można powiązać dojścia do portów, które zapewnia hosta, a host wywołuje metody `ICLRIoCompletionManager` zgłoszenia ukończenia żądań We/Wy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
