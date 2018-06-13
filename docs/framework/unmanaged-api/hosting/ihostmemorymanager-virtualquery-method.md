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
ms.openlocfilehash: 68a9d6ad7470ffaf1143a4a8e3134f20edb9e3c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439221"
---
# <a name="ihostmemorymanagervirtualquery-method"></a>IHostMemoryManager::VirtualQuery — Metoda
Służy jako otoka logiczne dla odpowiedniej funkcji Win32. Implementacja Win32 `VirtualQuery` pobiera informacje o zakresie stron w wirtualnej przestrzeni adresowej procesu wywołującego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT VirtualQuery (  
    [in]  void*    lpAddress,  
    [out] void*    lpBuffer,  
    [in]  SIZE_T   dwLength,  
    [out] SIZE_T*  pResult  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `lpAddress`  
 [in] Wskaźnik do adresów pamięci wirtualnej, można wykonać zapytania.  
  
 `lpBuffer`  
 [out] Wskaźnik do struktury, zawierający informacje o pamięci określonego regionu.  
  
 `dwLength`  
 [in] Rozmiar w bajtach buforu, który `lpBuffer` wskazuje.  
  
 `pResult`  
 [out] Wskaźnik do liczba bajtów zwrócona przez bufor informacji.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`VirtualQuery` zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `VirtualQuery` informacje na temat zakresu stron w wirtualnej przestrzeni adresowej procesu wywołującego. Ta implementacja ustawia wartość `pResult` parametr, aby liczba bajtów zwrócona w buforze informacji i zwraca wartość HRESULT. W systemie Win32 `VirtualQuery` rozmiar buforu jest zwracana wartość funkcji. Aby uzyskać więcej informacji zobacz dokumentację platformy systemu Windows.  
  
> [!IMPORTANT]
>  Wdrożenia systemu operacyjnego `VirtualQuery` nie wpływa negatywnie zakleszczenie i można uruchomić w celu ukończenia z losowe wątków w kodzie użytkownika. Należy zachować ostrożność dużą podczas wdrażania obsługiwane wersji tej metody.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IHostMemoryManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
