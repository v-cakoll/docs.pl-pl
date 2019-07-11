---
title: IHostMemoryManager::VirtualQuery — Metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualQuery
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualQuery
helpviewer_keywords:
- IHostMemoryManager::VirtualQuery method [.NET Framework hosting]
- VirtualQuery method [.NET Framework hosting]
ms.assetid: 757af1e6-b9e8-49e7-b5db-342be3aa205f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 684d5e41e1d7cee2775aa0988d33a974315eac4e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772737"
---
# <a name="ihostmemorymanagervirtualquery-method"></a>IHostMemoryManager::VirtualQuery — Metoda
Służy jako logiczne otoki dla odpowiedniej funkcji Win32. Implementacja Win32 `VirtualQuery` pobiera informacje o zakres stron w wirtualnej przestrzeni adresowej procesu wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `lpAddress`  
 [in] Wskaźnik na adres pamięci wirtualnej, można wykonywać zapytania.  
  
 `lpBuffer`  
 [out] Wskaźnik do struktury, która zawiera informacje o pamięci w określonym regionie.  
  
 `dwLength`  
 [in] Rozmiar w bajtach rozmiar buforu, `lpBuffer` wskazuje.  
  
 `pResult`  
 [out] Wskaźnik do liczby bajtów zwróconych przez bufor informacji.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`VirtualQuery` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `VirtualQuery` zawiera informacje dotyczące zakresu stron w wirtualnej przestrzeni adresowej procesu wywołującego. Ta implementacja ustawia wartość `pResult` parametru, aby liczba bajtów zwracane w buforze informacji i zwraca wartość HRESULT. W systemie Win32 `VirtualQuery` funkcji, wartość zwracana jest rozmiar buforu. Aby uzyskać więcej informacji zobacz dokumentację platformy Windows.  
  
> [!IMPORTANT]
>  Wdrożenia systemu operacyjnego `VirtualQuery` nie są naliczane zakleszczeń i można uruchomić w celu ukończenia z losową wątkami w kodzie użytkownika. Ostrożność bardzo zaimplementowanie wersji hostowanych przez tę metodę.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IHostMemoryManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
