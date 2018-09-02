---
title: Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9086502968fb9046237e77b76b4038a9f32f4ef
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407406"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5
W tej sekcji opisano niezarządzane interfejsy hostów można użyć do integracji środowisko uruchomieniowe języka wspólnego (CLR) w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]i nowsze wersje w swoich aplikacjach. Te interfejsy dostarczać metody do hosta skonfigurować i załadowania środowiska uruchomieniowego do procesu.  
  
 Począwszy od [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], hostingu wszystkie interfejsy mają następującą charakterystykę:  
  
-   Używają Zarządzanie okresem istnienia (`AddRef` i `Release`), hermetyzacji (niejawne context) i `QueryInterface` z modelu COM.  
  
-   Istnieje nie należy używać typów modelu COM takich jak `BSTR`, `SAFEARRAY`, lub `VARIANT`.  
  
-   Nie ma żadnych modeli typu apartment, agregacji ani rejestru aktywacji używanego przez [funkcja CoCreateInstance](https://go.microsoft.com/fwlink/?LinkId=142894).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ICLRAppDomainResourceMonitor, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 Udostępnia metody, które Sprawdź domenę aplikacji pamięci i Procesora CPU.  
  
 [ICLRDomainManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 Umożliwia hosta określić Menedżer domeny aplikacji, która będzie służyć do zainicjowania domyślnej domeny aplikacji i określić właściwości inicjowania.  
  
 [ICLRGCManager2, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 Udostępnia [setgcstartuplimitsex —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metody, która umożliwia hosta można skonfigurować rozmiaru segmentu kolekcji wyrzucania elementów i maksymalny rozmiar pamięci systemu kolekcji generacji 0 na wartości większej niż `DWORD`.  
  
 [ICLRMetaHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 Zawiera metody, które zwracają określonej wersji środowiska CLR, listę wszystkich zainstalowanych CLRs, listy wszystkie środowiska uruchomieniowe w trakcie, zwracają interfejs aktywacji i odnajdź wersję środowiska CLR używana do kompilowania zestawu.  
  
 [ICLRMetaHostPolicy, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 Udostępnia [getrequestedruntime —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) metodę, która udostępnia interfejs CLR na podstawie kryteriów zasad, zestaw zarządzany, wersji i pliku konfiguracji.  
  
 [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 Udostępnia metody, które zwracają informacje dotyczące określonego środowiska uruchomieniowego, w tym wersja, katalog i stan obciążenia.  
  
 [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 Zawiera podstawowe statyczne funkcje globalne do podpisywania zestawów o silnych nazwach. Wszystkie [iclrstrongname —](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) metody zwracają standardowa COM wartości HRESULT.  
  
 [ICLRStrongName2, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 Zapewnia możliwość tworzenia silnych nazw za pomocą grupy SHA-2 algorytmów wyznaczania wartości skrótu Secure (SHA-256, SHA-384 i SHA-512).  
  
 [ICLRTask2, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 Oferuje wszystkie funkcje [iclrtask — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); ponadto udostępnia metody, które umożliwiają wątku przerywa opóźnionych w bieżącym wątku.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przestarzałe klasy coclass i interfejsy hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 W tym artykule opisano interfejsami hostingu, wyposażone w wersjach programu .NET Framework 1.0 i 1.1.  
  
 [Interfejsy hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 W tym artykule opisano interfejsami hostingu, wyposażone w .NET Framework w wersji 2.0, 3.0 i 3.5.  
  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 Wprowadza hosting w .NET Framework.
