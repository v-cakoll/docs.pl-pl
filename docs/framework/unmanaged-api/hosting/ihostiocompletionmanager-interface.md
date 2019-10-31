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
ms.openlocfilehash: 51d79c398c94ec355528140325da2c25422cbad9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133849"
---
# <a name="ihostiocompletionmanager-interface"></a>IHostIoCompletionManager — Interfejs
Dostarcza metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do współdziałania z portami zakończenia we/wy dostarczonymi przez hosta.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[Bind, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md)|Tworzy powiązanie dojścia do portu zakończenia we/wy.|  
|[CloseIoCompletionPort, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-closeiocompletionport-method.md)|Zamyka port, który został utworzony przy użyciu wcześniejszego wywołania do `CreateIoCompletionPort`.|  
|[CreateIoCompletionPort, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md)|Żąda utworzenia przez hosta nowego portu zakończenia we/wy.|  
|[GetAvailableThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getavailablethreads-method.md)|Pobiera liczbę wątków zakończenia we/wy, które nie przetwarzają obecnie żądań.|  
|[GetHostOverlappedSize, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-gethostoverlappedsize-method.md)|Pobiera rozmiar danych niestandardowych, które Host zamierza dołączyć do żądań we/wy.|  
|[GetMaxThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getmaxthreads-method.md)|Pobiera maksymalną liczbę wątków, które host może przydzielić do żądań we/wy usługi.|  
|[GetMinThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-getminthreads-method.md)|Pobiera minimalną liczbę wątków przemieszczonych przez hosta w celu obsługi żądań we/wy.|  
|[InitializeHostOverlapped, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-initializehostoverlapped-method.md)|Udostępnia hostowi możliwość zainicjowania wszelkich niestandardowych danych dotyczących żądania we/wy.|  
|[SetCLRIoCompletionManager, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setclriocompletionmanager-method.md)|Dostarcza host ze wskaźnikiem interfejsu do wystąpienia [ICLRIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md) zaimplementowanego przez środowisko CLR.|  
|[SetMaxThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setmaxthreads-method.md)|Ustawia maksymalną liczbę wątków przynoszących Host do obsługi żądań we/wy.|  
|[SetMinThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-setminthreads-method.md)|Ustawia minimalną liczbę wątków, które host powinien przydzielić do zakończenia operacji we/wy.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostIoCompletionManager` odpowiada interfejsowi `ICLRIoCompletionManager` zaimplementowanym przez środowisko CLR. Środowisko CLR wywołuje metody `IHostIoCompletionManager`, aby powiązać dojścia do portów dostarczanych przez hosta, a host wywołuje metody `ICLRIoCompletionManager`, aby raportować ukończenie żądań we/wy.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
