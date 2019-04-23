---
title: ICorRuntimeHost::CreateDomainEx — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a538f14e7dbf24a94343f364201e968bffa757f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59158928"
---
# <a name="icorruntimehostcreatedomainex-method"></a>ICorRuntimeHost::CreateDomainEx — Metoda
Tworzy domenę aplikacji. Obiekt wywołujący odbierze wskaźnika interfejsu typu <xref:System._AppDomain>, do wystąpienia typu <xref:System.AppDomain?displayProperty=nameWithType>. Ta metoda umożliwia obiektowi wywołującemu Przekaż wystąpienie iappdomainsetup — Aby skonfigurować dodatkowe funkcje zwracanego <xref:System._AppDomain> wystąpienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzFriendlyName`  
 [in] Opcjonalny parametr umożliwia oferowanie przyjazną nazwę domeny. Ta przyjazna nazwa może wyświetlana w interfejsie użytkownika, takich jak debugery do identyfikowania domeny.  
  
 `pSetup`  
 [in] Opcjonalny interfejs wskaźnika typu `IAppDomainSetup`uzyskanej przez wywołanie [icorruntimehost::createdomainsetup —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) metody.  
  
 `pIdentityArray`  
 [in] Opcjonalną tablicę wskaźników do `IIdentity` wystąpień, które reprezentują dowód mapowany za pomocą zasad zabezpieczeń, aby ustanowić zestaw uprawnień. `IIdentity` Obiektu można uzyskać przez wywołanie metody [createevidence —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) metody.  
  
 `pAppDomain`  
 [out] Wskaźnik interfejsu typu <xref:System._AppDomain> do wystąpienia <xref:System.AppDomain?displayProperty=nameWithType> można jeszcze bardziej kontrolować domeny.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Operacja zakończyła się pomyślnie.|  
|S_FALSE|Nie można ukończyć operacji.|  
|E_FAIL|Wystąpił błąd nieznanego, krytycznego. Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w procesie. Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
  
## <a name="remarks"></a>Uwagi  
 `CreateDomainEx` Rozszerza możliwości [createdomain —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) , umożliwiając obiekt wywołujący, aby przekazać `IAppDomainSetup` wystąpienie o wartości właściwości — konfigurowanie domeny aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersja programu .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Zobacz także

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [CreateDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)
- [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
