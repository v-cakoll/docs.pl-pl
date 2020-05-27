---
title: IHostMemoryManager::GetMemoryLoad — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
ms.openlocfilehash: 73d9ae865b2c971a4defcacf5bd6505836c74e02
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804506"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a>IHostMemoryManager::GetMemoryLoad — Metoda
Pobiera ilość pamięci fizycznej, która jest aktualnie używana, i dlatego jest niedostępna, zgodnie z informacjami o hoście.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pMemoryLoad`  
 określoną Wskaźnik do przybliżonej wartości procentowej całkowitej ilości pamięci fizycznej, która jest obecnie używana.  
  
 `pAvailableBytes`  
 określoną Wskaźnik do liczby bajtów dostępnych dla środowiska uruchomieniowego języka wspólnego (CLR).  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`GetMemoryLoad`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `GetMemoryLoad`Zawija `GlobalMemoryStatus` funkcję Win32. Wartość `pMemoryLoad` jest odpowiednikiem `dwMemoryLoad` pola w `MEMORYSTATUS` strukturze zwróconego z `GlobalMemoryStatus` .  
  
 Środowisko uruchomieniowe używa wartości zwracanej jako algorytmu heurystycznego modułu wyrzucania elementów bezużytecznych. Na przykład jeśli Host zgłasza, że większość pamięci jest w użyciu, Moduł wyrzucania elementów bezużytecznych może wybrać zbieranie z wielu generacji w celu zwiększenia ilości pamięci, która może być dostępna.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.GC?displayProperty=nameWithType>
- [IHostMemoryManager, interfejs](ihostmemorymanager-interface.md)
