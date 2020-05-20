---
title: ICLRIoCompletionManager::OnComplete — Metoda
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager.OnComplete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager::OnComplete
helpviewer_keywords:
- OnComplete method [.NET Framework hosting]
- ICLRIoCompletionManager::OnComplete method [.NET Framework hosting]
ms.assetid: 003f6974-9727-4322-bed5-e330d1224d0b
topic_type:
- apiref
ms.openlocfilehash: 39c9752912e88b04455516c0e9bed43610ba8aa0
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703813"
---
# <a name="iclriocompletionmanageroncomplete-method"></a>ICLRIoCompletionManager::OnComplete — Metoda
Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) o stanie żądania we/wy, które zostało wykonane przy użyciu wywołania metody [IHostIoCompletionManager:: bind](ihostiocompletionmanager-bind-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT OnComplete (  
    [in] DWORD dwErrorCode,  
    [in] DWORD NumberOfBytesTransferred,  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwErrorCode`  
 podczas Wartość HRESULT wskazująca stan operacji wiązania.  
  
- S_OK wskazuje, że operacja została ukończona pomyślnie.  
  
- HOST_E_INTERRUPTED wskazuje, że wywołanie zostało przerwane przed ukończeniem.  
  
- E_FAIL wskazuje, że wystąpił nieznany, nieodwracalny błąd krytyczny.  
  
 `NumberOfBytesTransferred`  
 podczas Liczba bajtów transferowanych podczas przetwarzania żądania we/wy.  
  
 `pvOverlapped`  
 podczas Wskaźnik do `OVERLAPPED` struktury, która została przeniesiona do wywołania `IHostIoCompletionManager::Bind` metody.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`OnComplete`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie metody E_FAIL nie będzie można używać środowiska CLR w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli Host implementuje abstrakcję ukończenia operacji we/wy, środowisko CLR wykonuje żądania we/wy za pośrednictwem hosta przy użyciu metod [IHostIoCompletionManager](ihostiocompletionmanager-interface.md). Następnie Host wywołuje `OnComplete` metodę w celu powiadomienia środowiska uruchomieniowego o wyniku takich żądań.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRIoCompletionManager, interfejs](iclriocompletionmanager-interface.md)
- [IHostIoCompletionManager, interfejs](ihostiocompletionmanager-interface.md)
- [IHostThreadPoolManager, interfejs](ihostthreadpoolmanager-interface.md)
