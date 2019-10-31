---
title: ICLRErrorReportingManager::BeginCustomDump — Metoda
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.BeginCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type:
- apiref
ms.openlocfilehash: 7153ac214ab99228ac9c59032aa8248d06d14c3b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129295"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a>ICLRErrorReportingManager::BeginCustomDump — Metoda
Określa konfigurację niestandardowych zrzutów sterty dla raportowania błędów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwFlavor`  
 podczas Wartość [ECustomDumpFlavor —](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) , która wskazuje rodzaj zrzutu sterty, na którym ma zostać skompilowany zrzut sterty niestandardowej.  
  
 `dwNumItems`  
 podczas Długość tablicy `items`. Jeśli `dwFlavor` nie jest DUMP_FLAVOR_Mini, `dwNumItems` powinna być równa zero.  
  
 `items`  
 podczas Tablica wystąpień [CustomDumpItem —](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) , określająca elementy, które mają zostać dodane do mini zrzutu. Jeśli `dwFlavor` nie jest DUMP_FLAVOR_Mini, `items` powinna mieć wartość null.  
  
 `dwReserved`  
 podczas Zarezerwowane do użytku w przyszłości.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została pomyślnie zwrócona.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Metoda `BeginCustomDump` ustawia niestandardową konfigurację zrzutu sterty. Metoda [EndCustomDump —](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) czyści konfigurację zrzutu sterty niestandardowej i zwalnia wszystkie skojarzone Stany. Powinien być wywoływany po zakończeniu niestandardowego zrzutu sterty.  
  
> [!IMPORTANT]
> Nie można wywołać `EndCustomDump` powoduje przeciek pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [CustomDumpItem, struktura](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [ECustomDumpFlavor, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [ICLRErrorReportingManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
