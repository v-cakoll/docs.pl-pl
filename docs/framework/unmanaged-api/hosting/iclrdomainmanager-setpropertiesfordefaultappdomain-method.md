---
title: ICLRDomainManager::SetPropertiesForDefaultAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f107847ddd48805f4779ff94c4e436a176688030
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699028"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a>ICLRDomainManager::SetPropertiesForDefaultAppDomain — Metoda
Ustawia właściwości, które będą używane do zainicjowania domyślnej domeny aplikacji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `nProperties`  
 [in] Liczba wpisów w `pwszPropertyNames` i `pwszPropertyValues`.  
  
 `pwszPropertyNames`  
 [in] Tablica nazw właściwości lub wartość null, jeśli nie ma żadnych właściwości. Obecnie nazwa tylko właściwości, który jest rozpoznawany przez tę metodę jest "PARTIAL_TRUST_VISIBLE_ASSEMBLIES".  
  
 `pwszPropertyValues`  
 [in] Tablica wartości właściwości lub wartość null, jeśli nie ma żadnych właściwości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Metoda została ukończona pomyślnie.|  
|HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)|`pwszPropertyNames` zawiera nazwę właściwości, który nie jest rozpoznawany przez tę metodę.|  
  
## <a name="remarks"></a>Uwagi  
 Wartość właściwości "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" znajduje się lista zestawów, które mają warunkową <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA) z <xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType> flagi, które mają być widoczne dla częściowo zaufanego kodu wywołującego w domyślnej aplikacji w domenie.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
