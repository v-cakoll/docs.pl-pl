---
title: "ICorRuntimeHost::CreateDomainEx — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateDomainEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 042befa2dd96ad9f6e6dd3069ba2c4aabcd146fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcreatedomainex-method"></a>ICorRuntimeHost::CreateDomainEx — Metoda
Tworzy domeny aplikacji. Obiekt wywołujący uzyskuje wskaźnika interfejsu typu <xref:System._AppDomain>, aby wystąpienie typu <xref:System.AppDomain?displayProperty=nameWithType>. Ta metoda umożliwia obiekt wywołujący, aby przekazać wystąpienia IAppDomainSetup Konfigurowanie dodatkowych funkcji zwracana <xref:System._AppDomain> wystąpienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pwzFriendlyName`  
 [in] Parametr opcjonalny używany do nadaj przyjazną nazwę do domeny. Przyjazna nazwa mogą być wyświetlane w interfejsów użytkownika, takich jak debugera, aby zidentyfikować domenę.  
  
 `pSetup`  
 [in] Wskaźnik interfejsu opcjonalne typu `IAppDomainSetup`, uzyskany przez wywołanie do [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) metody.  
  
 `pIdentityArray`  
 [in] Opcjonalne tablicy wskaźników do `IIdentity` wystąpień, które reprezentują dowód mapowany za pomocą zasad zabezpieczeń do ustalenia zestawu uprawnień. `IIdentity` Obiektu można uzyskać przez wywołanie metody [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) metody.  
  
 `pAppDomain`  
 [out] Wskaźnik interfejsu typu <xref:System._AppDomain> na wystąpienie <xref:System.AppDomain?displayProperty=nameWithType> można dodatkowo kontrolować domeny.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Operacja powiodła się.|  
|WARTOŚCI S_FALSE|Nie można ukończyć operacji.|  
|E_FAIL|Wystąpił nieznany, poważnej awarii. Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie będzie już można używać w procesie. Kolejne wywołania żadnych hostingu interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
  
## <a name="remarks"></a>Uwagi  
 `CreateDomainEx`Rozszerza możliwości [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) przez obiekt wywołujący, aby przekazać `IAppDomainSetup` wystąpienia o wartości właściwości do konfigurowania domeny aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersja platformy .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [CreateDomain — metoda](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)  
 [ICorRuntimeHost — interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
