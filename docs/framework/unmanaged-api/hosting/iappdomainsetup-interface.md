---
title: "IAppDomainSetup — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppDomainSetup
api_location: mscoree.dll
api_type: COM
f1_keywords: IAppDomainSetup
helpviewer_keywords: IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e6ed5ea00799fff70626114257efef2d06b505ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup — Interfejs
Dostarcza właściwości, które umożliwia konfigurowanie hosta <xref:System.AppDomain?displayProperty=nameWithType> typu przed wywołaniem [ICorRuntimeHost::CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metodę, aby go utworzyć.  
  
## <a name="properties"></a>Właściwości  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Pobiera lub ustawia nazwę katalogu, który zawiera aplikację.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Pobiera lub ustawia nazwę aplikacji.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Pobiera lub ustawia nazwę obszaru określonych aplikacji gdy pliki są kopiowane w tle.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Pobiera lub ustawia nazwę pliku konfiguracyjnego aplikacji.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Pobiera lub ustawia nazwę katalogu, w którym przechowywane dynamicznie generowanym plików i dostępne.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Pobiera lub ustawia ścieżkę do pliku licencji, który jest skojarzony z tą domeną.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Pobiera lub ustawia listę katalogów, w połączeniu z <xref:System.AppDomainSetup.ApplicationBase%2A> katalog sondować zestawy prywatne.|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|Pobiera lub ustawia wartość ciągu, która obejmuje lub wyklucza <xref:System.AppDomainSetup.ApplicationBase%2A> ze ścieżki wyszukiwania dla aplikacji.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Pobiera lub ustawia nazwy katalogów, które zawierają zestawy należy skopiować w tle.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Pobiera lub ustawia ciąg, który wskazuje, czy kopiowanie w tle jest włączony czy wyłączony. Prawidłowe wartości to "true" lub "false".|  
  
## <a name="remarks"></a>Uwagi  
 `IAppDomainSetup` Interfejsu odpowiada zarządzanej <xref:System.IAppDomainSetup> interfejsu, który <xref:System.AppDomainSetup> typ implementuje. Zobacz <xref:System.IAppDomainSetup?displayProperty=nameWithType> szczegółowe opisy jego właściwości.  
  
 `IAppDomainSetup`reprezentuje informacje o powiązaniu zestawu, które mogą być dodawane do <xref:System.AppDomain> wystąpienia przed jego utworzenie. Na przykład można ustawić hosta <xref:System.AppDomainSetup.ApplicationBase%2A> właściwości ustanowienie katalogu głównego sondy środowisko uruchomieniowe języka wspólnego (CLR) do zarządzanych zestawów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup>  
 [Hosting — interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
