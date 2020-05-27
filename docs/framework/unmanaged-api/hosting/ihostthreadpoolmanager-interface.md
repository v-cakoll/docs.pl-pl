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
ms.openlocfilehash: bac29b5950f1547c5c60ac716d40d2ef4b1a2cc2
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842484"
---
# <a name="ihostthreadpoolmanager-interface"></a>IHostThreadPoolManager — Interfejs
Dostarcza metody, które umożliwiają środowisko uruchomieniowe języka wspólnego (CLR) do konfigurowania puli wątków i umieszczania elementów roboczych w kolejce w puli wątków.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAvailableThreads, metoda](ihostthreadpoolmanager-getavailablethreads-method.md)|Pobiera liczbę wątków w puli wątków, które nie przetwarzają obecnie elementów roboczych.|  
|[GetMaxThreads, metoda](ihostthreadpoolmanager-getmaxthreads-method.md)|Pobiera maksymalną liczbę wątków, które Host przechowuje współbieżnie w puli wątków.|  
|[GetMinThreads, metoda](ihostthreadpoolmanager-getminthreads-method.md)|Pobiera minimalną liczbę bezczynnych wątków hostowanych przez hosta w oczekiwaniu na żądania.|  
|[QueueUserWorkItem, metoda](ihostthreadpoolmanager-queueuserworkitem-method.md)|Kolejkuje funkcję do wykonania i dostarcza obiekt zawierający dane, które mają być używane przez funkcję.|  
|[SetMaxThreads, metoda](ihostthreadpoolmanager-setmaxthreads-method.md)|Ustawia maksymalną liczbę wątków, które host może przechowywać w puli wątków.|  
|[SetMinThreads, metoda](ihostthreadpoolmanager-setminthreads-method.md)|Określa minimalną liczbę bezczynnych wątków, które host musi zachować w oczekiwaniu na żądania.|  
  
## <a name="remarks"></a>Uwagi  
 Host nie jest wymagany do skonfigurowania puli wątków przy użyciu wartości określonych w wywołaniach `SetMaxThreads` `SetMinThreads` metod i. W takim przypadku host powinien zwrócić wartość HRESULT E_NOTIMPL z tych metod.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Threading>
- <xref:System.Threading.ThreadPool>
- [Hosting, interfejsy](hosting-interfaces.md)
