---
title: Wzorzec projektowy obserwatora — Najlepsze praktyki
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- observer design pattern [.NET Framework], best practices
- best practices [.NET Framework], observer design pattern
ms.assetid: c834760f-ddd4-417f-abb7-a059679d5b8c
ms.openlocfilehash: 2da29e0baf429142707d0ddd39b1a11c13a17a90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141540"
---
# <a name="observer-design-pattern-best-practices"></a>Wzorzec projektowy obserwatora — Najlepsze praktyki
W .NET Framework wzorzec projektowania obserwatora jest implementowany jako zestaw interfejsów. Interfejs <xref:System.IObservable%601?displayProperty=nameWithType> reprezentuje dostawcę danych, który jest również <xref:System.IDisposable> odpowiedzialny za zapewnienie implementacji, która pozwala obserwatorom anulować subskrypcję powiadomień. Interfejs <xref:System.IObserver%601?displayProperty=nameWithType> reprezentuje obserwatora. W tym temacie opisano najlepsze rozwiązania, które deweloperzy powinni przestrzegać podczas implementowania wzorca projektu obserwatora przy użyciu tych interfejsów.  
  
## <a name="threading"></a>Wątkowość  
 Zazwyczaj dostawca implementuje <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metodę, dodając określonego obserwatora do listy subskrybentów, który jest reprezentowany przez <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> niektóre obiektu kolekcji i implementuje metodę, usuwając określonego obserwatora z listy subskrybentów. Obserwator może wywołać te metody w dowolnym momencie. Ponadto ponieważ umowy provider/observer nie określa, kto jest odpowiedzialny za <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> wypisanie subskrypcji po metodzie wywołania wywołania, dostawca i obserwator może zarówno spróbować usunąć tego samego członka z listy. Ze względu na tę <xref:System.IObservable%601.Subscribe%2A> <xref:System.IDisposable.Dispose%2A> możliwość, zarówno i metody powinny być bezpieczne dla wątków. Zazwyczaj wiąże się to przy użyciu [kolekcji równoczesnych](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md) lub blokady. Implementacje, które nie są bezpieczne dla wątków należy jawnie dokument, że nie są.  
  
 Wszelkie dodatkowe gwarancje muszą być określone w warstwie na podstawie umowy dostawcy/obserwatora. Realizatorzy powinni wyraźnie wywołać, gdy nakładają dodatkowe wymagania, aby uniknąć nieporozumień użytkownika na temat umowy obserwatora.  
  
## <a name="handling-exceptions"></a>Obsługa wyjątków  
 Ze względu na luźne sprzężenie między dostawcą danych a obserwatorem wyjątki w wzorcu projektowania obserwatora mają być informacyjne. Ma to wpływ na sposób, w jaki dostawcy i obserwatorzy obsługują wyjątki w wzorzec projektowania obserwatora.  
  
### <a name="the-provider----calling-the-onerror-method"></a>Dostawca - Wywołanie OnError Metoda  
 Metoda <xref:System.IObserver%601.OnError%2A> jest przeznaczona jako komunikat informacyjny dla obserwatorów, podobnie jak <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> metoda. Jednak <xref:System.IObserver%601.OnNext%2A> metoda jest przeznaczona do zapewnienia obserwatorowi bieżących lub <xref:System.IObserver%601.OnError%2A> zaktualizowanych danych, podczas gdy metoda ma na celu wskazanie, że dostawca nie jest w stanie podać prawidłowych danych.  
  
 Dostawca powinien postępować zgodnie z następującymi <xref:System.IObserver%601.OnError%2A> najlepszymi rozwiązaniami podczas obsługi wyjątków i wywoływania metody:  
  
- Dostawca musi obsługiwać własne wyjątki, jeśli ma jakieś szczególne wymagania.  
  
- Dostawca nie powinien oczekiwać lub wymagać, aby obserwatorzy obsługili wyjątki w określony sposób.  
  
- Dostawca powinien wywołać <xref:System.IObserver%601.OnError%2A> metodę, gdy obsługuje wyjątek, który zagraża jego zdolność do dostarczania aktualizacji. Informacje na temat takich wyjątków mogą być przekazywane obserwatorowi. W innych przypadkach nie ma potrzeby powiadamiania obserwatorów o wyjątku.  
  
 Gdy dostawca wywołuje <xref:System.IObserver%601.OnError%2A> <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> lub metody, nie powinno być żadnych dalszych powiadomień, a dostawca może anulować subskrypcję swoich obserwatorów. Obserwatorzy mogą jednak zrezygnować z subskrypcji w dowolnym momencie, <xref:System.IObserver%601.OnError%2A> w <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> tym zarówno przed otrzymaniem powiadomienia lub powiadomienia, jak i po otrzymaniu powiadomienia. Wzorzec projektowania obserwatora nie dyktuje, czy dostawca lub obserwator jest odpowiedzialny za wypisanie subskrypcji; w związku z tym istnieje możliwość, że oba mogą próbować zrezygnować z subskrypcji. Zazwyczaj gdy obserwatorzy anulują subskrypcję, są usuwani z kolekcji subskrybentów. W aplikacji jednowątkowej <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji należy upewnić się, że odwołanie do obiektu jest prawidłowy i że obiekt jest członkiem kolekcji subskrybentów przed podjęciem próby usunięcia go. W aplikacji wielowątkowej należy użyć obiektu kolekcji bezpiecznego dla wątków, takiego jak <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> obiekt.  
  
### <a name="the-observer----implementing-the-onerror-method"></a>Obserwator - Implementacja OnError Metoda  
 Gdy obserwator otrzymuje powiadomienie o błędzie od dostawcy, obserwator powinien traktować wyjątek jako informacyjny i nie powinien być zobowiązany do podjęcia żadnych szczególnych działań.  
  
 Obserwator powinien postępować zgodnie z <xref:System.IObserver%601.OnError%2A> tymi najlepszymi rozwiązaniami podczas odpowiadania na wywołanie metody od dostawcy:  
  
- Obserwator nie powinien zgłaszać wyjątków od implementacji interfejsu, takich jak <xref:System.IObserver%601.OnNext%2A> lub <xref:System.IObserver%601.OnError%2A>. Jednak jeśli obserwator zgłasza wyjątki, należy oczekiwać, że te wyjątki, aby przejść nieobsługiwane.  
  
- Aby zachować stos wywołań, obserwator, który chce zgłosić <xref:System.Exception> obiekt, który został przekazany do jego <xref:System.IObserver%601.OnError%2A> metody należy zawinąć wyjątek przed jego zgłaszaniem. W tym celu należy użyć standardowego obiektu wyjątku.  
  
## <a name="additional-best-practices"></a>Dodatkowe najlepsze wskazówki  
 Próba wyrejestrowania <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> w metodzie może spowodować odwołanie null. Dlatego zaleca się, aby uniknąć tej praktyki.  
  
 Mimo że można dołączyć obserwatora do wielu dostawców, zalecany wzorzec jest dołączenie wystąpienia <xref:System.IObserver%601> tylko do jednego <xref:System.IObservable%601> wystąpienia.  
  
## <a name="see-also"></a>Zobacz też

- [Wzorzec projektowy obserwatora](../../../docs/standard/events/observer-design-pattern.md)
- [Instrukcje: Implementowanie obserwatora](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Instrukcje: Implementowanie dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md)
