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
ms.openlocfilehash: de41b5e0aaf835ee2d4e4f32696fe104d5830b57
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804450"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a>IHostMemoryManager::VirtualAlloc — Metoda
Służy jako otoka logiczna dla odpowiadającej jej funkcji Win32. Implementacja Win32 `VirtualAlloc` rezerwuje lub zatwierdza region stron w wirtualnej przestrzeni adresowej procesu wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 podczas Wskaźnik do adresu początkowego regionu do przydzielenia.  
  
 `dwSize`  
 podczas Rozmiar, w bajtach, regionu.  
  
 `flAllocationType`  
 podczas Typ alokacji pamięci.  
  
 `flProtect`  
 podczas Ochrona pamięci dla regionu stron do przydzielenia.  
  
 `dwCriticalLevel`  
 podczas Wartość [EMemoryCriticalLevel —](ememorycriticallevel-enumeration.md) , która wskazuje wpływ błędu alokacji.  
  
 `ppMem`  
 określoną Wskaźnik na adres początkowy przydzieloną pamięć lub wartość null, jeśli nie można spełnić żądania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`VirtualAlloc`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Za mało dostępnej pamięci, aby ukończyć żądanie alokacji|  
  
## <a name="remarks"></a>Uwagi  
 Zarezerwuj region w przestrzeni adresowej procesu przez wywołanie `VirtualAlloc` . `pAddress`Parametr zawiera początkowy adres żądanego bloku pamięci. Ten parametr ma zazwyczaj wartość null. System operacyjny przechowuje rekord bezpłatnych zakresów adresów dostępnych dla danego procesu. `pAddress`Wartość null powoduje, że system rezerwuje region wszędzie tam, gdzie jest to zgodne. Alternatywnie można podać konkretny adres początkowy bloku pamięci. W obu przypadkach parametr wyjściowy `ppMem` jest zwracany jako wskaźnik do przydzieloną pamięci. Sama funkcja zwraca wartość HRESULT.  
  
 Funkcja Win32 nie `VirtualAlloc` ma `ppMem` parametru i zwraca zamiast niego wskaźnik do przydzieloną pamięci. Aby uzyskać więcej informacji, zobacz dokumentację platformy systemu Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IHostMemoryManager, interfejs](ihostmemorymanager-interface.md)
