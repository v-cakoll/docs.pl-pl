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
ms.openlocfilehash: 92097cdf735630f3537296f188bd83ea8162add2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441141"
---
# <a name="ihostthreadpoolmanager-interface"></a>IHostThreadPoolManager — Interfejs
Udostępnia metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) w celu skonfigurowania puli wątków i kolejki elementów roboczych w puli wątków.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAvailableThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getavailablethreads-method.md)|Pobiera liczbę wątków w puli wątków, które nie są aktualnie przetwarza elementów roboczych.|  
|[GetMaxThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)|Pobiera maksymalną liczbę wątków, która jest obsługiwana przez hosta jednocześnie w puli wątków.|  
|[GetMinThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getminthreads-method.md)|Pobiera minimalna liczba wątków bezczynności, która jest obsługiwana przez hosta w oczekiwaniu żądania.|  
|[QueueUserWorkItem, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-queueuserworkitem-method.md)|Funkcja do wykonania kolejek i udostępnia obiekt zawierający dane, które mają być używane przez funkcję.|  
|[SetMaxThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setmaxthreads-method.md)|Ustawia maksymalną liczbę wątków, które host może przechowywać w puli wątków.|  
|[SetMinThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)|Ustawia minimalną liczbę bezczynności wątków, które muszą zachować hosta w oczekiwaniu żądania.|  
  
## <a name="remarks"></a>Uwagi  
 Host nie jest wymagana do skonfigurowania puli wątków przy użyciu wartości określone w wywołaniach `SetMaxThreads` i `SetMinThreads` metody. W takim przypadku hosta powinien zwrócić wartość HRESULT E_NOTIMPL z tych metod.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading>  
 <xref:System.Threading.ThreadPool>  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
