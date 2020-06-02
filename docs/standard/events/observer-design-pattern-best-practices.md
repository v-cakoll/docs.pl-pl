---
title: Wzorzec projektowy obserwatora — Najlepsze praktyki
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- observer design pattern [.NET Framework], best practices
- best practices [.NET Framework], observer design pattern
ms.assetid: c834760f-ddd4-417f-abb7-a059679d5b8c
ms.openlocfilehash: b4f8e568dcb6790dac1dc8fc5c969d6fa1367c4e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288462"
---
# <a name="observer-design-pattern-best-practices"></a>Wzorzec projektowy obserwatora — Najlepsze praktyki
W .NET Framework Wzorzec projektowy obserwatora jest implementowany jako zestaw interfejsów. <xref:System.IObservable%601?displayProperty=nameWithType>Interfejs reprezentuje dostawcę danych, który jest również odpowiedzialny za dostarczanie <xref:System.IDisposable> implementacji, która umożliwia obserwatorom anulowanie subskrypcji powiadomień. <xref:System.IObserver%601?displayProperty=nameWithType>Interfejs reprezentuje obserwatora. W tym temacie opisano najlepsze rozwiązania, które deweloperzy powinni wykonać podczas wdrażania wzorca projektowego obserwatora przy użyciu tych interfejsów.  
  
## <a name="threading"></a>Wątkowość  
 Zazwyczaj dostawca implementuje <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metodę przez dodanie określonego obserwatora do listy subskrybentów reprezentowanej przez jakiś obiekt kolekcji i implementuje <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metodę przez usunięcie określonego obserwatora z listy subskrybentów. Obserwator może wywoływać te metody w dowolnym momencie. Ponadto, ponieważ umowa dostawcy/obserwatora nie określa, kto jest odpowiedzialny za anulowanie subskrypcji po <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> metodzie wywołania zwrotnego, dostawca i obserwator mogą próbować usunąć ten sam element członkowski z listy. Ze względu na tę możliwość obie <xref:System.IObservable%601.Subscribe%2A> <xref:System.IDisposable.Dispose%2A> metody i powinny być bezpieczne wątkowo. Zazwyczaj obejmuje to użycie [współbieżnej kolekcji](../parallel-programming/data-structures-for-parallel-programming.md) lub blokady. Implementacje, które nie są bezpieczne dla wątków, powinny jawnie udokumentować, że nie są.  
  
 Wszelkie dodatkowe gwarancje muszą być określone w warstwie na górze dostawcy/kontraktu obserwatora. Implementacje powinny jasno wywoływać się, gdy nakładają dodatkowe wymagania, aby uniknąć nieporozumień przez użytkownika na temat kontraktu obserwatora.  
  
## <a name="handling-exceptions"></a>Obsługa wyjątków  
 Ze względu na luźny sprzężenie między dostawcą danych a obserwatorem, wyjątki we wzorcu projektowym obserwatora mają być informacyjne. Ma to wpływ na to, jak dostawcy i obserwatorzy obsługują wyjątki we wzorcu projektowym obserwatora.  
  
### <a name="the-provider----calling-the-onerror-method"></a>Dostawca — wywoływanie metody OnError  
 <xref:System.IObserver%601.OnError%2A>Metoda jest przeznaczona jako komunikat informacyjny dla obserwatorów, podobnie jak <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType> Metoda. Jednakże <xref:System.IObserver%601.OnNext%2A> Metoda została zaprojektowana w celu zapewnienia obserwatora z aktualnymi lub zaktualizowanymi danymi, podczas gdy <xref:System.IObserver%601.OnError%2A> Metoda jest zaprojektowana w celu wskazania, że dostawca nie jest w stanie dostarczyć prawidłowych danych.  
  
 Dostawca powinien przestrzegać tych najlepszych rozwiązań w przypadku obsługi wyjątków i wywoływania <xref:System.IObserver%601.OnError%2A> metody:  
  
- Dostawca musi obsługiwać własne wyjątki, jeśli ma określone wymagania.  
  
- Dostawca nie powinien oczekiwać lub wymagać, aby obserwatorzy obsługują wyjątki w określony sposób.  
  
- Dostawca powinien wywołać metodę, <xref:System.IObserver%601.OnError%2A> gdy obsługuje wyjątek, który narusza jego zdolność do udostępnienia aktualizacji. Informacje o takich wyjątkach mogą być przesyłane do obserwatora. W innych przypadkach nie trzeba powiadamiać obserwatorów o wyjątku.  
  
 Gdy dostawca wywoła <xref:System.IObserver%601.OnError%2A> <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> metodę lub, nie powinno być żadnych dalszych powiadomień i dostawca może anulować subskrypcję obserwatorów. Jednakże obserwatorzy mogą również anulować subskrypcję w dowolnym momencie, w tym zarówno przed, jak i po otrzymaniu <xref:System.IObserver%601.OnError%2A> <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType> powiadomienia. Wzorzec projektowy obserwatora nie określa, czy dostawca lub obserwator jest odpowiedzialny za anulowanie subskrypcji; w związku z tym istnieje możliwość, że obie metody mogą próbować anulować subskrypcję. Zwykle gdy obserwatorzy nie subskrybują subskrypcji, zostaną usunięci z kolekcji Subskrybenci. W aplikacji jednowątkowej <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacja powinna upewnić się, że odwołanie do obiektu jest prawidłowe i że obiekt jest członkiem kolekcji Subskrybenci przed podjęciem próby jego usunięcia. W aplikacji wielowątkowej należy użyć obiektu do zbierania danych bezpiecznych dla wątków, takiego jak <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> obiekt.  
  
### <a name="the-observer----implementing-the-onerror-method"></a>Obserwator — implementowanie metody OnError  
 Gdy obserwator otrzymuje powiadomienie o błędzie od dostawcy, obserwator powinien traktować wyjątek jako informacyjny i nie powinien być wymagany do podjęcia jakichkolwiek działań.  
  
 Obserwator powinien postępować zgodnie z najlepszymi rozwiązaniami w przypadku odpowiedzi na <xref:System.IObserver%601.OnError%2A> wywołanie metody od dostawcy:  
  
- Obserwator nie powinien zgłaszać wyjątków od implementacji interfejsu, takich jak <xref:System.IObserver%601.OnNext%2A> lub <xref:System.IObserver%601.OnError%2A> . Jeśli jednak obserwator zgłosi wyjątki, powinien oczekiwać, że te wyjątki nie są obsługiwane.  
  
- Aby zachować stos wywołań, obserwator, który chce zgłosić <xref:System.Exception> obiekt, który został przesłany do jego metody, <xref:System.IObserver%601.OnError%2A> powinien otoczyć wyjątek przed jego wygenerowaniem. W tym celu należy użyć obiektu standardowego wyjątku.  
  
## <a name="additional-best-practices"></a>Dodatkowe najlepsze rozwiązania  
 Próba wyrejestrowania w <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> metodzie może spowodować odwołanie o wartości null. Dlatego zalecamy uniknięcie tego postępowania.  
  
 Chociaż istnieje możliwość dołączenia obserwatora do wielu dostawców, zalecany wzorzec polega na dołączeniu <xref:System.IObserver%601> wystąpienia tylko do jednego <xref:System.IObservable%601> wystąpienia.  
  
## <a name="see-also"></a>Zobacz także

- [Wzorzec projektowy obserwatora](observer-design-pattern.md)
- [Instrukcje: implementowanie obserwatora](how-to-implement-an-observer.md)
- [Instrukcje: implementowanie dostawcy](how-to-implement-a-provider.md)
