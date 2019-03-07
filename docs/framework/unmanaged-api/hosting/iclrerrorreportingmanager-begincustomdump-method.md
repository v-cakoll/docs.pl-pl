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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af752ae52956ae1d97fb14ec3b494effdaed35c9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496615"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a>ICLRErrorReportingManager::BeginCustomDump — Metoda
Określa konfigurację zrzutów stosu niestandardowych dla usługi raportowania błędów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwFlavor`  
 [in] A [ecustomdumpflavor —](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) wartość wskazującą rodzaj zrzutu sterty, na którym można utworzyć zrzutu sterty niestandardowych.  
  
 `dwNumItems`  
 [in] Długość `items` tablicy. Jeśli `dwFlavor` nie jest DUMP_FLAVOR_Mini, `dwNumItems` powinna wynosić zero.  
  
 `items`  
 [in] Tablica [customdumpitem —](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) wystąpień, określając elementy do dodania do minizrzut. Jeśli `dwFlavor` nie jest DUMP_FLAVOR_Mini, `items` powinien mieć wartość null.  
  
 `dwReserved`  
 [in] Zarezerwowane do użytku w przyszłości.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda zwróciła pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie będzie już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `BeginCustomDump` Metody Ustawia konfigurację zrzutu sterty niestandardowych. [Endcustomdump —](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) metoda czyści konfiguracji zrzutu sterty niestandardowych i zwalnia każdy stan skojarzony. Powinna być wywoływana po wykonaniu zrzutu sterty niestandardowych.  
  
> [!IMPORTANT]
>  Nie można wywołać `EndCustomDump` powoduje, że przecieku pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [CustomDumpItem, struktura](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)
- [ECustomDumpFlavor, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)
- [ICLRErrorReportingManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
