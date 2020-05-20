---
title: Interfejsy hostingu środowiska CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
ms.openlocfilehash: e6913e18a4ff6e616f357a4ef43fb8b892264943
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616843"
---
# <a name="clr-hosting-interfaces"></a>Interfejsy hostingu środowiska CLR
W tej sekcji opisano interfejsy, które mogą być używane przez niezarządzane hosty do integrowania środowiska uruchomieniowego języka wspólnego (CLR) z aplikacjami. Informacje dotyczą .NET Framework w wersji 2,0 i nowszych. Te interfejsy umożliwiają hostowi kontrolowanie wielu innych aspektów środowiska uruchomieniowego niż było możliwe w wersjach 1,0 i 1,1 i zapewniają znacznie ściślejszą integrację między środowiskiem CLR a modelem wykonywania hosta.  
  
 W .NET Framework w wersji 1,0 i 1,1 model hostingu włączył niezarządzany host do załadowania środowiska CLR do procesu, skonfigurowania pewnych ustawień i otrzymywania powiadomień o zdarzeniach. Ogólnie rzecz biorąc, Host i środowisko CLR działały niezależnie w tym procesie. W .NET Framework w wersji 2,0 i nowszych nowe warstwy abstrakcji umożliwiają hostowi udostępnianie wielu zasobów, które są obecnie udostępniane przez typy w zestawie Win32, i poszerzają zestaw funkcji, które mogą być konfigurowane przez hosta.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [IActionOnCLREvent — Interfejs](iactiononclrevent-interface.md)  
 Zapewnia metodę, która wykonuje wywołanie zwrotne dla zarejestrowanego zdarzenia.  
  
 [IApartmentCallback, interfejs](iapartmentcallback-interface.md)  
 Zapewnia metody tworzenia wywołań zwrotnych w obrębie apartamentu.  
  
 [IAppDomainBinding — Interfejs](iappdomainbinding-interface.md)  
 Zapewnia metody ustawiania konfiguracji czasu wykonywania.  
  
 [ICatalogServices, interfejs](icatalogservices-interface.md)  
 Dostarcza metody dla usług katalogowych. (Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie).  
  
 [ICLRAssemblyIdentityManager, interfejs](iclrassemblyidentitymanager-interface.md)  
 Dostarcza metody, które obsługują komunikację między hostem i środowiskiem CLR o zestawach.  
  
 [ICLRAssemblyReferenceList — Interfejs](iclrassemblyreferencelist-interface.md)  
 Zarządza listą zestawów, które są ładowane przez środowisko CLR, a nie przez hosta.  
  
 [ICLRControl — Interfejs](iclrcontrol-interface.md)  
 Zapewnia metody do uzyskiwania dostępu do hosta i konfigurowania różnych aspektów środowiska CLR.  
  
 [ICLRDebugManager, interfejs](iclrdebugmanager-interface.md)  
 Dostarcza metody, które umożliwiają hostowi kojarzenie zestawu zadań z identyfikatorem i przyjazną nazwą.  
  
 [ICLRErrorReportingManager, interfejs](iclrerrorreportingmanager-interface.md)  
 Dostarcza metody, które umożliwiają hostowi skonfigurowanie niestandardowych zrzutów sterty na potrzeby raportowania błędów.  
  
 [ICLRGCManager, interfejs](iclrgcmanager-interface.md)  
 Dostarcza metody, które umożliwiają hostowi współdziałanie z systemem odzyskiwania pamięci CLR.  
  
 [ICLRHostBindingPolicyManager, interfejs](iclrhostbindingpolicymanager-interface.md)  
 Zapewnia metody dla hosta do szacowania i przekazywania zmian w informacjach o zasadach dla zestawów.  
  
 [ICLRHostProtectionManager, interfejs](iclrhostprotectionmanager-interface.md)  
 Umożliwia hostowi blokowanie określonych zarządzanych klas, metod, właściwości i pól z uruchamiania w częściowo zaufanym kodzie.  
  
 [ICLRIoCompletionManager, interfejs](iclriocompletionmanager-interface.md)  
 Implementuje metodę wywołania zwrotnego, która umożliwia hostowi powiadomienie środowiska CLR o stanie określonych żądań we/wy.  
  
 [ICLRMemoryNotificationCallback — Interfejs](iclrmemorynotificationcallback-interface.md)  
 Umożliwia hostowi zgłaszanie warunków ciśnienia pamięci przy użyciu podejścia podobnego do `CreateMemoryResourceNotification` funkcji Win32.  
  
 [ICLROnEventManager, interfejs](iclroneventmanager-interface.md)  
 Dostarcza metody, które umożliwiają hostowi rejestrowanie i Wyrejestrowywanie wywołań zwrotnych dla zdarzeń CLR.  
  
 [ICLRPolicyManager, interfejs](iclrpolicymanager-interface.md)  
 Dostarcza metody, które umożliwiają hostowi określenie akcji zasad, które mają być podejmowane w przypadku awarii i przekroczeń limitu czasu.  
  
 [ICLRProbingAssemblyEnum, interfejs](iclrprobingassemblyenum-interface.md)  
 Dostarcza metody, które umożliwiają hostowi pobieranie tożsamości dla zestawu przy użyciu informacji o tożsamości zestawu, które są wewnętrzne dla środowiska CLR, bez konieczności tworzenia lub zrozumienia tożsamości.  
  
 [ICLRReferenceAssemblyEnum, interfejs](iclrreferenceassemblyenum-interface.md)  
 Dostarcza metody, które umożliwiają hostowi manipulowanie zestawem zestawów, do których odwołuje się plik lub strumień przy użyciu danych tożsamości zestawu, które są wewnętrzne dla środowiska CLR, bez konieczności tworzenia lub zrozumienia tych tożsamości.  
  
 [ICLRRuntimeHost, interfejs](iclrruntimehost-interface.md)  
 Oferuje funkcje podobne do [ICorRuntimeHost](icorruntimehost-interface.md)z dodatkową metodą ustawiania interfejsu sterowania hosta.  
  
 [ICLRSyncManager — Interfejs](iclrsyncmanager-interface.md)  
 Zapewnia metody dla hosta do uzyskiwania informacji o żądanych zadaniach i wykrywania zakleszczenii w jego implementacji synchronizacji.  
  
 [ICLRTask — Interfejs](iclrtask-interface.md)  
 Dostarcza metody, które umożliwiają hostowi wykonywanie żądań CLR lub dostarczenie do środowiska CLR powiadomienia o skojarzonym zadaniu.  
  
 [ICLRTaskManager, interfejs](iclrtaskmanager-interface.md)  
 Dostarcza metody, które umożliwiają hostowi jawne żądanie, aby środowisko CLR utworzyło nowe zadanie, pobrać aktualnie wykonywane zadanie i ustawić język geograficzny i kulturę dla zadania.  
  
 [ICLRValidator, interfejs](iclrvalidator-interface.md)  
 Zapewnia metody sprawdzania poprawności przenośnych obrazów wykonywalnych (PE) i raportowania błędów walidacji.  
  
 [ICorConfiguration, interfejs](icorconfiguration-interface.md)  
 Zapewnia metody konfigurowania środowiska CLR.  
  
 [ICorThreadpool, interfejs](icorthreadpool-interface.md)  
 Zapewnia metody uzyskiwania dostępu do puli wątków.  
  
 [IDebuggerInfo, interfejs](idebuggerinfo-interface.md)  
 Zapewnia metody uzyskiwania informacji o stanie usług debugowania.  
  
 [IDebuggerThreadControl, interfejs](idebuggerthreadcontrol-interface.md)  
 Zapewnia metody powiadamiania hosta o blokowaniu i odblokowywaniu wątków przez usługi debugowania.  
  
 [IGCHost, interfejs](igchost-interface.md)  
 Zapewnia metody uzyskiwania informacji o systemie odzyskiwania pamięci i kontrolowania niektórych aspektów wyrzucania elementów bezużytecznych.  
  
 [IGCHost2, interfejs](igchost2-interface.md)  
 Udostępnia metodę [SetGCStartupLimitsEx —](igchost2-setgcstartuplimitsex-method.md) , która umożliwia hostowi Ustawianie rozmiaru segmentu wyrzucania elementów bezużytecznych i maksymalnego rozmiaru generacji wynoszącego system wyrzucania elementów bezużytecznych do wartości większej niż `DWORD` .  
  
 [IGCHostControl — Interfejs](igchostcontrol-interface.md)  
 Zapewnia metodę, która umożliwia modułowi wyrzucania elementów bezużytecznych żądanie zmiany limitów pamięci wirtualnej przez hosta.  
  
 [IGCThreadControl, interfejs](igcthreadcontrol-interface.md)  
 Zapewnia metody uczestnictwa w planowaniu wątków, które w przeciwnym razie byłyby blokowane do wyrzucania elementów bezużytecznych.  
  
 [IHostAssemblyManager, interfejs](ihostassemblymanager-interface.md)  
 Dostarcza metody, które umożliwiają hostowi określenie zestawów zestawów, które powinny być ładowane przez środowisko CLR lub przez hosta.  
  
 [IHostAssemblyStore, interfejs](ihostassemblystore-interface.md)  
 Dostarcza metody, które umożliwiają hostowi załadowanie zestawów i modułów niezależnie od środowiska CLR.  
  
 [IHostAutoEvent — Interfejs](ihostautoevent-interface.md)  
 Przedstawia reprezentację zdarzenia autoresetowania zaimplementowanego przez hosta.  
  
 [IHostControl, interfejs](ihostcontrol-interface.md)  
 Zapewnia metody konfigurowania ładowania zestawów i określania interfejsów hostingu obsługiwanych przez hosta.  
  
 [IHostCrst, interfejs](ihostcrst-interface.md)  
 Służy jako reprezentacja hosta sekcji krytycznej dla wątków.  
  
 [IHostGCManager — Interfejs](ihostgcmanager-interface.md)  
 Dostarcza metody, które powiadamiają hosta zdarzeń w mechanizmie wyrzucania elementów bezużytecznych zaimplementowane przez środowisko CLR.  
  
 [IHostIoCompletionManager, interfejs](ihostiocompletionmanager-interface.md)  
 Dostarcza metody, które umożliwiają współpracującie środowiska CLR z portami zakończenia we/wy dostarczonymi przez hosta.  
  
 [IHostMalloc, interfejs](ihostmalloc-interface.md)  
 Dostarcza metody dla środowiska CLR do żądania szczegółowych alokacji ze sterty za pośrednictwem hosta.  
  
 [IHostManualEvent, interfejs](ihostmanualevent-interface.md)  
 Zapewnia implementację hosta reprezentacji zdarzenia resetowania ręcznego.  
  
 [IHostMemoryManager, interfejs](ihostmemorymanager-interface.md)  
 Zapewnia metody środowiska CLR do przydzielenia żądań pamięci wirtualnej za pośrednictwem hosta zamiast używania standardowych funkcji pamięci wirtualnej Win32.  
  
 [IHostPolicyManager, interfejs](ihostpolicymanager-interface.md)  
 Dostarcza metody, które powiadamiają hosta o akcjach wykonywanych przez środowisko CLR w przypadku przerwań, przekroczeń limitu czasu lub niepowodzeń.  
  
 [IHostSecurityContext — Interfejs](ihostsecuritycontext-interface.md)  
 Włącza środowisko CLR do obsługi informacji kontekstu zabezpieczeń implementowanych przez hosta.  
  
 [IHostSecurityManager, interfejs](ihostsecuritymanager-interface.md)  
 Zapewnia metody umożliwiające dostęp do i kontrolę nad kontekstem zabezpieczeń aktualnie wykonywanego wątku.  
  
 [IHostSemaphore, interfejs](ihostsemaphore-interface.md)  
 Przedstawia reprezentację semafora zaimplementowanego przez hosta.  
  
 [IHostSyncManager, interfejs](ihostsyncmanager-interface.md)  
 Zapewnia metody dla środowiska CLR do tworzenia elementów pierwotnych synchronizacji przez wywołanie hosta zamiast korzystania z funkcji synchronizacji Win32.  
  
 [IHostTask, interfejs](ihosttask-interface.md)  
 Zapewnia metody umożliwiające komunikację środowiska CLR z hostem w celu zarządzania zadaniami.  
  
 [IHostTaskManager, interfejs](ihosttaskmanager-interface.md)  
 Zapewnia metody umożliwiające współdziałanie środowiska CLR z zadaniami za pośrednictwem hosta zamiast korzystania ze standardowego wątku lub funkcji światłowodowych systemu operacyjnego.  
  
 [IHostThreadPoolManager, interfejs](ihostthreadpoolmanager-interface.md)  
 Zapewnia metody dla środowiska CLR w celu skonfigurowania puli wątków i umieszczania w kolejce elementów roboczych w puli wątków.  
  
 [IManagedObject, interfejs](imanagedobject-interface.md)  
 Zapewnia metody kontrolowania obiektu zarządzanego.  
  
 IObjectHandle  
 Zapewnia metodę odpakowania obiektów marshal-by-Value z operatora pośredni.  
  
 [ITypeName, interfejs](itypename-interface.md)  
 Zapewnia metody uzyskiwania informacji o nazwie typu. (Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie).  
  
 [ITypeNameBuilder — Interfejs](itypenamebuilder-interface.md)  
 Zapewnia metody tworzenia nazwy typu. (Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie).  
  
 [ITypeNameFactory, interfejs](itypenamefactory-interface.md)  
 Dostarcza metody służące do dekonstrukcji nazwy typu. (Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczony do użycia bezpośrednio w kodzie).  
  
 IValidator  
 Zapewnia metody sprawdzania poprawności przenośnych obrazów wykonywalnych (PE) i raportowania błędów walidacji.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przestarzałe klasy coclass i interfejsy hostingu środowiska CLR](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Zawiera tematy opisujące Interfejsy hostingu dostępne w .NET Framework w wersji 1,0 i 1,1.  
  
 [Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5](clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 Zawiera tematy opisujące Interfejsy hostingu dostępne w .NET Framework 4.
