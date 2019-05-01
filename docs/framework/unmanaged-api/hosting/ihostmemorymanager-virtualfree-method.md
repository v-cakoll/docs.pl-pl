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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03cac2b8433d6491d1fa474a0d4064ef4e260d6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993229"
---
# <a name="ihostmemorymanagervirtualfree-method"></a>IHostMemoryManager::VirtualFree — Metoda
Służy jako logiczne otoki dla odpowiedniej funkcji Win32. Implementacja Win32 `VirtualFree` zwalnia, anuluje, zwalnia lub anuluje region stron w wirtualnej przestrzeni adresowej procesu wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT VirtualFree (  
    [in] LPVOID  lpAddress,  
    [in] SIZE_T  dwSize,  
    [in] DWORD   dwFreeType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lpAddress`  
 [in] Wskaźnik na adres bazowy stron pamięci wirtualnej, który ma zostać zwolniony.  
  
 `dwSize`  
 [in] Rozmiar w bajtach, region, który ma zostać zwolniony.  
  
 `dwFreeType`  
 [in] Typ zwalnianie operacji.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`VirtualFree` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_INVALIDOPERATION|Nastąpiła próba, aby zwolnić pamięć, która nie została przydzielona za pośrednictwem hosta.|  
  
## <a name="remarks"></a>Uwagi  
 `VirtualFree` zwalnia strony pamięci wirtualnej skojarzone z `lpAddress` parametru za pomocą podczas wcześniejszego wywołania [ihostmemorymanager::VirtualAlloc —](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md) funkcji. Próbuje zwolnić pamięć, która nie została przydzielona za pośrednictwem hosta powinien zwrócić HOST_E_INVALIDOPERATION.  
  
 Semantyka są identyczne z tymi wdrożenia Win32 `VirtualFree`. Aby uzyskać więcej informacji zobacz dokumentację platformy Windows.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IHostMemoryManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [IHostMalloc, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
