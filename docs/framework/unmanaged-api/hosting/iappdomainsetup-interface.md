---
title: IAppDomainSetup — Interfejs
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbde873481aea9de94862117a99079301965f33c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220074"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup — Interfejs
Udostępnia właściwości umożliwiające hosta skonfigurować <xref:System.AppDomain?displayProperty=nameWithType> typ przed wywołaniem [icorruntimehost::createdomainex —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metodę, aby go utworzyć.  
  
## <a name="properties"></a>Właściwości  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Pobiera lub ustawia nazwę katalogu, który zawiera aplikację.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Pobiera lub ustawia nazwę aplikacji.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Pobiera lub ustawia nazwę obszaru określonych aplikacji której pliki są kopiowane w tle.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Pobiera lub ustawia nazwę pliku konfiguracji aplikacji.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Pobiera lub ustawia nazwę katalogu, gdzie przechowywane dynamicznie generowanych plików i dostępne.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Pobiera lub ustawia ścieżkę do pliku licencji, który jest skojarzony z tą domeną.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Pobiera lub ustawia listę katalogów w połączeniu z <xref:System.AppDomainSetup.ApplicationBase%2A> katalogu, aby sondować zestawy prywatne.|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|Pobiera lub ustawia wartość ciągu, która obejmuje lub wyklucza <xref:System.AppDomainSetup.ApplicationBase%2A> ze ścieżki wyszukiwania dla aplikacji.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Pobiera lub ustawia nazwy katalogów, które zawierają zestawy być kopiowane w tle.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Pobiera lub ustawia ciąg, który wskazuje, czy kopiowanie w tle jest włączony lub wyłączony. Prawidłowe wartości to "true" lub "false".|  
  
## <a name="remarks"></a>Uwagi  
 `IAppDomainSetup` Interfejsu odnosi się do zarządzanej <xref:System.IAppDomainSetup> interfejsu, który <xref:System.AppDomainSetup> typ implementuje. Zobacz <xref:System.IAppDomainSetup?displayProperty=nameWithType> szczegółowe opisy jego właściwości.  
  
 `IAppDomainSetup` przedstawia informacje o powiązań zestawów, które mogą być dodawane do <xref:System.AppDomain> wystąpienia przed jego utworzenia. Na przykład można ustawić hosta <xref:System.AppDomainSetup.ApplicationBase%2A> zarządzane zestawy, właściwość, aby ustanowić katalogu głównego sondy środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [Hosting — Interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
