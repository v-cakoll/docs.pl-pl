---
title: IHostMemoryManager::VirtualFree — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualFree
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualFree
helpviewer_keywords:
- IHostMemoryManager::VirtualFree method [.NET Framework hosting]
- VirtualFree method [.NET Framework hosting]
ms.assetid: 1a436e89-eb28-4d15-bcf1-a072f86dbd99
topic_type:
- apiref
ms.openlocfilehash: 4d37b7d803509ebfa861b7502d419f868bd12e11
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804387"
---
# <a name="ihostmemorymanagervirtualfree-method"></a>IHostMemoryManager::VirtualFree — Metoda
Służy jako otoka logiczna dla odpowiadającej jej funkcji Win32. Implementacja Win32 `VirtualFree` zwalnia, decommits lub releases i decommit region stron w wirtualnej przestrzeni adresowej procesu wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lpAddress`  
 podczas Wskaźnik na adres podstawowy stron pamięci wirtualnej, które mają zostać zwolnione.  
  
 `dwSize`  
 podczas Rozmiar, w bajtach, regionu, który ma zostać zwolniony.  
  
 `dwFreeType`  
 podczas Typ operacji zwalniania.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`VirtualFree`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_INVALIDOPERATION|Podjęto próbę zwolnienia pamięci, która nie została przyalokowana przez hosta.|  
  
## <a name="remarks"></a>Uwagi  
 `VirtualFree`zwalnia strony pamięci wirtualnej skojarzone z `lpAddress` parametrem za pomocą wcześniejszego wywołania funkcji [IHostMemoryManager:: funkcja VirtualAlloc](ihostmemorymanager-virtualalloc-method.md) . Próby zwolnienia pamięci, która nie została przydzielono za pomocą hosta, powinny zwrócić HOST_E_INVALIDOPERATION.  
  
 Semantyka jest taka sama jak w przypadku implementacji Win32 `VirtualFree` . Aby uzyskać więcej informacji, zobacz dokumentację platformy systemu Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IHostMemoryManager, interfejs](ihostmemorymanager-interface.md)
- [IHostMalloc, interfejs](ihostmalloc-interface.md)
