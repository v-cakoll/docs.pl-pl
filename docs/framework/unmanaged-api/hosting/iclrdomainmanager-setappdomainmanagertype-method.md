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
ms.openlocfilehash: 9b142f1a05036eddf44c69d8b7da95091dc8f445
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963094"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType — Metoda
Określa typ, który pochodzi od <xref:System.AppDomainManager?displayProperty=nameWithType> klasy, Menedżera domeny aplikacji, który będzie używany do inicjowania domyślnej domeny aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `wszAppDomainManagerAssembly`  
 podczas Nazwa wyświetlana zestawu zawierającego typ Menedżera domeny aplikacji; na przykład: "AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".  
  
 `wszAppDomainManagerType`  
 podczas Nazwa typu Menedżera domeny aplikacji, łącznie z przestrzenią nazw.  
  
 `dwInitializeDomainFlags`  
 podczas Kombinacja [EInitializeNewDomainFlags —](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) wartości wyliczenia, które zawierają informacje o Menedżerze domeny aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określone wartości HRESULT oraz błędy HRESULT wskazujące niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
  
## <a name="remarks"></a>Uwagi  
 Obecnie jedyną zdefiniowaną wartością dla elementu `dwInitializeDomainFlags` jest `eInitializeNewDomainFlags_NoSecurityChanges`, która informuje środowisko uruchomieniowe języka wspólnego (CLR), że Menedżer domeny aplikacji nie zmodyfikuje ustawień zabezpieczeń <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> podczas wykonywania metody. Dzięki temu środowisko CLR optymalizuje ładowanie zestawów, które mają atrybut Conditional <xref:System.Security.AllowPartiallyTrustedCallersAttribute> (APTCA). Może to spowodować znaczne zwiększenie czasu uruchamiania, jeśli zamknięcie przechodnie tego zestawu zestawów jest duże.  
  
> [!IMPORTANT]
> Jeśli host określi `eInitializeNewDomainFlags_NoSecurityChanges` Menedżera domeny aplikacji <xref:System.InvalidOperationException> , jest zgłaszany w przypadku każdej próby zmodyfikowania zabezpieczeń domeny aplikacji.  
  
 Wywołanie metody [ICLRControl:: SetAppDomainManagerType —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)jest równoważne wywołaniu `ICLRDomainManager::SetAppDomainManagerType` with `eInitializeNewDomainFlags_None`.  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówki** MetaHost.h  
  
 **Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
