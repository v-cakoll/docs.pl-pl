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
ms.openlocfilehash: 80404e65263aa4ad245a8c8213630a4736bd7b11
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456873"
---
# <a name="clr-hosting-interfaces"></a>Interfejsy hostingu środowiska CLR
W tej sekcji opisano interfejsy, które niezarządzane hosty służy do integrowania środowisko uruchomieniowe języka wspólnego (CLR) w swoich aplikacjach. Informacje odnoszą się do wersji programu .NET Framework 2.0 i nowszych wersjach. Te interfejsy Włącz hosta kontrolują wiele aspektów więcej obsługi niż w wersji 1.0 i 1.1 i zapewnia znacznie ściślejszą integrację środowiska CLR i modelu wykonywania hosta.  
  
 W .NET Framework w wersji 1.0 i 1.1 modelu hostingu włączono niezarządzany host do ładowania CLR do procesu, aby skonfigurować niektóre ustawienia i otrzymywać powiadomienia o zdarzeniach. Jednak ogólnie rzecz biorąc, hosta i CLR został uruchomiony niezależnie w tym procesie. W .NET Framework w wersji 2.0 i nowszych wersjach nowe warstwy abstrakcji umożliwiają hosta zapewniają wiele zasobów oferowanych przez typy w zestawie Win32 i rozszerzaj zestaw funkcji, które można skonfigurować hosta.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [IActionOnCLREvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 Dostarcza metodę, która wykonuje wywołanie zwrotne zarejestrowane zdarzenia.  
  
 [IApartmentCallback, interfejs](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 Udostępnia metody do tworzenia wywołań zwrotnych w ramach typu apartment.  
  
 [IAppDomainBinding, interfejs](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 Udostępnia metody dla konfiguracji czasu wykonywania.  
  
 [ICatalogServices, interfejs](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 Udostępnia metody do katalogowania usług. (Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).  
  
 [ICLRAssemblyIdentityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 Udostępnia metody, które obsługują komunikację między hostem a środowisko CLR, informacje o zestawach.  
  
 [ICLRAssemblyReferenceList, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 Zarządza listę zestawów, które są ładowane przez środowisko CLR, a nie przez hosta.  
  
 [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 Udostępnia metody dla hosta w celu uzyskania dostępu do i skonfigurować różne aspekty środowiska CLR.  
  
 [ICLRDebugManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 Udostępnia metody umożliwiające hosta skojarzyć zestaw zadań z identyfikatorem i przyjazną nazwę.  
  
 [ICLRErrorReportingManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 Udostępnia metody umożliwiające hosta do skonfigurowania zrzutów stosu niestandardowych dla usługi raportowania błędów.  
  
 [ICLRGCManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 Udostępnia metody umożliwiające hosta do interakcji z systemem zbierania odśmiecania pamięci CLR.  
  
 [ICLRHostBindingPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 Udostępnia metody dla hosta ocenić i komunikują się zmian w informacje o zasadach dla zestawów.  
  
 [ICLRHostProtectionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 Umożliwia hosta zablokować określonych zarządzanych klas, metod, właściwości i pola z uruchomionych w kodzie częściowo zaufanym.  
  
 [ICLRIoCompletionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 Implementuje metodę wywołania zwrotnego, umożliwiająca hosta powiadomić CLR stan określonego żądania We/Wy.  
  
 [ICLRMemoryNotificationCallback, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 Włącza hosta do warunków wykorzystanie pamięci raportu przy użyciu podejścia, podobnie jak w przypadku Win32 `CreateMemoryResourceNotification` funkcji.  
  
 [ICLROnEventManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 Udostępnia metody umożliwiające hosta rejestrować i wyrejestrowywać wywołania zwrotne dla zdarzenia CLR.  
  
 [ICLRPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 Udostępnia metody umożliwiające hosta określić zasady działań podejmowanych w przypadku awarii lub przekroczenia limitu czasu.  
  
 [ICLRProbingAssemblyEnum, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 Udostępnia metody umożliwiające hosta można pobrać badania tożsamości zestawu przy użyciu zestawu tożsamości informacji wewnętrznych do środowiska CLR, bez konieczności tworzenia lub zrozumieć tej tożsamości.  
  
 [ICLRReferenceAssemblyEnum, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 Udostępnia metody umożliwiające hosta do manipulowania zbiór zestawów, które odwołuje się do pliku lub strumienia przy użyciu danych tożsamości zestawu, które jest wewnętrznym CLR, bez konieczności tworzenia lub zrozumienie tych tożsamości.  
  
 [ICLRRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 Oferuje funkcje podobne do [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md), przy użyciu dodatkowej metody do ustawiania interfejs kontrolki hosta.  
  
 [ICLRSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 Udostępnia metody dla hosta, aby uzyskać informacje o żądanych zadań i wykrył zakleszczenie w jego implementacja synchronizacji.  
  
 [ICLRTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 Udostępnia metody umożliwiające hosta propozycji dotyczących środowiska CLR lub w celu udostępnienia powiadomienia do CLR o skojarzone zadanie.  
  
 [ICLRTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 Udostępnia metody umożliwiające hosta zażądać jawnie, środowisko CLR Utwórz nowe zadanie, Pobierz aktualnie wykonywane zadanie i ustawić geograficzne języka i kultury dla zadania.  
  
 [ICLRValidator, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 Udostępnia metody sprawdzania poprawności przenośnego pliku wykonywalnego obrazów (PE) i raportowanie błędów sprawdzania poprawności.  
  
 [ICorConfiguration, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 Udostępnia metody do konfigurowania środowiska CLR.  
  
 [ICorThreadpool, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 Udostępnia metody do uzyskiwania dostępu do puli wątków.  
  
 [IDebuggerInfo, interfejs](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 Udostępnia metody uzyskiwania informacji na temat stanu usług debugowania.  
  
 [IDebuggerThreadControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 Zawiera metody służące do powiadamiania hosta dotyczące blokowania i odblokowywania wątków przez usług debugowania.  
  
 [IGCHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 Udostępnia metody uzyskiwania informacji na temat systemu czyszczenia pamięci oraz kontrolowanie niektóre aspekty wyrzucania elementów bezużytecznych.  
  
 [IGCHost2, interfejs](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 Udostępnia [setgcstartuplimitsex —](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metodę, która umożliwia hosta można skonfigurować rozmiaru segmentu kolekcji wyrzucania elementów i maksymalny rozmiar systemu czyszczenia pamięci generacji zero na wartości większej niż `DWORD`.  
  
 [IGCHostControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 Dostarcza metodę, która włącza moduł odśmiecania pamięci zażądać hosta, aby zmienić limity pamięci wirtualnej.  
  
 [IGCThreadControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 Udostępnia metody do uczestnictwa w planowaniu wątki, które w przeciwnym razie zostałby zablokowany do wyrzucania elementów bezużytecznych.  
  
 [IHostAssemblyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 Udostępnia metody umożliwiające hosta określić zestawy zestawy, które powinny być załadowane przez środowisko CLR lub przez hosta.  
  
 [IHostAssemblyStore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 Udostępnia metody umożliwiające hosta można załadować zestawów i modułów, niezależnie od środowiska CLR.  
  
 [IHostAutoEvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 Udostępnia reprezentację zdarzenie z resetowaniem automatycznym implementowany przez hosta.  
  
 [IHostControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 Udostępnia metody do konfigurowania ładowania zestawów i podczas określania, które hostingu interfejsów obsługuje hosta.  
  
 [IHostCrst, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 Służy jako hosta reprezentacja sekcję krytyczną dla wątków.  
  
 [IHostGCManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 Udostępnia metody, które powiadamiają o hoście zdarzenia w mechanizmie kolekcji wyrzucania elementów, które są implementowane przez środowisko CLR.  
  
 [IHostIoCompletionManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 Udostępnia metody, które włączyć integrację środowiska CLR do interakcji z portów We/Wy udostępniane przez hosta.  
  
 [IHostMalloc, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 Udostępnia metody dla środowiska CLR zażądać szczegółowych alokacji ze stosu za pośrednictwem hosta.  
  
 [IHostManualEvent, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 Udostępnia implementację hosta reprezentacji zdarzenie resetowania ręcznego.  
  
 [IHostMemoryManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 Udostępnia metody dla środowiska CLR wysyłać żądania pamięci wirtualnej za pośrednictwem hosta, a nie przy użyciu standardowych funkcji Win32 w pamięci wirtualnej.  
  
 [IHostPolicyManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 Udostępnia metody, które powiadamiają o hoście akcje, które środowisko CLR wykonuje się w przypadku programu przerywa przekroczenia limitu czasu lub niepowodzenia.  
  
 [IHostSecurityContext, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 Włącza środowisko CLR zachować informacje kontekstu zabezpieczeń implementowany przez hosta.  
  
 [IHostSecurityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 Udostępnia metody, które umożliwiają dostęp do i kontrolę nad kontekstu zabezpieczeń aktualnie wykonywany wątek.  
  
 [IHostSemaphore, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 Udostępnia reprezentację semafor implementowany przez hosta.  
  
 [IHostSyncManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 Udostępnia metody dla środowiska CLR do tworzenia podstawowych synchronizacji przez wywołanie przez hosta, zamiast korzystać z funkcji synchronizacji systemu Win32.  
  
 [IHostTask, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 Udostępnia metody, które włączyć integrację środowiska CLR do komunikowania się z hosta do zarządzania zadaniami.  
  
 [IHostTaskManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 Udostępnia metody, które włączyć integrację środowiska CLR do pracy z zadaniami za pośrednictwem hosta, zamiast korzystać z funkcji wątki lub włókna standardowy system operacyjny.  
  
 [IHostThreadPoolManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 Udostępnia metody dla środowiska CLR, aby skonfigurować puli wątków i kolejki elementów roboczych w puli wątków.  
  
 [IManagedObject, interfejs](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 Zawiera metody służące do sterowania zarządzanego obiektu.  
  
 Iobjecthandle "—"  
 Zapewnia metodę Odkodowywanie obiektów marshal przez wartość pośredni.  
  
 [ITypeName, interfejs](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 Udostępnia metody uzyskiwania informacji o nazwie typu. (Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).  
  
 [ITypeNameBuilder, interfejs](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 Udostępnia metody do tworzenia nazwy typu. (Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).  
  
 [ITypeNameFactory, interfejs](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 Udostępnia metody dla dekonstrukcja nazwę typu. (Ten interfejs obsługuje infrastrukturę .NET Framework i nie jest przeznaczona do użycia bezpośrednio w kodzie).  
  
 Ivalidator "—"  
 Udostępnia metody sprawdzania poprawności przenośnego pliku wykonywalnego obrazów (PE) i raportowanie błędów sprawdzania poprawności.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Przestarzałe klasy coclass i interfejsy hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 Zawiera tematy, które opisują hostingu dostarczanych w .NET Framework w wersji 1.0 i 1.1.  
  
 [Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 Zawiera tematy, które opisują hostingu dostarczanych w programie .NET Framework 4.
