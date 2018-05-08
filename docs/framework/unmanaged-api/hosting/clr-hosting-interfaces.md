---
title: Interfejsy hostingu środowiska CLR
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03839a2c6e52f9d2dcdd2e0941ff4fdbeb8a3a17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="clr-hosting-interfaces"></a>Interfejsy hostingu środowiska CLR
W tej sekcji opisano interfejsów, które niezarządzanych hostów można użyć do integracji środowisko uruchomieniowe języka wspólnego (CLR) w swoich aplikacjach. Informacje odnoszą się do platformy .NET Framework w wersji 2.0 lub nowszy. Te interfejsy Włącz hosta do kontrolowania wielu aspektów więcej czasu wykonywania niż w wersji 1.0, 1.1 i podaj znacznie większego integrację środowiska CLR i model wykonania hosta.  
  
 W programie .NET Framework w wersji 1.0, 1.1 obsługi włączone niezarządzane hosta można załadować środowiska CLR do procesu, konfigurowanie niektórych ustawień i otrzymywanie powiadomień o zdarzeniach. Jednak ogólnie rzecz biorąc, hosta i środowiska CLR został uruchomiony niezależnie w tym procesie. .NET Framework w wersji 2.0 i nowszych wersji nowe warstwy abstrakcji umożliwiają hosta zapewniają wiele zasobów oferowanych przez typów w zestawie Win32 i rozszerzyć zestaw funkcji, które można skonfigurować hosta.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [IActionOnCLREvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 Udostępnia metody, która wykonuje wywołanie zwrotne zarejestrowane zdarzenia.  
  
 [IApartmentCallback, interfejs](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 Udostępnia metody do tworzenia wywołań zwrotnych w apartamencie.  
  
 [IAppDomainBinding, interfejs](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 Udostępnia metody dla konfiguracji środowiska wykonawczego.  
  
 [ICatalogServices, interfejs](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 Udostępnia metody dla skatalogowania usług. (Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).  
  
 [ICLRAssemblyIdentityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 Udostępnia metody, które obsługują komunikację między hostem i informacje o zestawach środowiska CLR.  
  
 [ICLRAssemblyReferenceList, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 Zarządza listę zestawów, które są ładowane przez środowisko CLR, a nie przez hosta.  
  
 [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 Udostępnia metody dla hosta w celu uzyskania dostępu do i skonfigurować różne aspekty środowiska CLR.  
  
 [ICLRDebugManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 Udostępnia metody umożliwiające hosta do skojarzenia z identyfikatorem i przyjazną nazwę zestawu zadań.  
  
 [ICLRErrorReportingManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 Udostępnia metody, które umożliwiają hosta skonfigurować zrzuty stosu niestandardowych dla usługi raportowania błędów.  
  
 [ICLRGCManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 Udostępnia metody umożliwiające hosta do interakcji z system CLR czyszczenia pamięci.  
  
 [ICLRHostBindingPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 Udostępnia metody dla hosta ocenić i komunikować się zmiany informacji o zasadach dla zestawów.  
  
 [ICLRHostProtectionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 Umożliwia hosta blokowanie określonych klas zarządzanych, metody, właściwości i pola w programie częściowo zaufany kod.  
  
 [ICLRIoCompletionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 Implementuje metody wywołania zwrotnego, która umożliwia hosta powiadomiono CLR stan określonego żądań We/Wy.  
  
 [ICLRMemoryNotificationCallback, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 Włącza hosta do warunków braku pamięci raportu w sposób podobny do środowiska Win32 `CreateMemoryResourceNotification` funkcji.  
  
 [ICLROnEventManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 Udostępnia metody umożliwiające hosta umożliwia rejestrowanie i wyrejestrowywanie wywołań zwrotnych dla zdarzenia środowiska CLR.  
  
 [ICLRPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 Udostępnia metody, które umożliwiają hosta określić zasady akcje do wykonania w przypadku awarii i przekroczeń limitu czasu.  
  
 [ICLRProbingAssemblyEnum, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 Udostępnia metody umożliwiające hosta można uzyskać za pomocą zestawu tożsamości informacje, które są wewnętrzne dla środowiska CLR, bez konieczności tworzenia i zrozumienie tej tożsamości sondowania tożsamości zestawu.  
  
 [ICLRReferenceAssemblyEnum, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 Udostępnia metody, które umożliwiają hosta do manipulowania zbiór zestawów odwołuje się do pliku lub strumienia za pomocą zestawu danych tożsamości, które jest wewnętrzna CLR, bez konieczności tworzenia i zrozumienie tych tożsamości.  
  
 [ICLRRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 Zapewnia funkcje podobne do [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), z dodatkową metodę można ustawić interfejsu kontroli hosta.  
  
 [ICLRSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 Udostępnia metody dla hosta, aby uzyskać informacje dotyczące zadań i wykrył zakleszczenie w jej wykonanie synchronizacji.  
  
 [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 Udostępnia metody umożliwiające hosta do wysyłania żądań CLR lub w celu udostępnienia powiadomień do środowiska CLR o skojarzonego zadania.  
  
 [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 Udostępnia metody umożliwiające hosta do żądania jawnie, czy CLR utworzyć nowe zadanie, Pobierz aktualnie wykonywanego zadania i ustaw geograficzne języka i kultury dla zadania.  
  
 [ICLRValidator, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 Udostępnia metody dla sprawdzanie poprawności przenośne obrazy wykonywalne (PE) i raportowanie błędów sprawdzania poprawności.  
  
 [ICorConfiguration, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 Udostępnia metody do konfigurowania środowiska CLR.  
  
 [ICorThreadpool, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 Udostępnia metody, aby uzyskać dostęp do puli wątków.  
  
 [IDebuggerInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 Udostępnia metody uzyskiwania informacji na temat stanu usług debugowania.  
  
 [IDebuggerThreadControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 Udostępnia metody dla powiadamiania hosta o blokowania i odblokowywania wątków przez usług debugowania.  
  
 [IGCHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 Udostępnia metody uzyskiwania informacji na temat systemu czyszczenia pamięci oraz kontrolowanie niektórych aspektów wyrzucanie elementów bezużytecznych.  
  
 [IGCHost2, interfejs](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 Udostępnia [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metodę, która umożliwia hosta ustawioną rozmiar segmentu kolekcji pamięci i maksymalny rozmiar generowania systemu czyszczenia pamięci zerowej wartości większej niż `DWORD`.  
  
 [IGCHostControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 Udostępnia metody, która włącza moduł garbage collector na żądanie hosta, aby zmienić limit pamięci wirtualnej.  
  
 [IGCThreadControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 Udostępnia metody do uczestnictwa w planowaniu wątków, które można zablokować dla wyrzucanie elementów bezużytecznych.  
  
 [IHostAssemblyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 Udostępnia metody, które umożliwiają hosta określić zestawy zestawy, które powinny być załadowane przez środowisko CLR lub przez hosta.  
  
 [IHostAssemblyStore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 Udostępnia metody umożliwiające hosta można załadować zestawów i modułów, niezależnie od środowiska CLR.  
  
 [IHostAutoEvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 Udostępnia reprezentację automatyczne resetowanie zdarzenia implementowanego przez zdarzenie hosta.  
  
 [IHostControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 Udostępnia metody konfigurowania ładowania zestawów i określania, które hosting interfejsy obsługuje hosta.  
  
 [IHostCrst, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 Służy jako hosta reprezentację sekcja krytyczna dla wątków.  
  
 [IHostGCManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 Udostępnia metody, które powiadamiają o hoście zdarzenia mechanizmu kolekcji garbage zaimplementowana przez środowisko CLR.  
  
 [IHostIoCompletionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 Udostępnia metody umożliwiające CLR wchodzić w interakcje z portów We/Wy dostarczone przez hosta.  
  
 [IHostMalloc, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 Udostępnia metody dla środowiska CLR do żądania szczegółowych alokacji sterty za pośrednictwem hosta.  
  
 [IHostManualEvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 Udostępnia implementację hosta reprezentację zdarzeń resetowania ręcznego.  
  
 [IHostMemoryManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 Udostępnia metody dla środowiska CLR na wysyłanie żądań pamięci wirtualnej za pośrednictwem hosta, a nie przy użyciu standardowych funkcji Win32 w pamięci wirtualnej.  
  
 [IHostPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 Udostępnia metody, które powiadamiają o hoście akcje, które wykonuje CLR w przypadku liczby przerywa przekroczenia limitu czasu lub błędów.  
  
 [IHostSecurityContext, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 Umożliwia CLR zachować informacje kontekstu zabezpieczeń zaimplementowana przez hosta.  
  
 [IHostSecurityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 Udostępnia metody umożliwiające dostęp do i kontrolę nad wątku aktualnie wykonywane w kontekście zabezpieczeń.  
  
 [IHostSemaphore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 Udostępnia reprezentację semafora zaimplementowana przez hosta.  
  
 [IHostSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 Udostępnia metody dla CLR można utworzyć w nim elementów podstawowych synchronizacji przez wywołanie przez hosta, zamiast używać funkcji synchronizacji Win32.  
  
 [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 Udostępnia metody umożliwiające CLR do komunikowania się z hosta do zarządzania zadaniami.  
  
 [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 Udostępnia metody umożliwiające CLR do pracy z zadaniami za pośrednictwem hosta zamiast przy użyciu funkcji wątki lub włókna standardowy system operacyjny.  
  
 [IHostThreadPoolManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 Udostępnia metody dla środowiska CLR do skonfigurowania puli wątków i do kolejki elementów roboczych w puli wątków.  
  
 [IManagedObject, interfejs](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 Udostępnia metody umożliwiające sterowanie zarządzanego obiektu.  
  
 "IObjectHandle"  
 Zapewnia metodę otwierania obiektów kierowanie przez wartości z pośrednie.  
  
 [ITypeName, interfejs](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 Udostępnia metody uzyskiwania informacji na nazwę typu. (Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).  
  
 [ITypeNameBuilder, interfejs](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 Udostępnia metody do tworzenia nazwy typu. (Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).  
  
 [ITypeNameFactory, interfejs](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 Udostępnia metody dla deconstructing nazwę typu. (Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).  
  
 "IValidator"  
 Udostępnia metody dla sprawdzanie poprawności przenośne obrazy wykonywalne (PE) i raportowanie błędów sprawdzania poprawności.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przestarzałe klasy coclass i interfejsy hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Zawiera tematy, które opisują interfejsy hostingu dostępne w programie .NET Framework w wersji 1.0, 1.1.  
  
 [Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 Zawiera tematy, które opisują interfejsy hostingu w [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)].
