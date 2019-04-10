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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e7976740a79efda8e5ab569f2efb55444012c5d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220373"
---
# <a name="ihostthreadpoolmanager-interface"></a>IHostThreadPoolManager — Interfejs
Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR), aby skonfigurować puli wątków i kolejki elementów roboczych w puli wątków.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAvailableThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|Pobiera liczbę wątków w puli wątków, które nie są obecnie przetwarza elementy robocze.|  
|[GetMaxThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|Pobiera maksymalną liczbę wątków, które przechowuje hosta jednocześnie w puli wątków.|  
|[GetMinThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|Pobiera minimalna liczba bezczynnych wątków, które przechowuje hosta w oczekiwaniu żądań.|  
|[QueueUserWorkItem, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|Kolejki funkcję do wykonania i zapewnia obiekt zawierający dane do użycia przez funkcję.|  
|[SetMaxThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|Ustawia maksymalną liczbę wątków, zapewniające przez hosta w puli wątków.|  
|[SetMinThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|Ustawia minimalna liczba bezczynnych wątków, które hosta, musisz utrzymywać w oczekiwaniu żądań.|  
  
## <a name="remarks"></a>Uwagi  
 Host nie jest wymagana do skonfigurowania puli wątków przy użyciu wartości określone w wywołaniach `SetMaxThreads` i `SetMinThreads` metody. W tym przypadku hosta powinien zwrócić wartość HRESULT E_NOTIMPL z tych metod.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [Hosting — Interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
