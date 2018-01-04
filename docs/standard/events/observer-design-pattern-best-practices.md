---
title: "Wzorzec projektowy obserwatora — Najlepsze praktyki"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- observer design pattern [.NET Framework], best practices
- best practices [.NET Framework], observer design pattern
ms.assetid: c834760f-ddd4-417f-abb7-a059679d5b8c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dc42ccd425b52719b2b69525d2bbbe4607a19982
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="observer-design-pattern-best-practices"></a>Wzorzec projektowy obserwatora — Najlepsze praktyki
W programie .NET Framework wzorzec projektowy obserwatora są zaimplementowane jako zestaw interfejsów. <xref:System.IObservable%601?displayProperty=nameWithType> Interfejsu reprezentuje dostawcy danych, który również jest odpowiedzialny za zapewnienie <xref:System.IDisposable> implementację, która umożliwia obserwatorów zrezygnować z powiadomień. <xref:System.IObserver%601?displayProperty=nameWithType> Interfejsu reprezentuje obserwatora. W tym temacie opisano najważniejsze wskazówki, które deweloperzy należy wykonać podczas implementowania wzorzec projektowy obserwatora za pomocą tych interfejsów.  
  
## <a name="threading"></a>Wątkowość  
 Zazwyczaj implementuje dostawcę <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> implementuje metody przez dodanie określonego obserwatora do listy subskrybentów, reprezentowanego przez niektóre obiektu kolekcji, a <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metody przez usunięcie określonego obserwatora z listy subskrybentów. Obserwator można wywołać metody w dowolnym momencie. Ponadto, ponieważ dostawcy/obserwatora kontraktu nie określa, kto jest odpowiedzialny za anulowanie po <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> metody wywołania zwrotnego, dostawcy i obserwatora może spróbować usunąć tego samego członka z listy. Z powodu tej możliwości zarówno <xref:System.IObservable%601.Subscribe%2A> i <xref:System.IDisposable.Dispose%2A> metody powinny być bezpieczne wątkowo. Zwykle to polega na użyciu [kolekcji współbieżnych](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md) lub blokady. Implementacje, które nie są wątkowo powinny jawnie dokumentu, które nie są.  
  
 Wszelkie dodatkowe gwarancje ma być określone w warstwie na górze umowa dostawcy/obserwatora. Implementacje powinny wyróżnienia wyraźnie podczas ich nałożyć dodatkowe wymagania dotyczące uniknąć pomyłek użytkownika o kontraktu obserwatora.  
  
## <a name="handling-exceptions"></a>Obsługa wyjątków  
 Z powodu luźne powiązanie między dostawcą danych i obserwatora wyjątków we wzorcu projektowym obserwatora mają być informacyjny. Ma to wpływ na sposób dostawców i obserwatorów Obsługa wyjątków we wzorcu projektowym obserwatora.  
  
### <a name="the-provider----calling-the-onerror-method"></a>Dostawca--Wywołanie OnError — metoda  
 <xref:System.IObserver%601.OnError%2A> — Metoda ma komunikat informacyjny do obserwatorów, podobnie jak <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> metody. Jednak <xref:System.IObserver%601.OnNext%2A> — metoda zaprojektowano pod kątem obserwatora za pomocą bieżącego lub zaktualizowanych danych, podczas gdy <xref:System.IObserver%601.OnError%2A> metoda jest przeznaczona do wskazywania nie można dostarczyć prawidłowych danych dostawcy.  
  
 Dostawcy należy stosować następujące najlepsze rozwiązania, gdy obsługa wyjątków i wywoływania <xref:System.IObserver%601.OnError%2A> metody:  
  
-   Dostawca musi obsługiwać własne wyjątki, jeśli ma ona żadnych określonych wymagań.  
  
-   Dostawca należy spodziewać się lub nie wymagają, aby obserwatorów obsługi wyjątków w żadnym konkretnym.  
  
-   Dostawca powinny wywoływać <xref:System.IObserver%601.OnError%2A> metodą podczas obsługi wyjątku obniża możliwość udostępniania aktualizacji. Informacje o takich wyjątków mogą być przekazywane do obserwatora. W pozostałych przypadkach jest niepotrzebna powiadomiono obserwatorów Wystąpił wyjątek.  
  
 Raz wywołania dostawcy <xref:System.IObserver%601.OnError%2A> lub <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> metody, nie powinny istnieć żadne dodatkowe powiadomienia, a dostawca subskrypcję można anulować jego obserwatorów. Jednak obserwatora można również samodzielnie w każdej chwili zrezygnować, zarówno w tym przed i po otrzymaniu <xref:System.IObserver%601.OnError%2A> lub <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> powiadomień. Wzorzec projektowy obserwatora nie określa, czy dostawca lub obserwatora jest odpowiedzialny za anulowanie; w związku z tym istnieje możliwość, że oba podjąć próbę anulowania subskrypcji. Zwykle gdy obserwatorów subskrypcję, zostaną usunięte z kolekcji subskrybentów. W aplikacji jednowątkowe <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji powinien upewnij się, że odwołanie do obiektu jest prawidłowa i czy obiekt jest członkiem kolekcji subskrybentów przed próbą jej usunięcia. W aplikacji wielowątkowych kolekcji wątkowo obiektów, takich jak <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> obiektów, powinien być używany.  
  
### <a name="the-observer----implementing-the-onerror-method"></a>Obserwator — Wdrażanie OnError — metoda  
 Po obserwatora otrzyma powiadomienie o błędzie od dostawcy, obserwatora powinny traktować wyjątek celów informacyjnych i nie powinno być wymagane do wykonywać żadnych czynności w szczególności.  
  
 Obserwator należy stosować następujące najlepsze rozwiązania odpowiadać na <xref:System.IObserver%601.OnError%2A> wywołanie metody od dostawcy:  
  
-   Obserwator nie powinien zgłosić wyjątki od ich implementacji interfejsu, takich jak <xref:System.IObserver%601.OnNext%2A> lub <xref:System.IObserver%601.OnError%2A>. Jednak jeśli obserwatora zgłaszają wyjątki, należy oczekiwać te wyjątki, aby przejść nieobsługiwany.  
  
-   Aby zachować stosu wywołań obserwatora, który chce throw <xref:System.Exception> obiektu, który został przekazany do jego <xref:System.IObserver%601.OnError%2A> metoda powinna być zawijana wyjątek przed zgłaszanie go. W tym celu należy używać obiektu standardowe wyjątku.  
  
## <a name="additional-best-practices"></a>Dodatkowe wskazówki  
 Próba wyrejestrowania w <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metody może spowodować odwołanie o wartości null. Dlatego zaleca się unikanie tym rozwiązaniem.  
  
 Chociaż można dołączyć obserwatora do wielu dostawców, wzorzec zalecane jest dołączenie <xref:System.IObserver%601> tylko jedno wystąpienie <xref:System.IObservable%601> wystąpienia.  
  
## <a name="see-also"></a>Zobacz też  
 [Wzorzec projektowy obserwatora](../../../docs/standard/events/observer-design-pattern.md)  
 [Instrukcje: Implementowanie obserwatora](../../../docs/standard/events/how-to-implement-an-observer.md)  
 [Instrukcje: Implementowanie dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md)
