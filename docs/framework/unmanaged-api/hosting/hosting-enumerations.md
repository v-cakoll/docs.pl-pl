---
title: Hosting — Wyliczenia
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged enumerations [.NET Framework], hosting
- enumerations [.NET Framework hosting]
- hosting enumerations [.NET Framework]
ms.assetid: e09131eb-1f7d-4f52-ae42-7393e9b62ef6
ms.openlocfilehash: 8edace3191ee4477b19f199d5db6c891c993dcd5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504306"
---
# <a name="hosting-enumerations"></a>Hosting — Wyliczenia
W tej sekcji opisano niezarządzane wyliczenia używane przez interfejs API hostingu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [CLSID_RESOLUTION_FLAGS, wyliczenie](clsid-resolution-flags-enumeration.md)  
 Zawiera wartości wskazujące sposób, w jaki środowisko uruchomieniowe języka wspólnego (CLR) powinno rozwiązać problem `CLSID` .  
  
 [COR_GC_STAT_TYPES, wyliczenie](cor-gc-stat-types-enumeration.md)  
 Określa statystyki, które mają być rejestrowane w celu wyrzucania elementów bezużytecznych.  
  
 [COR_GC_THREAD_STATS_TYPES, wyliczenie](cor-gc-thread-stats-types-enumeration.md)  
 Wskazuje statystykę wyrzucania elementów bezużytecznych wątku.  
  
 [EApiCategories, wyliczenie](eapicategories-enumeration.md)  
 Opisuje kategorie możliwości, które host może blokować z uruchamiania w częściowo zaufanym kodzie.  
  
 [EBindPolicyLevels, wyliczenie](ebindpolicylevels-enumeration.md)  
 Zawiera flagi określające poziom, na którym należy zastosować lub zmodyfikować zasady zestawu.  
  
 [ECLRAssemblyIdentityFlags, wyliczenie](eclrassemblyidentityflags-enumeration.md)  
 Wskazuje typ tożsamości zestawu.  
  
 [EClrEvent, wyliczenie](eclrevent-enumeration.md)  
 Opisuje zdarzenia środowiska CLR, dla których host może rejestrować wywołania zwrotne.  
  
 [EClrFailure — Wyliczenie](eclrfailure-enumeration.md)  
 Opisuje zestaw błędów, dla których host może ustawiać akcje zasad.  
  
 [EClrOperation — Wyliczenie](eclroperation-enumeration.md)  
 Opisuje zestaw operacji, dla których host może stosować akcje zasad.  
  
 [EClrUnhandledException — Wyliczenie](eclrunhandledexception-enumeration.md)  
 Opisuje dostępne opcje zarządzania wyjątkami, które nie są obsługiwane w kodzie użytkownika.  
  
 [EContextType, wyliczenie](econtexttype-enumeration.md)  
 Opisuje kontekst zabezpieczeń aktualnie wykonywanego wątku.  
  
 [ECustomDumpFlavor — Wyliczenie](ecustomdumpflavor-enumeration.md)  
 Zawiera wartości wskazujące, które elementy mają być uwzględnione w niestandardowym podzestawie zrzutu sterty podczas raportowania błędów.  
  
 [ECustomDumpItemKind, wyliczenie](ecustomdumpitemkind-enumeration.md)  
 Zarezerwowane dla przyszłego rozszerzenia struktury [struktury CustomDumpItem —](customdumpitem-structure.md) .  
  
 [EHostApplicationPolicy — Wyliczenie](ehostapplicationpolicy-enumeration.md)  
 Wskazuje, jak zmodyfikować obiekt interfejsu [interfejsu IHostAssemblyManager](ihostassemblymanager-interface.md) . To wyliczenie jest przestarzałe.  
  
 [EHostBindingPolicyModifyFlags — Wyliczenie](ehostbindingpolicymodifyflags-enumeration.md)  
 Umożliwia hostowi określenie typu przekierowania, który ma być wykonywany przez środowisko CLR podczas stosowania modyfikacji zasad z zestawu źródłowego do zestawu docelowego.  
  
 [EInitializeNewDomainFlags, wyliczenie](einitializenewdomainflags-enumeration.md)  
 Umożliwia hostowi zapewnienie środowiska uruchomieniowego z informacjami o inicjalizacji domeny aplikacji.  
  
 [EMemoryAvailable, wyliczenie](ememoryavailable-enumeration.md)  
 Zawiera wartości wskazujące ilość wolnej pamięci fizycznej na komputerze.  
  
 [EMemoryCriticalLevel, wyliczenie](ememorycriticallevel-enumeration.md)  
 Zawiera wartości wskazujące wpływ błędu w przypadku żądania określonego przydziału pamięci, ale nie można go spełnić.  
  
 [EPolicyAction — Wyliczenie](epolicyaction-enumeration.md)  
 Opisuje akcje zasad, które host może ustawić dla operacji opisanych przez [Wyliczenie EClrOperation —](eclroperation-enumeration.md) i błędy opisane przez [Wyliczenie EClrFailure —](eclrfailure-enumeration.md).  
  
 [ESymbolReadingPolicy, wyliczenie](esymbolreadingpolicy-enumeration.md)  
 Zawiera wartości, które ustawiają zasady odczytujące pliki bazy danych (PDB) programu.  
  
 [ETaskType, wyliczenie](etasktype-enumeration.md)  
 Zawiera wartości wskazujące rodzaj zadania reprezentowanego przez [interfejs ICLRTask](iclrtask-interface.md) lub interfejs [interfejsu IHostTask](ihosttask-interface.md) .  
  
 [HOST_TYPE, wyliczenie](host-type-enumeration.md)  
 Zawiera wartości określające typ hosta, który uruchamia aplikację.  
  
 [MALLOC_TYPE — Wyliczenie](malloc-type-enumeration.md)  
 Zawiera wartości określające charakterystyki przydzielenia pamięci.  
  
 [METAHOST_CONFIG_FLAGS, wyliczenie](metahost-config-flags-enumeration.md)  
 Opisuje możliwe flagi zwrócone w `pdwConfigFlags` parametrze metody [ICLRMetaHostPolicy:: GetRequestedRuntime —](iclrmetahostpolicy-getrequestedruntime-method.md) .  
  
 [METAHOST_POLICY_FLAGS, wyliczenie](metahost-policy-flags-enumeration.md)  
 Program udostępnia zasady powiązań, które są wspólne dla większości hostów środowiska uruchomieniowego.  
  
 [RUNTIME_INFO_FLAGS — Wyliczenie](runtime-info-flags-enumeration.md)  
 Zawiera wartości wskazujące, jakie informacje o środowisku CLR należy zwrócić.  
  
 [StackOverflowType, wyliczenie](stackoverflowtype-enumeration.md)  
 Zawiera wartości wskazujące podstawową przyczynę zdarzenia przepełnienia stosu.  
  
 [STARTUP_FLAGS, wyliczenie](startup-flags-enumeration.md)  
 Zawiera wartości, które wskazują zachowanie uruchamiania środowiska CLR.  
  
 [ValidatorFlags, wyliczenie](validatorflags-enumeration.md)  
 Zawiera wartości wskazujące typ walidacji, który powinien zostać wykonany w wywołaniu [metody walidacji](iclrvalidator-validate-method.md).  
  
 [WAIT_OPTION — Wyliczenie](wait-option-enumeration.md)  
 Wskazuje akcję, którą host powinien wykonać, jeśli operacja zażądała bloków CLR.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Współklasy hostingu](hosting-coclasses.md)  
  
 [Hosting, interfejsy](hosting-interfaces.md)  
  
 [Przestarzałe funkcje hostingu środowiska CLR](deprecated-clr-hosting-functions.md)  
  
 [Hosting, struktury](hosting-structures.md)
