---
title: ICLRDomainManager::SetAppDomainManagerType — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6cfef7d929d40996716a02a4db51630827011a68
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183251"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType — Metoda
Określa typ pochodną <xref:System.AppDomainManager?displayProperty=nameWithType> klasy Menedżer domeny aplikacji, która będzie służyć do zainicjowania domyślnej domeny aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszAppDomainManagerAssembly`  
 [in] Nazwa wyświetlana zestawu, który zawiera typ Menedżera domeny aplikacji; na przykład: "AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".  
  
 `wszAppDomainManagerType`  
 [in] Nazwa typu Menedżer domeny aplikacji, włącznie z przestrzenią nazw.  
  
 `dwInitializeDomainFlags`  
 [in] Kombinacji [einitializenewdomainflags —](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) wartości wyliczenia, które zawierają informacje dotyczące Menedżera domeny aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
  
## <a name="remarks"></a>Uwagi  
 Obecnie tylko określone wartości `dwInitializeDomainFlags` jest `eInitializeNewDomainFlags_NoSecurityChanges`, informuje środowisko uruchomieniowe języka wspólnego (CLR), czy Menedżer domeny aplikacji nie będą modyfikować ustawień zabezpieczeń podczas wykonywania <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody. Dzięki temu CLR do optymalizacji ładowania zestawów, które mają warunkową <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA). Może to spowodować znaczne ulepszenia w czasie uruchamiania Jeśli przechodnie zamknięcia ten zbiór zestawów jest duży.  
  
> [!IMPORTANT]
>  Jeśli host Określa `eInitializeNewDomainFlags_NoSecurityChanges` dla Menedżera domeny aplikacji, <xref:System.InvalidOperationException> jest generowany, jeśli wszystkie podejmowana jest próba zmodyfikowania bezpieczeństwa domeny aplikacji.  
  
 Wywoływanie [iclrcontrol::setappdomainmanagertype —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)metodą jest równoważne z wywoływaniem `ICLRDomainManager::SetAppDomainManagerType` z `eInitializeNewDomainFlags_None`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags — Wyliczenie](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
