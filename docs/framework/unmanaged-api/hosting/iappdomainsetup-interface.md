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
ms.openlocfilehash: 0fab64c31d4a73995c16d21767f4569f21c7df9a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126871"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup — Interfejs
Udostępnia właściwości, które umożliwiają hostowi skonfigurowanie typu <xref:System.AppDomain?displayProperty=nameWithType> przed wywołaniem metody [ICorRuntimeHost:: CreateDomainEx —](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) , aby ją utworzyć.  
  
## <a name="properties"></a>Właściwości  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Pobiera lub ustawia nazwę katalogu, który zawiera aplikację.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Pobiera lub ustawia nazwę aplikacji.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Pobiera lub ustawia nazwę obszaru określonego dla aplikacji, w której pliki są kopiowane w tle.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Pobiera lub ustawia nazwę pliku konfiguracji dla aplikacji.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Pobiera lub ustawia nazwę katalogu, w którym są przechowywane i dostępne dynamicznie generowane pliki.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Pobiera lub ustawia ścieżkę do pliku licencji skojarzonego z tą domeną.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Pobiera lub ustawia listę katalogów połączonych z katalogiem <xref:System.AppDomainSetup.ApplicationBase%2A> w celu sondowania zestawów prywatnych.|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|Pobiera lub ustawia wartość ciągu, która zawiera lub wyklucza <xref:System.AppDomainSetup.ApplicationBase%2A> ze ścieżki wyszukiwania dla aplikacji.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Pobiera lub ustawia nazwy katalogów, które zawierają zestawy przeznaczone do kopiowania w tle.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Pobiera lub ustawia ciąg, który wskazuje, czy kopiowanie w tle jest włączone czy wyłączone. Prawidłowe wartości to "true" lub "false".|  
  
## <a name="remarks"></a>Uwagi  
 Interfejs `IAppDomainSetup` odpowiada interfejsowi zarządzanemu <xref:System.IAppDomainSetup>, który implementuje typ <xref:System.AppDomainSetup>. Zobacz <xref:System.IAppDomainSetup?displayProperty=nameWithType>, aby uzyskać szczegółowe opisy jego właściwości.  
  
 `IAppDomainSetup` reprezentuje informacje o powiązaniu zestawu, które można dodać do wystąpienia <xref:System.AppDomain> przed jego utworzeniem. Na przykład host może ustawić właściwość <xref:System.AppDomainSetup.ApplicationBase%2A>, aby ustanowić katalog główny, który sond środowiska uruchomieniowego języka wspólnego (CLR) dla zestawów zarządzanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
