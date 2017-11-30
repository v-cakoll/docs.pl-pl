---
title: "Wyjątki w zarządzanych wątkach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ebb5559d300bb3db34fe640e87eb8b9e67931561
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-in-managed-threads"></a>Wyjątki w zarządzanych wątkach
Środowisko uruchomieniowe języka wspólnego w programie .NET Framework w wersji 2.0, umożliwia najbardziej nieobsługiwanych wyjątków w wątkach, aby kontynuować naturalny. W większości przypadków oznacza to, że nieobsługiwany wyjątek powoduje zamknięcie aplikacji.  
  
> [!NOTE]
>  Jest to istotna zmiana z wersji systemu .NET Framework 1.0 i 1.1, która zapewnia backstop dla wielu nieobsługiwanych wyjątków — na przykład nieobsługiwane wyjątki w wątku puli wątków. Zobacz [zmiany z wcześniejszych wersji](#ChangeFromPreviousVersions) dalszej części tego tematu.  
  
 Środowisko uruchomieniowe języka wspólnego zapewnia wyjątki backstop dla niektórych nieobsługiwany, które są używane do sterowania przepływem programu:  
  
-   A <xref:System.Threading.ThreadAbortException> wyjątek w wątku, ponieważ <xref:System.Threading.Thread.Abort%2A> została wywołana.  
  
-   <xref:System.AppDomainUnloadedException> Wyjątek w wątku, ponieważ domena aplikacji, w którym jest wykonywany wątek jest zwalniany.  
  
-   Środowisko uruchomieniowe języka wspólnego lub procesu hosta kończy wątku przez Zgłaszanie wyjątku wewnętrznego.  
  
 Jeśli żadnego z tych wyjątków są nieobsługiwane w wątkach utworzone przez środowisko uruchomieniowe języka wspólnego, wyjątek kończy wątek, ale środowisko uruchomieniowe języka wspólnego nie zezwalaj na wyjątek kontynuować.  
  
 Jeśli te wyjątki są nieobsługiwane w głównym wątku lub wątków, które wprowadzono środowiska uruchomieniowego z kodem niezarządzanym pochodzą normalnie, co powoduje zakończenie aplikacji.  
  
> [!NOTE]
>  Istnieje możliwość środowiska uruchomieniowego do throw nieobsługiwany wyjątek przed żadnego kodu zarządzanego miał możliwość zainstalowania obsługi wyjątków. Mimo że kodu zarządzanego ma możliwość obsługi takich wyjątku, wyjątek można kontynuować naturalny.  
  
## <a name="exposing-threading-problems-during-development"></a>Udostępnianie wątkowość problemy podczas tworzenia  
 Jeśli wątki mogą zakończyć się niepowodzeniem w trybie dyskretnym, bez przerywania aplikacji, poważnych problemów programowania może nie zostać wykryte. Jest to konkretnych problemów dotyczących usług i innych aplikacji uruchamianych przez dłuższy czas. Jak wątki kończyć się niepowodzeniem, stan programu stopniowo uległa uszkodzeniu. Może obniżyć wydajność aplikacji lub aplikacji może zostać zawieszone.  
  
 Stosowanie nieobsługiwanych wyjątków w wątków, aby kontynuować naturalnie, aż do zakończenia programu, systemu operacyjnego przedstawia takich problemów podczas projektowania i testowania. Raporty o błędach programu zakończenia obsługi debugowania.  
  
<a name="ChangeFromPreviousVersions"></a>   
## <a name="change-from-previous-versions"></a>Zmień z poprzednich wersji  
 Najbardziej znaczących zmian dotyczących zarządzanych wątków. Środowisko uruchomieniowe języka wspólnego w wersji systemu .NET Framework 1.0 i 1.1 zawiera backstop nieobsługiwanych wyjątków w następujących sytuacjach:  
  
-   Coś takiego jak nieobsługiwany wyjątek w wątku puli wątków nie istnieje. Gdy zadanie zgłasza wyjątek, który nie obsługuje, środowisko uruchomieniowe drukuje śladu stosu wyjątku do konsoli, a następnie zwraca wątku do puli wątków.  
  
-   Nie należy nie takich jak nieobsługiwany wyjątek w wątku utworzone za pomocą <xref:System.Threading.Thread.Start%2A> metody <xref:System.Threading.Thread> klasy. Gdy kodu uruchamianego w takich wątku zgłasza wyjątek, który nie obsługuje, środowiska uruchomieniowego drukuje śladu stosu wyjątku do konsoli i bezpiecznie zakończenie wątku.  
  
-   Coś takiego jak nieobsługiwany wyjątek w wątku finalizatora nie istnieje. Gdy finalizator zgłasza wyjątek, który nie obsługuje, środowisko uruchomieniowe drukuje śladu stosu wyjątku do konsoli, a następnie umożliwia wątku finalizatora wznowić wykonywanie finalizatory.  
  
 Pierwszym planie lub w tle stan zarządzanego wątku nie ma wpływu na tego zachowania.  
  
 W przypadku nieobsługiwanych wyjątków w wątkach pochodzących z kodem niezarządzanym różnica jest bardziej niewielkie. Okno dialogowe dołączania JIT środowiska uruchomieniowego zastępuje okna dialogowego systemu operacyjnego zarządzanych czy natywnego wyjątki w wątkach, które zostały przekazane za pomocą kodu natywnego. Proces kończy się we wszystkich przypadkach.  
  
### <a name="migrating-code"></a>Migrowanie kodu  
 Ogólnie rzecz biorąc zmiana powoduje to udostępnienie wcześniej nierozpoznany problemów programowania tak, aby ich. W niektórych przypadkach jednak programiści mogą miały zaletą backstop środowiska uruchomieniowego, na przykład w celu zakończenia wątków. W zależności od sytuacji ich należy wziąć pod uwagę jedną z następujących strategii migracji:  
  
-   Restrukturyzacja kod, więc wątek zamyka bezpieczne po odebraniu sygnału.  
  
-   Użyj <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metodę, aby przerwać wątek.  
  
-   Wątek musi zostać zatrzymana, dzięki czemu można kontynuować zakończenia procesu, aby wątek wątku w tle, aby automatycznie zostanie zakończony na zakończenie procesu.  
  
 We wszystkich przypadkach strategii postępować zgodnie z wytycznymi projektowania dla wyjątków. Zobacz [projektowania wytyczne dla wyjątków](../../../docs/standard/design-guidelines/exceptions.md).  
  
### <a name="application-compatibility-flag"></a>Flaga zgodności aplikacji  
 Jako środek tymczasowy zgodności Administratorzy można umieścić flagę zgodności w `<runtime>` sekcji pliku konfiguracji aplikacji. Powoduje to plików wykonywalnych języka powrócić do zachowania w wersjach 1.0 i 1.1.  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a>Zastąpienie hosta  
 W programie .NET Framework w wersji 2.0, można używać hosta niezarządzane [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interfejsu w interfejsie API hostingu, aby zastąpić domyślną nieobsłużony wyjątek zasady środowisko uruchomieniowe języka wspólnego. [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) funkcja jest używana do ustawiania zasad dla nieobsługiwanych wyjątków.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzana wątkowość — podstawy](../../../docs/standard/threading/managed-threading-basics.md)
