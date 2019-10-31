---
title: Wzorzec projektowy obserwatora — Najlepsze praktyki
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- observer design pattern [.NET Framework], best practices
- best practices [.NET Framework], observer design pattern
ms.assetid: c834760f-ddd4-417f-abb7-a059679d5b8c
ms.openlocfilehash: 2da29e0baf429142707d0ddd39b1a11c13a17a90
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141540"
---
# <a name="observer-design-pattern-best-practices"></a>Wzorzec projektowy obserwatora — Najlepsze praktyki
W .NET Framework Wzorzec projektowy obserwatora jest implementowany jako zestaw interfejsów. Interfejs <xref:System.IObservable%601?displayProperty=nameWithType> reprezentuje dostawcę danych, który jest również odpowiedzialny za dostarczanie <xref:System.IDisposable> implementacji, która umożliwia obserwatorom anulowanie subskrypcji powiadomień. Interfejs <xref:System.IObserver%601?displayProperty=nameWithType> reprezentuje obserwatora. W tym temacie opisano najlepsze rozwiązania, które deweloperzy powinni wykonać podczas wdrażania wzorca projektowego obserwatora przy użyciu tych interfejsów.  
  
## <a name="threading"></a>Wątkowość  
 Zazwyczaj dostawca implementuje metodę <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> poprzez dodanie określonego obserwatora do listy subskrybentów reprezentowanej przez jakiś obiekt kolekcji i implementuje metodę <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> przez usunięcie określonego obserwatora z listy subskrybentów. Obserwator może wywoływać te metody w dowolnym momencie. Ponadto, ponieważ kontrakt dostawcy/obserwatora nie określa, kto jest odpowiedzialny za anulowanie subskrypcji po metodzie wywołania zwrotnego <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, dostawca i obserwator mogą próbować usunąć ten sam element członkowski z listy. Ze względu na tę możliwość obie metody <xref:System.IObservable%601.Subscribe%2A> i <xref:System.IDisposable.Dispose%2A> powinny być bezpieczne wątkowo. Zazwyczaj obejmuje to użycie [współbieżnej kolekcji](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md) lub blokady. Implementacje, które nie są bezpieczne dla wątków, powinny jawnie udokumentować, że nie są.  
  
 Wszelkie dodatkowe gwarancje muszą być określone w warstwie na górze dostawcy/kontraktu obserwatora. Implementacje powinny jasno wywoływać się, gdy nakładają dodatkowe wymagania, aby uniknąć nieporozumień przez użytkownika na temat kontraktu obserwatora.  
  
## <a name="handling-exceptions"></a>Obsługa wyjątków  
 Ze względu na luźny sprzężenie między dostawcą danych a obserwatorem, wyjątki we wzorcu projektowym obserwatora mają być informacyjne. Ma to wpływ na to, jak dostawcy i obserwatorzy obsługują wyjątki we wzorcu projektowym obserwatora.  
  
### <a name="the-provider----calling-the-onerror-method"></a>Dostawca — wywoływanie metody OnError  
 Metoda <xref:System.IObserver%601.OnError%2A> jest przeznaczona jako komunikat informacyjny dla obserwatorów, podobnie jak w przypadku metody <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>. Jednak Metoda <xref:System.IObserver%601.OnNext%2A> została zaprojektowana w celu zapewnienia obserwatora z aktualnymi lub zaktualizowanymi danymi, podczas gdy metoda <xref:System.IObserver%601.OnError%2A> została zaprojektowana tak, aby wskazywała, że dostawca nie jest w stanie dostarczyć prawidłowych danych.  
  
 Dostawca powinien przestrzegać następujących najlepszych rozwiązań w przypadku obsługi wyjątków i wywoływania metody <xref:System.IObserver%601.OnError%2A>:  
  
- Dostawca musi obsługiwać własne wyjątki, jeśli ma określone wymagania.  
  
- Dostawca nie powinien oczekiwać lub wymagać, aby obserwatorzy obsługują wyjątki w określony sposób.  
  
- Dostawca powinien wywołać metodę <xref:System.IObserver%601.OnError%2A>, gdy obsługuje wyjątek, który narusza jego zdolność do dostarczania aktualizacji. Informacje o takich wyjątkach mogą być przesyłane do obserwatora. W innych przypadkach nie trzeba powiadamiać obserwatorów o wyjątku.  
  
 Gdy dostawca wywoła metodę <xref:System.IObserver%601.OnError%2A> lub <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, nie powinno być żadnych dalszych powiadomień i dostawca może anulować subskrypcję obserwatorów. Jednakże obserwatorzy mogą również anulować subskrypcję w dowolnym momencie, w tym zarówno przed, jak i po otrzymaniu powiadomienia o <xref:System.IObserver%601.OnError%2A> lub <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>. Wzorzec projektowy obserwatora nie określa, czy dostawca lub obserwator jest odpowiedzialny za anulowanie subskrypcji; w związku z tym istnieje możliwość, że obie metody mogą próbować anulować subskrypcję. Zwykle gdy obserwatorzy nie subskrybują subskrypcji, zostaną usunięci z kolekcji Subskrybenci. W aplikacji jednowątkowej implementacja <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> powinna upewnić się, że odwołanie do obiektu jest prawidłowe i że obiekt jest członkiem kolekcji Subskrybenci, zanim spróbuje ją usunąć. W aplikacji wielowątkowej należy użyć obiektu do zbierania danych bezpiecznych dla wątków, takiego jak obiekt <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.  
  
### <a name="the-observer----implementing-the-onerror-method"></a>Obserwator — implementowanie metody OnError  
 Gdy obserwator otrzymuje powiadomienie o błędzie od dostawcy, obserwator powinien traktować wyjątek jako informacyjny i nie powinien być wymagany do podjęcia jakichkolwiek działań.  
  
 Obserwator powinien postępować zgodnie z następującymi najlepszymi rozwiązaniami w przypadku odpowiedzi na wywołanie metody <xref:System.IObserver%601.OnError%2A> od dostawcy:  
  
- Obserwator nie powinien zgłaszać wyjątków od implementacji interfejsu, takich jak <xref:System.IObserver%601.OnNext%2A> lub <xref:System.IObserver%601.OnError%2A>. Jeśli jednak obserwator zgłosi wyjątki, powinien oczekiwać, że te wyjątki nie są obsługiwane.  
  
- Aby zachować stos wywołań, obserwator, który chce zgłosić obiekt <xref:System.Exception>, który został przesłany do jego metody <xref:System.IObserver%601.OnError%2A>, powinien otoczyć wyjątek przed jego wygenerowaniem. W tym celu należy użyć obiektu standardowego wyjątku.  
  
## <a name="additional-best-practices"></a>Dodatkowe najlepsze rozwiązania  
 Próba wyrejestrowania w metodzie <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> może spowodować odwołanie do wartości null. Dlatego zalecamy uniknięcie tego postępowania.  
  
 Chociaż istnieje możliwość dołączenia obserwatora do wielu dostawców, zalecany wzorzec polega na dołączeniu wystąpienia <xref:System.IObserver%601> tylko do jednego wystąpienia <xref:System.IObservable%601>.  
  
## <a name="see-also"></a>Zobacz także

- [Wzorzec projektowy obserwatora](../../../docs/standard/events/observer-design-pattern.md)
- [Instrukcje: Implementowanie obserwatora](../../../docs/standard/events/how-to-implement-an-observer.md)
- [Instrukcje: Implementowanie dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md)
