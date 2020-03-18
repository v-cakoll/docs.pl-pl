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
ms.openlocfilehash: 6c14c60b30f8f70aa5e888ed45d6f867154e18d8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159653"
---
# <a name="exceptions-in-managed-threads"></a>Wyjątki w zarządzanych wątkach
Począwszy od .NET Framework w wersji 2.0, środowisko uruchomieniowe języka wspólnego umożliwia większość nieobsługiwanych wyjątków w wątkach, aby postępować naturalnie. W większości przypadków oznacza to, że nieobsługiwany wyjątek powoduje zakończenie aplikacji.  
  
> [!NOTE]
> Jest to istotna zmiana w stosunku do .NET Framework w wersjach 1.0 i 1.1, które zapewniają backstop dla wielu nieobsługiwanych wyjątków — na przykład nieobsługiwanych wyjątków w wątkach puli wątków. Zobacz [Zmiany z poprzednich wersji](#ChangeFromPreviousVersions) w dalszej części tego tematu.  
  
 Czas wykonywania języka wspólnego zapewnia backstop dla niektórych nieobsługiwanych wyjątków, które są używane do kontrolowania przepływu programu:  
  
- A <xref:System.Threading.ThreadAbortException> jest wyrzucany <xref:System.Threading.Thread.Abort%2A> w wątku, ponieważ został wywołany.  
  
- Zostanie <xref:System.AppDomainUnloadedException> wyrzucone w wątku, ponieważ domena aplikacji, w której jest wykonywany wątek, jest zwalniana.  
  
- Czas wykonywania języka wspólnego lub proces hosta kończy wątek, zgłaszanie wyjątek wewnętrzny.  
  
 Jeśli którykolwiek z tych wyjątków są nieobsługiwane w wątkach utworzonych przez program runtime języka wspólnego, wyjątek kończy wątek, ale czas wykonywania języka wspólnego nie zezwala na wyjątek, aby kontynuować.  
  
 Jeśli te wyjątki są nieobsługiwane w wątku głównym lub w wątkach, które wprowadziły czas wykonywania z kodu niezarządzanego, postępują normalnie, powodując zakończenie aplikacji.  
  
> [!NOTE]
> Jest możliwe dla programu runtime zgłosić nieobsługiwany wyjątek, zanim kod zarządzany miał szansę zainstalować program obsługi wyjątków. Mimo że kod zarządzany nie miał szans na obsługę takiego wyjątku, wyjątek może postępować naturalnie.  
  
## <a name="exposing-threading-problems-during-development"></a>Ujawnianie problemów z wątkowaniem podczas tworzenia  
 Gdy wątki mogą zakończyć się niepowodzeniem w trybie dyskretnym, bez kończenia aplikacji, poważne problemy z programowaniem mogą pozostać niewykryte. Jest to szczególny problem dla usług i innych aplikacji, które działają przez dłuższy czas. Gdy wątki zawodzą, stan programu stopniowo ulega uszkodzeniu. Wydajność aplikacji może ulec pogorszeniu lub aplikacja może przestać odpowiadać.  
  
 Zezwalanie nieobsługiwanych wyjątków w wątkach, aby postępować naturalnie, dopóki system operacyjny nie zakończy program, udostępnia takie problemy podczas opracowywania i testowania. Raporty o błędach dotyczące zakończenia programu obsługują debugowanie.  
  
<a name="ChangeFromPreviousVersions"></a>
## <a name="change-from-previous-versions"></a>Zmiana z poprzednich wersji  
 Najważniejsza zmiana dotyczy zarządzanych wątków. W .NET Framework w wersjach 1.0 i 1.1 czas wykonywania języka wspólnego zapewnia backstop dla nieobsługiwanych wyjątków w następujących sytuacjach:  
  
- Nie ma czegoś takiego jak nieobsługiwany wyjątek w wątku puli wątków. Gdy zadanie zgłasza wyjątek, który nie obsługuje, w czasie wykonywania drukuje śledzenia stosu wyjątków do konsoli, a następnie zwraca wątek do puli wątków.  
  
- Nie ma czegoś takiego jak nieobsługiwany wyjątek w wątku utworzonym <xref:System.Threading.Thread.Start%2A> za pomocą metody <xref:System.Threading.Thread> klasy. Gdy kod uruchomiony w takim wątku zgłasza wyjątek, który nie obsługuje, w czasie wykonywania drukuje śledzenia stosu wyjątku do konsoli, a następnie bezpiecznie kończy wątek.  
  
- Nie ma czegoś takiego jak nieobsługiwany wyjątek w wątku finalizatora. Gdy finalizator zgłasza wyjątek, który nie obsługuje, w czasie wykonywania drukuje śledzenia stosu wyjątków do konsoli, a następnie umożliwia finalizatorwątku wznowić uruchomione finalizatorów.  
  
 Pierwszy plan lub stan tła zarządzanego wątku nie ma wpływu na to zachowanie.  
  
 W przypadku nieobsługiwanych wyjątków w wątkach pochodzących z kodu niezarządzanego różnica jest bardziej subtelna. Okno dialogowe jit-attach w czasie wykonywania wywłaszcza okno dialogowe systemu operacyjnego dla wyjątków zarządzanych lub wyjątków macierzystych w wątkach, które przeszły przez kod macierzysty. Proces kończy się we wszystkich przypadkach.  
  
### <a name="migrating-code"></a>Migracja kodu  
 Ogólnie rzecz biorąc, zmiana spowoduje ujawnienie wcześniej nierozpoznanych problemów z programowaniem, dzięki czemu można je naprawić. W niektórych przypadkach jednak programiści mogą skorzystać z backstop ujmowego czasu wykonywania, na przykład do zakończenia wątków. W zależności od sytuacji powinni oni rozważyć jedną z następujących strategii migracji:  
  
- Zrestrukturyzuj kod, aby wątek wychodzi bezpiecznie po odebraniu sygnału.  
  
- Użyj <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> metody, aby przerwać wątek.  
  
- Jeśli wątek musi zostać zatrzymany, aby zakończenie procesu można kontynuować, należy wątku wątku w tle, tak aby został automatycznie zakończony przy zakończeniu procesu.  
  
 We wszystkich przypadkach strategia powinna być zgodna z wytycznymi projektowymi dotyczącymi wyjątków. Zobacz [Wskazówki dotyczące projektowania wyjątków](../../../docs/standard/design-guidelines/exceptions.md).  
  
### <a name="application-compatibility-flag"></a>Flaga zgodności aplikacji  
 Jako tymczasowa miara zgodności administratorzy `<runtime>` mogą umieszczać flagę zgodności w sekcji pliku konfiguracji aplikacji. Powoduje to, że wspólny program uruchomieniowy języka, aby powrócić do zachowania w wersjach 1.0 i 1.1.  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a>Zastępowanie hosta  
 W .NET Framework w wersji 2.0 host niezarządzany może używać interfejsu [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) w interfejsie Hosta, aby zastąpić domyślne nieobsługiwane zasady wyjątków w czasie wykonywania wspólnego języka. Funkcja [ICLRPolicyManager::SetUnhandledExceptionPolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) jest używana do ustawiania zasad dla nieobsługiwanych wyjątków.  
  
## <a name="see-also"></a>Zobacz też

- [Zarządzana wątkowość — podstawy](../../../docs/standard/threading/managed-threading-basics.md)
