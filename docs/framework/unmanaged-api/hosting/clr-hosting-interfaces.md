---
title: Interfejsy hostingu środowiska CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: 66fdd97d101f5ea53a96b996a2a60e5ed65a2701
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131969"
---
# <a name="clr-hosting-interfaces"></a>Interfejsy hostingu środowiska CLR
W tej sekcji opisano interfejsy, które mogą być używane przez niezarządzane hosty do integrowania środowiska uruchomieniowego języka wspólnego (CLR) z aplikacjami. Informacje dotyczą .NET Framework w wersji 2,0 i nowszych. Te interfejsy umożliwiają hostowi kontrolowanie wielu innych aspektów środowiska uruchomieniowego niż było możliwe w wersjach 1,0 i 1,1 i zapewniają znacznie ściślejszą integrację między środowiskiem CLR a modelem wykonywania hosta.  
  
 W .NET Framework w wersji 1,0 i 1,1 model hostingu włączył niezarządzany host do załadowania środowiska CLR do procesu, skonfigurowania pewnych ustawień i otrzymywania powiadomień o zdarzeniach. Ogólnie rzecz biorąc, Host i środowisko CLR działały niezależnie w tym procesie. W .NET Framework w wersji 2,0 i nowszych nowe warstwy abstrakcji umożliwiają hostowi udostępnianie wielu zasobów, które są obecnie udostępniane przez typy w zestawie Win32, i poszerzają zestaw funkcji, które mogą być konfigurowane przez hosta.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [IActionOnCLREvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 Zapewnia metodę, która wykonuje wywołanie zwrotne dla zarejestrowanego zdarzenia.  
  
 [IApartmentCallback, interfejs](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 Zapewnia metody tworzenia wywołań zwrotnych w obrębie apartamentu.  
  
 [IAppDomainBinding, interfejs](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 Zapewnia metody ustawiania konfiguracji czasu wykonywania.  
  
 [ICatalogServices, interfejs](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 Dostarcza metody dla usług katalogowych. (Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie).  
  
 [ICLRAssemblyIdentityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 Dostarcza metody, które obsługują komunikację między hostem i środowiskiem CLR o zestawach.  
  
 [ICLRAssemblyReferenceList, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 Zarządza listą zestawów, które są ładowane przez środowisko CLR, a nie przez hosta.  
  
 [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 Zapewnia metody do uzyskiwania dostępu do hosta i konfigurowania różnych aspektów środowiska CLR.  
  
 [ICLRDebugManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 Dostarcza metody, które umożliwiają hostowi kojarzenie zestawu zadań z identyfikatorem i przyjazną nazwą.  
  
 [ICLRErrorReportingManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 Dostarcza metody, które umożliwiają hostowi skonfigurowanie niestandardowych zrzutów sterty na potrzeby raportowania błędów.  
  
 [ICLRGCManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 Dostarcza metody, które umożliwiają hostowi współdziałanie z systemem odzyskiwania pamięci CLR.  
  
 [ICLRHostBindingPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 Zapewnia metody dla hosta do szacowania i przekazywania zmian w informacjach o zasadach dla zestawów.  
  
 [ICLRHostProtectionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 Umożliwia hostowi blokowanie określonych zarządzanych klas, metod, właściwości i pól z uruchamiania w częściowo zaufanym kodzie.  
  
 [ICLRIoCompletionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 Implementuje metodę wywołania zwrotnego, która umożliwia hostowi powiadomienie środowiska CLR o stanie określonych żądań we/wy.  
  
 [ICLRMemoryNotificationCallback, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 Umożliwia hostowi zgłaszanie warunków ciśnienia pamięci przy użyciu podejścia podobnego do funkcji Win32 `CreateMemoryResourceNotification`.  
  
 [ICLROnEventManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 Dostarcza metody, które umożliwiają hostowi rejestrowanie i Wyrejestrowywanie wywołań zwrotnych dla zdarzeń CLR.  
  
 [ICLRPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 Dostarcza metody, które umożliwiają hostowi określenie akcji zasad, które mają być podejmowane w przypadku awarii i przekroczeń limitu czasu.  
  
 [ICLRProbingAssemblyEnum, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 Dostarcza metody, które umożliwiają hostowi pobieranie tożsamości dla zestawu przy użyciu informacji o tożsamości zestawu, które są wewnętrzne dla środowiska CLR, bez konieczności tworzenia lub zrozumienia tożsamości.  
  
 [ICLRReferenceAssemblyEnum, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 Dostarcza metody, które umożliwiają hostowi manipulowanie zestawem zestawów, do których odwołuje się plik lub strumień przy użyciu danych tożsamości zestawu, które są wewnętrzne dla środowiska CLR, bez konieczności tworzenia lub zrozumienia tych tożsamości.  
  
 [ICLRRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 Oferuje funkcje podobne do [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)z dodatkową metodą ustawiania interfejsu sterowania hosta.  
  
 [ICLRSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 Zapewnia metody dla hosta do uzyskiwania informacji o żądanych zadaniach i wykrywania zakleszczenii w jego implementacji synchronizacji.  
  
 [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 Dostarcza metody, które umożliwiają hostowi wykonywanie żądań CLR lub dostarczenie do środowiska CLR powiadomienia o skojarzonym zadaniu.  
  
 [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 Dostarcza metody, które umożliwiają hostowi jawne żądanie, aby środowisko CLR utworzyło nowe zadanie, pobrać aktualnie wykonywane zadanie i ustawić język geograficzny i kulturę dla zadania.  
  
 [ICLRValidator, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 Zapewnia metody sprawdzania poprawności przenośnych obrazów wykonywalnych (PE) i raportowania błędów walidacji.  
  
 [ICorConfiguration, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 Zapewnia metody konfigurowania środowiska CLR.  
  
 [ICorThreadpool, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 Zapewnia metody uzyskiwania dostępu do puli wątków.  
  
 [IDebuggerInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 Zapewnia metody uzyskiwania informacji o stanie usług debugowania.  
  
 [IDebuggerThreadControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 Zapewnia metody powiadamiania hosta o blokowaniu i odblokowywaniu wątków przez usługi debugowania.  
  
 [IGCHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 Zapewnia metody uzyskiwania informacji o systemie odzyskiwania pamięci i kontrolowania niektórych aspektów wyrzucania elementów bezużytecznych.  
  
 [IGCHost2, interfejs](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 Udostępnia metodę [SetGCStartupLimitsEx —](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) , która umożliwia hostowi Ustawianie rozmiaru segmentu wyrzucania elementów bezużytecznych i maksymalnego rozmiaru generacji od zera systemu odzyskiwania pamięci do wartości większej niż `DWORD`.  
  
 [IGCHostControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 Zapewnia metodę, która umożliwia modułowi wyrzucania elementów bezużytecznych żądanie zmiany limitów pamięci wirtualnej przez hosta.  
  
 [IGCThreadControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 Zapewnia metody uczestnictwa w planowaniu wątków, które w przeciwnym razie byłyby blokowane do wyrzucania elementów bezużytecznych.  
  
 [IHostAssemblyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 Dostarcza metody, które umożliwiają hostowi określenie zestawów zestawów, które powinny być ładowane przez środowisko CLR lub przez hosta.  
  
 [IHostAssemblyStore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 Dostarcza metody, które umożliwiają hostowi załadowanie zestawów i modułów niezależnie od środowiska CLR.  
  
 [IHostAutoEvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 Przedstawia reprezentację zdarzenia autoresetowania zaimplementowanego przez hosta.  
  
 [IHostControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 Zapewnia metody konfigurowania ładowania zestawów i określania interfejsów hostingu obsługiwanych przez hosta.  
  
 [IHostCrst, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 Służy jako reprezentacja hosta sekcji krytycznej dla wątków.  
  
 [IHostGCManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 Dostarcza metody, które powiadamiają hosta zdarzeń w mechanizmie wyrzucania elementów bezużytecznych zaimplementowane przez środowisko CLR.  
  
 [IHostIoCompletionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 Dostarcza metody, które umożliwiają współpracującie środowiska CLR z portami zakończenia we/wy dostarczonymi przez hosta.  
  
 [IHostMalloc, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 Dostarcza metody dla środowiska CLR do żądania szczegółowych alokacji ze sterty za pośrednictwem hosta.  
  
 [IHostManualEvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 Zapewnia implementację hosta reprezentacji zdarzenia resetowania ręcznego.  
  
 [IHostMemoryManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 Zapewnia metody środowiska CLR do przydzielenia żądań pamięci wirtualnej za pośrednictwem hosta zamiast używania standardowych funkcji pamięci wirtualnej Win32.  
  
 [IHostPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 Dostarcza metody, które powiadamiają hosta o akcjach wykonywanych przez środowisko CLR w przypadku przerwań, przekroczeń limitu czasu lub niepowodzeń.  
  
 [IHostSecurityContext, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 Włącza środowisko CLR do obsługi informacji kontekstu zabezpieczeń implementowanych przez hosta.  
  
 [IHostSecurityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 Zapewnia metody umożliwiające dostęp do i kontrolę nad kontekstem zabezpieczeń aktualnie wykonywanego wątku.  
  
 [IHostSemaphore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 Przedstawia reprezentację semafora zaimplementowanego przez hosta.  
  
 [IHostSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 Zapewnia metody dla środowiska CLR do tworzenia elementów pierwotnych synchronizacji przez wywołanie hosta zamiast korzystania z funkcji synchronizacji Win32.  
  
 [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 Zapewnia metody umożliwiające komunikację środowiska CLR z hostem w celu zarządzania zadaniami.  
  
 [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 Zapewnia metody umożliwiające współdziałanie środowiska CLR z zadaniami za pośrednictwem hosta zamiast korzystania ze standardowego wątku lub funkcji światłowodowych systemu operacyjnego.  
  
 [IHostThreadPoolManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 Zapewnia metody dla środowiska CLR w celu skonfigurowania puli wątków i umieszczania w kolejce elementów roboczych w puli wątków.  
  
 [IManagedObject, interfejs](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 Zapewnia metody kontrolowania obiektu zarządzanego.  
  
 IObjectHandle  
 Zapewnia metodę odpakowania obiektów marshal-by-Value z operatora pośredni.  
  
 [ITypeName, interfejs](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 Zapewnia metody uzyskiwania informacji o nazwie typu. (Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie).  
  
 [ITypeNameBuilder, interfejs](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 Zapewnia metody tworzenia nazwy typu. (Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie).  
  
 [ITypeNameFactory, interfejs](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 Dostarcza metody służące do dekonstrukcji nazwy typu. (Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie).  
  
 IValidator  
 Zapewnia metody sprawdzania poprawności przenośnych obrazów wykonywalnych (PE) i raportowania błędów walidacji.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przestarzałe klasy coclass i interfejsy hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Zawiera tematy opisujące Interfejsy hostingu dostępne w .NET Framework w wersji 1,0 i 1,1.  
  
 [Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 Zawiera tematy opisujące Interfejsy hostingu dostępne w .NET Framework 4.
