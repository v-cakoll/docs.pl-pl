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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c85888e9d29e7b3ae6ad76d1e534e08a4603ed2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499028"
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>ICLRRuntimeInfo::BindAsLegacyV2Runtime — Metoda
Wiąże bieżącego środowiska uruchomieniowego dla wszystkich starszych wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) w wersji 2 aktywacji decyzji dotyczących zasad.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT:  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Wiązanie zakończyło się pomyślnie lub tego środowiska wykonawczego został już powiązany jako starszych wersji 2 aktywacji zasad środowisko uruchomieniowe CLR.|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|Środowiskiem uruchomieniowym w różnych była już powiązana starsze zasady 2 aktywacji wersji środowiska CLR.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli bieżącego środowiska uruchomieniowego jest już powiązany dla wszystkich starszej wersji środowiska CLR w wersji 2 aktywacji decyzji dotyczących zasad (na przykład za pomocą `useLegacyV2RuntimeActivationPolicy` atrybutu na [ \<uruchamiania > element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) w pliku konfiguracyjnym), ta metoda Zwraca wynik błędu; Zamiast tego wynik jest S_OK, tak, jak możesz ją, jeśli metoda było pomyślnie powiązane zasady aktywacji starszej wersji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [\<Uruchamianie > Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
