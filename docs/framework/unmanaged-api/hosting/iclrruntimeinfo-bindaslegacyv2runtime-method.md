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
ms.openlocfilehash: 4390f379e5092cc59d123631f5e6d8da82e2bd7f
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703893"
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
 Jeśli bieżące środowisko uruchomieniowe jest już powiązane ze wszystkimi decyzjami dotyczącymi starszych zasad aktywacji środowiska CLR w wersji 2 (na przykład przy użyciu `useLegacyV2RuntimeActivationPolicy` atrybutu [ \< elementu> startowego](../../configure-apps/file-schema/startup/startup-element.md) w pliku konfiguracji), ta metoda nie zwraca wyniku błędu; zamiast tego wynik jest S_OK, tak jak gdyby metoda pomyślnie powiązana z starszą zasadą aktywacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Obiekt ServiceHost. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeInfo, interfejs](iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
- [Hosting](index.md)
- [\<> uruchomienia — element](../../configure-apps/file-schema/startup/startup-element.md)
