---
title: IHostMemoryManager::VirtualAlloc — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5407a9d23833d73b2d6ef0038454f56f01d56867
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087654"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>IHostMemoryManager::VirtualAlloc — Metoda
Służy jako logiczne otoki dla odpowiedniej funkcji Win32. Implementacja Win32 `VirtualAlloc` rezerwuje lub zwalnia region stron w wirtualnej przestrzeni adresowej procesu wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAddress`  
 [in] Wskaźnik do adres początkowy regionów do przydzielenia.  
  
 `dwSize`  
 [in] Rozmiar w bajtach, regionu.  
  
 `flAllocationType`  
 [in] Typ alokacji pamięci.  
  
 `flProtect`  
 [in] Ochrona pamięci dla regionu stron do przydzielenia.  
  
 `dwCriticalLevel`  
 [in] [Ememorycriticallevel —](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) wartość, która wskazuje wpływ wystąpił błąd alokacji.  
  
 `ppMem`  
 [out] Wskaźnik na adres początkowy ilość przydzielonej pamięci lub wartość null, jeśli żądanie nie mogło zostać spełnione.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Za mało pamięci była dostępna do wykonania żądania alokacji|  
  
## <a name="remarks"></a>Uwagi  
 Możesz zarezerwować region przestrzeni adresowej procesu, wywołując `VirtualAlloc`. `pAddress` Parametr zawiera adres początkowy bloku pamięci, które chcesz. Ten parametr jest zazwyczaj ustawiony na wartość null. System operacyjny jest rejestrowana wolnego adresu zakresy dostępne w danym procesie. A `pAddress` wartości null powoduje, że systemu, aby zarezerwować region wszędzie tam, gdzie za stosowny. Alternatywnie możesz podać określony adres początkowy dla bloku pamięci. W obu przypadkach, parametr wyjściowy `ppMem` jest zwracana jako wskaźnik do alokacji pamięci. Ta funkcja zwraca wartość HRESULT.  
  
 Win32 `VirtualAlloc` funkcja nie ma `ppMem` parametru, a zamiast tego zwraca wskaźnik do ilość przydzielonej pamięci. Aby uzyskać więcej informacji zobacz dokumentację platformy Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IHostMemoryManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
