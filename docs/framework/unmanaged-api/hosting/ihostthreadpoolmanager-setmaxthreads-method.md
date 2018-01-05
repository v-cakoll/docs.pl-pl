---
title: "IHostThreadPoolManager::SetMaxThreads — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostThreadPoolManager.SetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostThreadPoolManager::SetMaxThreads
helpviewer_keywords:
- IHostThreadPoolManager::SetMaxThreads method [.NET Framework hosting]
- SetMaxThreads method, IHostThreadPoolManager interface [.NET Framework hosting]
ms.assetid: 77cfd347-95c2-4425-b807-4ecc2a8d4578
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e3f637b1a50e3be3c544a107c603bc84ba2d5450
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostthreadpoolmanagersetmaxthreads-method"></a>IHostThreadPoolManager::SetMaxThreads — Metoda
Ustawia maksymalną liczbę wątków, które host może przechowywać w puli wątków.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetMaxThreads (  
    [in] DWORD MaxThreads  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `MaxThreads`  
 Maksymalna liczba wątków roboczych w puli wątków.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetMaxThreads`zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany, poważnej awarii. Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
|E_NOTIMPL|Host nie zapewniać implementację elementu `SetMaxThreads`.|  
  
## <a name="remarks"></a>Uwagi  
 Host nie jest wymagana w celu dopuszczenia CLR skonfigurować rozmiar puli wątków. Niektóre hosty, może być wyłączną kontrolę nad puli wątków powodów, takich jak wdrożenia, wydajności i skalowalności. W takim przypadku hosta powinien zwrócić wartość HRESULT E_NOTIMPL.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Threading.ThreadPool.SetMaxThreads%2A>  
 <xref:System.Threading.ThreadPool>  
 [GetMaxThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-getmaxthreads-method.md)  
 [SetMinThreads, metoda](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-setminthreads-method.md)  
 [IHostThreadPoolManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
