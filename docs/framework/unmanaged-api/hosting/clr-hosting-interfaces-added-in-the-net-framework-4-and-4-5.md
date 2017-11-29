---
title: "Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 65d80734bfbe16c8b5052f8de1e4c6280b663707
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5
W tej sekcji opisano interfejsów, które niezarządzanych hostów można użyć do integracji środowisko uruchomieniowe języka wspólnego (CLR) w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]i nowszych wersjach w swoich aplikacjach. Te interfejsy podania metod dla hosta, skonfigurować i załadować środowiska uruchomieniowego do procesu.  
  
 Począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], wszystkie hostingu interfejsów mają następującą charakterystykę:  
  
-   Używają Zarządzanie okresem istnienia (`AddRef` i `Release`), encapsulation (niejawne kontekst) i `QueryInterface` z modelu COM.  
  
-   Brak nie używaj typów COM takich jak `BSTR`, `SAFEARRAY`, lub `VARIANT`.  
  
-   Nie ma żadnych modeli apartamentu, agregacji lub rejestru aktywacji używanego [funkcji CoCreateInstance](http://go.microsoft.com/fwlink/?LinkId=142894).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ICLRAppDomainResourceMonitor — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 Udostępnia metody, które sprawdzić pamięci i Procesora CPU domeny aplikacji.  
  
 [ICLRDomainManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 Umożliwia hosta określić Menedżer domeny aplikacji, który będzie używany do inicjowania domyślnej domeny aplikacji i określić właściwości inicjowania.  
  
 [ICLRGCManager2 — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 Udostępnia [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metodę, która umożliwia hosta można skonfigurować rozmiar segmentu kolekcji pamięci i maksymalny rozmiar pamięci systemu kolekcji pokolenia 0 na wartości większej niż `DWORD`.  
  
 [ICLRMetaHost — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 Udostępnia metody, które zwraca określonej wersji środowiska CLR, wyświetlić listę wszystkich zainstalowanych CLRs listy wszystkich środowisk uruchomieniowych w procesie, zwracać interfejs aktywacji i odnajdywanie wersji środowiska CLR, używana do kompilowania zestawu.  
  
 [ICLRMetaHostPolicy — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 Udostępnia [GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metodę, która zapewnia interfejs CLR na podstawie kryteriów zasad, zestaw zarządzany, wersji i pliku konfiguracji.  
  
 [ICLRRuntimeInfo — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 Udostępnia metody, które zwracają informacje dotyczące określonego środowiska uruchomieniowego, łącznie z wersji, katalogu i stanie obciążenia.  
  
 [ICLRStrongName — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 Podpisywanie zestawów o silnych nazwach zapewnia podstawowe statyczne funkcje globalne. Wszystkie [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) metody zwracają standardowe COM wyników HRESULT.  
  
 [ICLRStrongName2 — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 Zapewnia możliwość tworzenia silnych nazw za pomocą grupy SHA-2 algorytmów wyznaczania wartości skrótu Secure (SHA-256, SHA-384 i SHA-512).  
  
 [ICLRTask2 — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 Zawiera wszystkie funkcje [ICLRTask — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); ponadto udostępnia metody umożliwiające przerwanie wątku opóźnionych w bieżącym wątku.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przestarzałe hostingu interfejsy i współklasy środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Opisuje interfejsy hostingu wersjach systemu .NET Framework 1.0 i 1.1.  
  
 [Interfejsy hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 Opisuje interfejsy hostingu wersjach systemu .NET Framework 2.0, 3.0 i 3.5.  
  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 Wprowadzono w programie .NET Framework — hosting.
