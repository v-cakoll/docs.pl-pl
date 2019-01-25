---
title: ICLRAppDomainResourceMonitor — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ee76f894d31fd65fd31011f33f7363f1b09de31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54726809"
---
# <a name="iclrappdomainresourcemonitor-interface"></a>ICLRAppDomainResourceMonitor — Interfejs
Udostępnia metody, które Sprawdź domenę aplikacji pamięci i Procesora CPU.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetCurrentAllocated, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)|Pobiera całkowity rozmiar w bajtach, wszystkie alokacje pamięci, które zostały wprowadzone przez domenę aplikacji, ponieważ został utworzony, bez odjęcie ilości pamięci, która została zebranych elementów bezużytecznych.|  
|[GetCurrentSurvived, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|Pobiera liczbę bajtów, które przetrwały ostatniej pełnej, blokowanie wyrzucania elementów bezużytecznych i które są przywoływane przez bieżącej domeny aplikacji.|  
|[GetCurrentCpuTime, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)|Pobiera całkowitego czasu procesora użytą przez wszystkie wątki podczas wykonywania w bieżącej domenie aplikacji, od momentu utworzenia domeny aplikacji.|  
  
## <a name="remarks"></a>Uwagi  
 `ICLRAppDomainResourceMonitor` Interfejs zapewnia funkcje podobne do następujących właściwości zarządzane:  
  
-   <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
-   <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MetaHost.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [\<appDomainResourceMonitoring> Element](../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [Monitorowanie zasobów domen aplikacji](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)
