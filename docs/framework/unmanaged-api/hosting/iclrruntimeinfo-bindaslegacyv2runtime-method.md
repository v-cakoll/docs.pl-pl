---
title: "ICLRRuntimeInfo::BindAsLegacyV2Runtime — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.BindAsLegacyV2Runtime
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::BindAsLegacyV2Runtime
helpviewer_keywords:
- ICLRRuntimeInfo::BindAsLegacyV2Runtime method [.NET Framework hosting]
- BindAsLegacyV2Runtime method [.NET Framework hosting]
ms.assetid: 65fd55ac-4a24-4479-9384-a2e8013bfb2b
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5552214f722cd7f9a56c2fce1e7c67de41d5bb1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfobindaslegacyv2runtime-method"></a>ICLRRuntimeInfo::BindAsLegacyV2Runtime — Metoda
Wiąże bieżącego środowiska uruchomieniowego dla wszystkich starszych wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) w wersji 2 aktywacji decyzji dotyczących zasad.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT BindAsLegacyV2Runtime ();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT:  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Wiązanie zakończyło się pomyślnie albo tego środowiska wykonawczego został już powiązany jako starszych wersji 2 aktywacji zasad środowisko uruchomieniowe CLR.|  
|CLR_E_SHIM_LEGACYRUNTIMEALREADYBOUND|Różne środowiska wykonawczego został już powiązany z starszej wersji zasad 2 aktywacji wersji środowiska CLR.|  
  
## <a name="remarks"></a>Uwagi  
 Jeśli bieżącego środowiska uruchomieniowego jest już powiązany dla wszystkich starszej wersji środowiska CLR w wersji 2 aktywacji decyzji dotyczących zasad (na przykład za pomocą `useLegacyV2RuntimeActivationPolicy` atrybutu [ \<uruchamiania > elementu](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) w pliku konfiguracji), metoda Zwraca wynik błędu; Zamiast tego wynikiem jest wartość S_OK, tak samo, jak możesz ją, jeśli metoda ma pomyślnie powiązany zasad aktywacji starszych wersji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [\<Uruchamianie > — Element](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)
