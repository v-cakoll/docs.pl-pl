---
title: Wzorzec projektowy obserwatora — Najlepsze praktyki
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- observer design pattern [.NET Framework], best practices
- best practices [.NET Framework], observer design pattern
ms.assetid: c834760f-ddd4-417f-abb7-a059679d5b8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03b77074323346e1a26fa07dc1ec873152da356b
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45519672"
---
# <a name="observer-design-pattern-best-practices"></a>Wzorzec projektowy obserwatora — Najlepsze praktyki
W .NET Framework po wzorcu projektowania obserwatora są zaimplementowane jako zestaw interfejsów. <xref:System.IObservable%601?displayProperty=nameWithType> Interfejs reprezentuje dostawcy danych, który jest również odpowiedzialny za zapewnienie <xref:System.IDisposable> implementację, która umożliwia obserwatorów zrezygnować z powiadomień. <xref:System.IObserver%601?displayProperty=nameWithType> Interfejs reprezentuje obserwatora. W tym temacie opisano najlepsze rozwiązania, które deweloperzy powinni stosować podczas implementowania po wzorcu projektowania obserwatora, za pomocą tych interfejsów.  
  
## <a name="threading"></a>Wątkowość  
 Zwykle implementuje dostawcę <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metoda przez dodanie określonego obserwatora do listy subskrybentów, który jest reprezentowany przez niektóre obiekt kolekcji, a implementuje <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metody przez usunięcie określonego obserwatora z listy subskrybentów. Obserwator może wywoływać te metody, w dowolnym momencie. Ponadto, ponieważ kontrakt dostawcy/obserwatorów nie określa kto jest odpowiedzialny za anulowania subskrypcji po <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> metody wywołania zwrotnego, dostawcy i obserwatora może spróbować usunąć tego samego członka z listy. Ze względu na tę możliwość zarówno <xref:System.IObservable%601.Subscribe%2A> i <xref:System.IDisposable.Dispose%2A> powinny móc wywoływać metody metodą o bezpiecznych wątkach. Zazwyczaj polega to na użyciu [kolekcji współbieżnych](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md) lub blokady. Implementacje, które nie są wątkowo jawnie powinny zostać udokumentowane, które nie są one.  
  
 Wszelkie dodatkowe gwarancje musi określać w warstwie na podstawie umowy dostawca/obserwatora. Implementujące obiekty powinny wyróżnienia wyraźnie, podczas ich nakładać dodatkowe wymagania, aby uniknąć pomyłek użytkowników o kontraktu obserwatora.  
  
## <a name="handling-exceptions"></a>Obsługa wyjątków  
 Ze względu na luźne powiązanie między dostawcą danych i obserwatora wyjątków we wzorcu projektowym obserwatora mają być informacyjne. Ma to wpływ na sposób obsługi wyjątków we wzorcu projektowym obserwatora dostawców i obserwatorów.  
  
### <a name="the-provider----calling-the-onerror-method"></a>Dostawca--Wywoływania OnError — metoda  
 <xref:System.IObserver%601.OnError%2A> Metoda ma pełnić komunikat informacyjny do obserwatorów, znacznie takich jak <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> metody. Jednak <xref:System.IObserver%601.OnNext%2A> metoda umożliwia obserwatora przy użyciu bieżących lub zaktualizowanych danych, natomiast <xref:System.IObserver%601.OnError%2A> metodę zaprojektowano w celu wskazania, że dostawca jest nie można podać prawidłowe dane.  
  
 Dostawca należy stosować następujące najlepsze rozwiązania, podczas obsługi wyjątków i wywoływać metodę <xref:System.IObserver%601.OnError%2A> metody:  
  
-   Dostawca musi obsługiwać własne wyjątki, jeśli ma żadnych szczególnych wymagań.  
  
-   Dostawca powinien oczekuje ani nie wymaga, że obserwatorów obsługi wyjątków w żadnym określonym.  
  
-   Dostawca powinien wywoływać <xref:System.IObserver%601.OnError%2A> metodą podczas obsługi wyjątku, który obniża możliwości na potrzeby udostępniania aktualizacji. Informacji na temat wyjątków może być przekazywany do obserwatora. W innych przypadkach nie ma potrzeby powiadomić obserwatorów wyjątek.  
  
 Raz wywołania dostawcy <xref:System.IObserver%601.OnError%2A> lub <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> metody powinny istnieć żadne dalsze powiadomienia, a dostawca swoją subskrypcję możesz cofnąć jego obserwatorów. Jednak obserwatorzy również anulować subskrypcję samodzielnie w dowolnym momencie, w tym przed i po otrzymaniu <xref:System.IObserver%601.OnError%2A> lub <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> powiadomień. Wzorzec projektowy obserwatora nie określa, czy przez dostawcę lub obserwatora jest odpowiedzialny za anulowania subskrypcji; w związku z tym, istnieje możliwość, że oba podjąć próbę anulowania subskrypcji. Zazwyczaj gdy obserwatorów subskrypcję, są usuwane z kolekcji subskrybentów. W przypadku aplikacji jednowątkowe <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji należy upewnić się, że odwołanie do obiektu jest prawidłowa i czy obiekt jest elementem członkowskim kolekcji subskrybentów przed próbą usunięcia go. W aplikacji wielowątkowych, kolekcję wątków obiektu, takie jak <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> obiektu, powinien być używany.  
  
### <a name="the-observer----implementing-the-onerror-method"></a>Obserwator — Implementowanie OnError — metoda  
 Gdy obserwatora otrzymuje powiadomienia o błędzie od dostawcy, obserwator powinien traktować wyjątek informacyjny i nie powinno być wymagane podjęcie dowolną określoną akcję.  
  
 Obserwator należy stosować następujące najlepsze rozwiązania, podczas odpowiadania na <xref:System.IObserver%601.OnError%2A> wywołania metody od dostawcy:  
  
-   Obserwator nie powinna zgłaszać wyjątków z jego implementacji interfejsu, takich jak <xref:System.IObserver%601.OnNext%2A> lub <xref:System.IObserver%601.OnError%2A>. Jednak jeśli obserwatora zgłaszają wyjątki, należy oczekiwać te wyjątki, aby nieobsłużony.  
  
-   Aby zachować stos wywołań, obserwatora, który chce throw <xref:System.Exception> obiektu, który został przekazany do jego <xref:System.IObserver%601.OnError%2A> metoda powinna zawijać wyjątek, zanim zostanie on zgłoszony. Obiekt wyjątku standardowa stosuje się do tego celu.  
  
## <a name="additional-best-practices"></a>Dodatkowe wskazówki  
 Podjęto próbę wyrejestrować w <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metody może spowodować odwołanie o wartości null. Dlatego zaleca się, należy unikać tej praktyką.  
  
 Chociaż istnieje możliwość dołączenia obserwatora do wielu dostawców, zalecany wzorzec jest dołączenie <xref:System.IObserver%601> tylko jedno wystąpienie <xref:System.IObservable%601> wystąpienia.  
  
## <a name="see-also"></a>Zobacz także

- [Wzorzec projektowy obserwatora](../../../docs/standard/events/observer-design-pattern.md)  
- [Instrukcje: Implementowanie obserwatora](../../../docs/standard/events/how-to-implement-an-observer.md)  
- [Instrukcje: Implementowanie dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md)
