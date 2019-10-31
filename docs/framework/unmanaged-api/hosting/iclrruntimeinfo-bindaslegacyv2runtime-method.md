---
title: ICLRRuntimeInfo::BindAsLegacyV2Runtime — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type:
- apiref
ms.openlocfilehash: d37ec8e17e62f58212a5f79f4d6b6aa75f57bf7c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120257"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>ICLRRuntimeInfo::BindAsLegacyV2Runtime — Metoda
Wiąże bieżące środowisko uruchomieniowe dla wszystkich starszych decyzji zasad aktywacji środowiska uruchomieniowego języka wspólnego (CLR) w wersji 2.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT:  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Powiązanie zakończyło się pomyślnie lub to środowisko uruchomieniowe zostało już powiązane jako starsze środowisko uruchomieniowe zasad aktywacji środowiska CLR w wersji 2.|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|Inne środowisko uruchomieniowe zostało już powiązane ze starszymi zasadami aktywacji środowiska CLR w wersji 2.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli bieżące środowisko uruchomieniowe jest już powiązane ze wszystkimi decyzjami dotyczącymi starszych zasad aktywacji środowiska CLR w wersji 2 (na przykład przy użyciu atrybutu `useLegacyV2RuntimeActivationPolicy` w [elemencie > start\<](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) w pliku konfiguracji), ta metoda nie zwróci wyniku błędu; Zamiast tego wynik jest S_OK, tak jak gdyby metoda pomyślnie powiązana z starszą zasadą aktywacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [\<> uruchomienia elementu](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
