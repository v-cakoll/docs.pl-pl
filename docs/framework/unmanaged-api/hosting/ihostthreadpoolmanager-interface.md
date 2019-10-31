---
title: IHostThreadPoolManager — Interfejs
ms.date: 03/30/2017
api_name:
- IHostThreadPoolManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostThreadPoolManager
helpviewer_keywords:
- IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: c3a2cd90-7c4e-4374-bb87-b41befb8344f
topic_type:
- apiref
ms.openlocfilehash: 8aef78c7cf70e6b2d97af9c47d57908b86729ff7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122086"
---
# <a name="ihostthreadpoolmanager-interface"></a>IHostThreadPoolManager — Interfejs
Dostarcza metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do konfigurowania puli wątków i umieszczania elementów roboczych w kolejce w puli wątków.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAvailableThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|Pobiera liczbę wątków w puli wątków, które nie przetwarzają obecnie elementów roboczych.|  
|[GetMaxThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|Pobiera maksymalną liczbę wątków, które Host przechowuje współbieżnie w puli wątków.|  
|[GetMinThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|Pobiera minimalną liczbę bezczynnych wątków hostowanych przez hosta w oczekiwaniu na żądania.|  
|[QueueUserWorkItem, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|Kolejkuje funkcję do wykonania i dostarcza obiekt zawierający dane, które mają być używane przez funkcję.|  
|[SetMaxThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|Ustawia maksymalną liczbę wątków, które host może przechowywać w puli wątków.|  
|[SetMinThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|Określa minimalną liczbę bezczynnych wątków, które host musi zachować w oczekiwaniu na żądania.|  
  
## <a name="remarks"></a>Uwagi  
 Host nie jest wymagany do skonfigurowania puli wątków przy użyciu wartości określonych w wywołaniach metod `SetMaxThreads` i `SetMinThreads`. W takim przypadku host powinien zwrócić wartość HRESULT E_NOTIMPL z tych metod.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
