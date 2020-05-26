---
title: IHostCrst::SetSpinCount — Metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.SetSpinCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::SetSpinCount
helpviewer_keywords:
- IHostCrst::SetSpinCount method [.NET Framework hosting]
- SetSpinCount method [.NET Framework hosting]
ms.assetid: 863fc8ce-9b8a-477e-8dd8-75c8544bb43a
topic_type:
- apiref
ms.openlocfilehash: 2436809f35d5c46416f48987cc92feb51d291a6a
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804881"
---
# <a name="ihostcrstsetspincount-method"></a>IHostCrst::SetSpinCount — Metoda
Ustawia liczbę obrotów dla bieżącego wystąpienia [IHostCrst](ihostcrst-interface.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetSpinCount (  
    [in] DWORD dwSpinCount  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwSpinCount`  
 podczas Nowa liczba obrotów dla bieżącego `IHostCrst` wystąpienia.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`SetSpinCount`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 W przypadku systemów wieloprocesorowych, jeśli Sekcja krytyczna reprezentowana przez bieżące `IHostCrst` wystąpienie jest niedostępna, wywołujący wątek zostanie `dwSpinCount` opóźniony przed wywołaniem [IHostSemaphore:: Poczekaj](ihostsemaphore-wait-method.md) na semafor skojarzony z sekcją krytyczną. Jeśli Sekcja krytyczna zostanie zwolniona podczas operacji pokrętła, wątek wywołujący unika operacji oczekiwania.  
  
 Użycie `dwSpinCount` jest identyczne z użyciem parametru o tej samej nazwie w `InitializeCriticalSectionAndSpinCount` funkcji Win32.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICLRSyncManager — Interfejs](iclrsyncmanager-interface.md)
- [IHostCrst, interfejs](ihostcrst-interface.md)
- [IHostSyncManager, interfejs](ihostsyncmanager-interface.md)
