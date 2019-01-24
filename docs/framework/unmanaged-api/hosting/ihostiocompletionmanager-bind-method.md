---
title: IHostIoCompletionManager::Bind — Metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.Bind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c03cdb9f9205676d17d6e18b9b2e074132ee26f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594775"
---
# <a name="ihostiocompletionmanagerbind-method"></a>IHostIoCompletionManager::Bind — Metoda
Wiąże określone dojście do portu ukończenia operacji We/Wy, który został utworzony przez wcześniejsze wywołanie [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `hPort`  
 [in] Portu zakończenia We/Wy, dla której chcesz powiązać `hHandle`. Jeśli wartość `hPort` ma wartość null, `hHandle` jest powiązany z domyślnego portu zakończenia We/Wy.  
  
 `hHandle`  
 [in] Dojście systemu operacyjnego, aby powiązać `hPort`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`Bind` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Port wykonywania operacji We/Wy jest tworzona przy użyciu wywołania `CreateIoCompletionPort`. CLR wywołuje `Bind` powiązać dojścia do tego portu.  
  
> [!NOTE]
>  Po zakończeniu żądania We/Wy, host musi wywołać [iclriocompletionmanager::onComplete —](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICLRIoCompletionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
