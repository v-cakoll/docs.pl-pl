---
title: ICLRErrorReportingManager::EndCustomDump — Metoda
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.EndCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e5e5a594743c5770d4b9f93d4b0949cce24592a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435722"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a>ICLRErrorReportingManager::EndCustomDump — Metoda
Usuwa Konfiguracja zrzutu niestandardowych stosu, który został określony we wcześniejszych wywołanie [ICLRErrorReportingManager::BeginCustomDump](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`EndCustomDump` zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `EndCustomDump` Metody czyści konfiguracji zrzutu stosu niestandardowy ustawiony przez wywołanie wcześniejszych `BeginCustomDump` — metoda i zwalnia każdy stan skojarzony. Należy wywołać po wykonaniu zrzutu stosu niestandardowych.  
  
> [!IMPORTANT]
>  Nie można wywołać `EndCustomDump` powoduje, że nastąpił przeciek pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [CustomDumpItem, struktura](../../../../docs/framework/unmanaged-api/hosting/customdumpitem-structure.md)  
 [ECustomDumpFlavor, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpflavor-enumeration.md)  
 [ICLRErrorReportingManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)
