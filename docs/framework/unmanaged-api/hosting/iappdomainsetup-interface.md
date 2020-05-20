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
ms.openlocfilehash: 1726f8929404e0dde979972d7830a6951dd71891
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617064"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup — Interfejs
Udostępnia właściwości, które umożliwiają hostowi skonfigurowanie <xref:System.AppDomain?displayProperty=nameWithType> typu przed wywołaniem metody [ICorRuntimeHost:: CreateDomainEx —](icorruntimehost-createdomainex-method.md) , aby ją utworzyć.  
  
## <a name="properties"></a>Właściwości  
  
|Właściwość|Opis|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|Pobiera lub ustawia nazwę katalogu, który zawiera aplikację.|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|Pobiera lub ustawia nazwę aplikacji.|  
|<xref:System.AppDomainSetup.CachePath%2A>|Pobiera lub ustawia nazwę obszaru określonego dla aplikacji, w której pliki są kopiowane w tle.|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|Pobiera lub ustawia nazwę pliku konfiguracji dla aplikacji.|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|Pobiera lub ustawia nazwę katalogu, w którym są przechowywane i dostępne dynamicznie generowane pliki.|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|Pobiera lub ustawia ścieżkę do pliku licencji skojarzonego z tą domeną.|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|Pobiera lub ustawia listę katalogów połączonych z <xref:System.AppDomainSetup.ApplicationBase%2A> katalogiem w celu sondowania zestawów prywatnych.|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|Pobiera lub ustawia wartość ciągu, która zawiera lub wyklucza <xref:System.AppDomainSetup.ApplicationBase%2A> ścieżkę wyszukiwania dla aplikacji.|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|Pobiera lub ustawia nazwy katalogów, które zawierają zestawy przeznaczone do kopiowania w tle.|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|Pobiera lub ustawia ciąg, który wskazuje, czy kopiowanie w tle jest włączone czy wyłączone. Prawidłowe wartości to "true" lub "false".|  
  
## <a name="remarks"></a>Uwagi  
 `IAppDomainSetup`Interfejs odpowiada zarządzanemu <xref:System.IAppDomainSetup> interfejsowi, który <xref:System.AppDomainSetup> implementuje typ. <xref:System.IAppDomainSetup?displayProperty=nameWithType>Szczegółowe opisy jego właściwości można znaleźć w temacie.  
  
 `IAppDomainSetup`reprezentuje informacje o powiązaniu zestawu, które można dodać do <xref:System.AppDomain> wystąpienia przed jego utworzeniem. Na przykład host może ustawić <xref:System.AppDomainSetup.ApplicationBase%2A> Właściwość, aby ustanowić katalog główny, który sond środowiska uruchomieniowego języka wspólnego (CLR) dla zestawów zarządzanych.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [Hosting, interfejsy](hosting-interfaces.md)
