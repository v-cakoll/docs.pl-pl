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
ms.openlocfilehash: ea10f9b7d23d8ca6a94d05cac6e586b434c000d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435546"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType — Metoda
Określa typ pochodny <xref:System.AppDomainManager?displayProperty=nameWithType> klasy Menedżer domeny aplikacji, które będą używane do inicjowania domyślnej domeny aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `wszAppDomainManagerAssembly`  
 [in] Wyświetlana nazwa zestawu zawierającego typ Menedżer domeny aplikacji; na przykład: "AdMgrExample, Version = 1.0.0.0, Culture = neutral, PublicKeyToken = 6856bccf150f00b3".  
  
 `wszAppDomainManagerType`  
 [in] Nazwa typu Menedżer domeny aplikacji, włącznie z przestrzenią nazw.  
  
 `dwInitializeDomainFlags`  
 [in] Kombinację [EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md) wartości wyliczenia, które zawierają informacje dotyczące Menedżera domeny aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
  
## <a name="remarks"></a>Uwagi  
 Obecnie tylko określone wartości `dwInitializeDomainFlags` jest `eInitializeNewDomainFlags_NoSecurityChanges`, który określa, że środowisko uruchomieniowe języka wspólnego (CLR) czy Menedżer domeny aplikacji nie spowoduje jej modyfikacji ustawień zabezpieczeń podczas wykonywania <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> metody. Dzięki temu CLR w celu zoptymalizowania ładowania zestawów, które mają warunkowe <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA). Może to spowodować znaczne ulepszenia w chwili uruchomienia Jeśli przechodnie zamknięcia to zbiór zestawów jest duży.  
  
> [!IMPORTANT]
>  Jeśli host Określa `eInitializeNewDomainFlags_NoSecurityChanges` Menedżera domeny aplikacji, <xref:System.InvalidOperationException> jest generowany, jeśli wszystkie próby zmodyfikowania bezpieczeństwa domeny aplikacji.  
  
 Wywoływanie [ICLRControl::SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)jest odpowiednikiem wywołania metody `ICLRDomainManager::SetAppDomainManagerType` z `eInitializeNewDomainFlags_None`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 [ICLRDomainManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 [EInitializeNewDomainFlags, wyliczenie](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
