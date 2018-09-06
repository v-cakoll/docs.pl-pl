---
title: Wyjątki w zarządzanych wątkach
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63931f4498f4c1f313e7980b91ef712d4a46a837
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43865182"
---
# <a name="exceptions-in-managed-threads"></a>Wyjątki w zarządzanych wątkach
Począwszy od programu .NET Framework w wersji 2.0 środowisko uruchomieniowe języka wspólnego pozwala najbardziej nieobsługiwanych wyjątków w wątkach, aby kontynuować naturalnie. W większości przypadków oznacza to, że nieobsługiwany wyjątek powoduje zamknięcie aplikacji.  
  
> [!NOTE]
>  Jest to znaczące zmiany z wersji systemu .NET Framework 1.0 i 1.1, która zawiera backstop dla wielu nieobsłużonych wyjątków — na przykład nieobsłużonych wyjątków z wątków z puli wątków. Zobacz [zmiany z wcześniejszych wersji](#ChangeFromPreviousVersions) w dalszej części tego tematu.  
  
 Środowisko uruchomieniowe języka wspólnego zawiera wyjątki backstop na pewnych nieobsłużony, które są używane do sterowania przepływem programu:  
  
-   A <xref:System.Threading.ThreadAbortException> jest zgłaszany w wątku, ponieważ <xref:System.Threading.Thread.Abort%2A> została wywołana.  
  
-   <xref:System.AppDomainUnloadedException> Jest zgłaszany w wątku, ponieważ Trwa zwalnianie domeny aplikacji, w którym wykonywany jest wątek.  
  
-   Środowisko uruchomieniowe języka wspólnego lub procesu hosta kończy wątku, zgłaszając wyjątek wewnętrzny.  
  
 Jeśli dowolny z tych wyjątków nieobsługiwanego w wątkach, utworzone przez środowisko uruchomieniowe języka wspólnego wątek kończy się wyjątek, ale środowisko uruchomieniowe języka wspólnego nie zezwala na wyjątek kontynuować.  
  
 Jeśli te wyjątki są nieobsługiwane w głównym wątku, lub w wątkach, które wprowadzono środowisko uruchomieniowe z kodem niezarządzanym pochodzą normalnie, co spowoduje przerwanie aplikacji.  
  
> [!NOTE]
>  Istnieje możliwość dla środowiska uruchomieniowego do zgłoszenia nieobsługiwany wyjątek, zanim dowolnego kodu zarządzanego miała szansę, aby zainstalować program obsługi wyjątku. Mimo że kod zarządzany miał możliwość obsługi takiego wyjątku, wyjątek może przejść w sposób naturalny.  
  
## <a name="exposing-threading-problems-during-development"></a>Udostępnianie wątkowości problemy podczas programowania  
 Jeśli wątki mogą zakończyć się niepowodzeniem w trybie dyskretnym, bez przerywania aplikacji poważnych problemów programowania przejść niewykryte. Jest to konkretnych problemów dla usług i innych aplikacji uruchamianych przez dłuższy czas. Ponieważ wątki kończyć się niepowodzeniem, stan programu stopniowo ulegnie uszkodzeniu. Limitu może obniżyć wydajność aplikacji lub aplikacji może być zawieszeniu.  
  
 Zezwolenie nieobsługiwanych wyjątków w wątkach, aby kontynuować naturalnie, aż do zakończenia programu, system operacyjny udostępnia takie problemy podczas tworzenia i testowania aplikacji. Raporty o błędach programu zakończenia obsługi debugowania.  
  
<a name="ChangeFromPreviousVersions"></a>   
## <a name="change-from-previous-versions"></a>Zmiana z poprzednich wersji  
 Najbardziej znacząca zmiana dotyczy tylko zarządzanych wątków. W wersjach programu .NET Framework 1.0 i 1.1 środowisko uruchomieniowe języka wspólnego dostarcza backstop dla nieobsłużonych wyjątków w następujących sytuacjach:  
  
-   Brak coś takiego jak nieobsługiwany wyjątek w wątku z puli wątków. Gdy zadanie zgłasza wyjątek, który nie obsługuje, środowisko uruchomieniowe Wyświetla ślad stosu wyjątku do konsoli, a następnie zwraca wątku do puli wątków.  
  
-   Brak coś takiego nieobsługiwany wyjątek w wątku utworzonych za pomocą <xref:System.Threading.Thread.Start%2A> metody <xref:System.Threading.Thread> klasy. Gdy kod działający na takich wątków zgłasza wyjątek, który nie obsługuje, środowisko uruchomieniowe Wyświetla ślad stosu wyjątku do konsoli i bez problemu zmieniała kończy wątku.  
  
-   Brak coś takiego jak nieobsługiwany wyjątek w wątku finalizatora. Gdy finalizator zgłasza wyjątek, który nie obsługuje, środowisko uruchomieniowe Wyświetla ślad stosu wyjątku do konsoli, a następnie umożliwia wątek finalizatora ponownie uruchomić finalizatorów.  
  
 Stan pierwszego planu i tła wątków zarządzanych nie wpływa na to zachowanie.  
  
 Dla nieobsłużonych wyjątków w wątkach, pochodzących z kodem niezarządzanym różnica jest bardziej subtelny. Okno dialogowe dołączania JIT środowiska uruchomieniowego zastępuje okno dialogowe systemu operacyjnego dla wyjątków zarządzanych lub natywnych wyjątków w wątkach, które zostały przekazane za pośrednictwem kodu natywnego. Proces kończy się we wszystkich przypadkach.  
  
### <a name="migrating-code"></a>Migrowanie kodu  
 Ogólnie rzecz biorąc zmiana udostępni wcześniej nierozpoznany problemów programowania, aby ich. W niektórych przypadkach jednak programistów wprowadzić jakieś zalet backstop środowiska uruchomieniowego, na przykład zakończyć wątków. W zależności od sytuacji powinni rozważyć jedną z następujących strategii migracji:  
  
-   Restrukturyzacja kodu, dzięki czemu wątek kończy działanie bez problemu zmieniała po odebraniu sygnału.  
  
-   Użyj <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metodę, aby przerwać wątku.  
  
-   Wątek musi zostać zatrzymana, aby kontynuować zakończenia procesu, aby wątek wątku w tle, aby było automatycznie przerywane na zakończenie procesu.  
  
 We wszystkich przypadkach strategii powinien być zgodny z wytycznymi projektowania dla wyjątków. Zobacz [projektowania wskazówki dotyczące wyjątków](../../../docs/standard/design-guidelines/exceptions.md).  
  
### <a name="application-compatibility-flag"></a>Flagi zgodności aplikacji  
 Jako tymczasowy zgodności, Administratorzy mogą umieszczać flagę zgodności w `<runtime>` sekcję pliku konfiguracji aplikacji. Powoduje to, że środowisko uruchomieniowe języka wspólnego powraca do zachowania w wersjach 1.0 i 1.1.  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a>Zastąpienie hosta  
 W .NET Framework w wersji 2.0, można użyć niezarządzany host [iclrpolicymanager —](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interfejsu API hostingu, aby zastąpić domyślne nieobsługiwane wyjątki od zasad środowiska uruchomieniowego języka wspólnego. [Iclrpolicymanager::setunhandledexceptionpolicy —](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) funkcja jest używana do ustawiania zasad dla nieobsłużonych wyjątków.  
  
## <a name="see-also"></a>Zobacz także

- [Zarządzana wątkowość — podstawy](../../../docs/standard/threading/managed-threading-basics.md)
