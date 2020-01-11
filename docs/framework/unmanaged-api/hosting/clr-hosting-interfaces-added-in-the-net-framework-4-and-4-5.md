---
title: Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: 8484b47549f83795778420048d610e2d1626d87b
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899716"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5
W tej sekcji opisano interfejsy, które mogą być używane przez niezarządzane hosty do integrowania środowiska uruchomieniowego języka wspólnego (CLR) w .NET Framework 4, .NET Framework 4,5 i nowszych wersjach w swoich aplikacjach. Te interfejsy zapewniają metody hosta do konfigurowania i ładowania środowiska uruchomieniowego do procesu.  
  
 Począwszy od .NET Framework 4, wszystkie interfejsy hostingu mają następującą charakterystykę:  
  
- Wykorzystują one zarządzanie okresem istnienia (`AddRef` i `Release`), hermetyzację (niejawny kontekst) i `QueryInterface` z modelu COM.  
  
- Nie używają one typów COM, takich jak `BSTR`, `SAFEARRAY`lub `VARIANT`.  
  
- Nie istnieją modele komórek, agregacja ani aktywacja rejestru, które używają [funkcji CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [ICLRAppDomainResourceMonitor, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 Dostarcza metody, które sprawdzają użycie procesora i pamięci domeny aplikacji.  
  
 [ICLRDomainManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 Umożliwia hostowi określenie Menedżera domeny aplikacji, który będzie używany do inicjowania domyślnej domeny aplikacji, oraz do określania właściwości inicjacji.  
  
 [ICLRGCManager2, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 Udostępnia metodę [SetGCStartupLimitsEx —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) , która umożliwia hostowi Ustawianie rozmiaru segmentu wyrzucania elementów bezużytecznych i maksymalnego rozmiaru generacji 0 systemu wyrzucania elementów bezużytecznych do wartości większej niż `DWORD`.  
  
 [ICLRMetaHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 Dostarcza metody, które zwracają określoną wersję środowiska CLR, wyświetla listę wszystkich zainstalowanych CLRs, wyświetla wszystkie środowiska uruchomieniowe w procesie, zwracają interfejs aktywacji i odnajdują wersję środowiska CLR używaną do kompilowania zestawu.  
  
 [ICLRMetaHostPolicy, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 Udostępnia metodę [GetRequestedRuntime —](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) , która dostarcza interfejs CLR na podstawie kryteriów zasad, zestawu zarządzanego, wersji i pliku konfiguracji.  
  
 [ICLRRuntimeInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 Dostarcza metody, które zwracają informacje dotyczące określonego środowiska uruchomieniowego, w tym wersję, katalog i stan ładowania.  
  
 [ICLRStrongName, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 Udostępnia podstawowe globalne funkcje statyczne do podpisywania zestawów o silnych nazwach. Wszystkie metody [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md) zwracają standardowe wartości HRESULT modelu com.  
  
 [ICLRStrongName2, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 Zapewnia możliwość tworzenia silnych nazw przy użyciu grupy SHA-2 bezpiecznych algorytmów wyznaczania wartości skrótu (SHA-256, SHA-384 i SHA-512).  
  
 [ICLRTask2, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 Oferuje wszystkie funkcje [interfejsu ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); Ponadto udostępnia metody zezwalające na opóźnione przerywanie wątków w bieżącym wątku.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przestarzałe klasy coclass i interfejsy hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Opisuje interfejsy hostingu udostępniane w .NET Framework wersje 1,0 i 1,1.  
  
 [Interfejsy hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 Opisuje interfejsy hostingu udostępniane w .NET Framework wersje 2,0, 3,0 i 3,5.  
  
 [Hosting](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 Wprowadza hosting w .NET Framework.
