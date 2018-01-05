---
title: "ICLRErrorReportingManager::BeginCustomDump — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager.BeginCustomDump
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d09afd9fe0a2905c79ffb2d50b342041865b593b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a>ICLRErrorReportingManager::BeginCustomDump — Metoda
Określa konfigurację zrzuty stosu niestandardowych dla usługi raportowania błędów.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFlavor`  
 [in] A [ECustomDumpFlavor](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md) wartość, która wskazuje rodzaj zrzutu sterty umożliwiającego tworzenie zrzutu sterty niestandardowych.  
  
 `dwNumItems`  
 [in] Długość `items` tablicy. Jeśli `dwFlavor` DUMP_FLAVOR_Mini, nie jest `dwNumItems` powinna wynosić zero.  
  
 `items`  
 [in] Tablica [CustomDumpItem](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md) wystąpień, określając elementy do dodania do mini zrzutu. Jeśli `dwFlavor` DUMP_FLAVOR_Mini, nie jest `items` może mieć wartości null.  
  
 `dwReserved`  
 [in] Zarezerwowane do użytku w przyszłości.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda zwróciła pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `BeginCustomDump` Metody Ustawia konfigurację zrzutu sterty niestandardowych. [EndCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md) metody czyści konfiguracji zrzutu sterty niestandardowych i zwalnia każdy stan skojarzony. Należy wywołać po wykonaniu zrzutu sterty niestandardowych.  
  
> [!IMPORTANT]
>  Nie można wywołać `EndCustomDump` powoduje, że nastąpił przeciek pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [CustomDumpItem, struktura](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 [ECustomDumpFlavor, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 [ICLRErrorReportingManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
