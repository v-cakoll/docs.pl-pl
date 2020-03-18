---
title: Decydowanie o czasie implementacji klienta wzorca asynchronicznego opartego na zdarzeniach
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
ms.openlocfilehash: 5fca32953af91184fe99d8ef6afe5a2374f325d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67663717"
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>Decydowanie o czasie implementacji klienta wzorca asynchronicznego opartego na zdarzeniach

Wzorzec asynchroniczny oparty na zdarzeniach udostępnia wzorzec do ujawniania asynchronicznego zachowania klasy. Wraz z wprowadzeniem tego wzorca .NET Framework definiuje dwa wzorce do ujawniania zachowania asynchronicznego: wzorzec asynchroniczny oparty na <xref:System.IAsyncResult?displayProperty=nameWithType> interfejsie i wzorzec oparty na zdarzeniach. W tym temacie opisano, kiedy jest odpowiedni do zaimplementowania obu wzorców.

Aby uzyskać więcej informacji na temat <xref:System.IAsyncResult> programowania asynchronicznego z interfejsem, zobacz [Asynchroniczny model programowania (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).

## <a name="general-principles"></a>Zasady ogólne

Ogólnie rzecz biorąc należy udostępnić funkcje asynchroniczne przy użyciu wzorca asynchronicznego opartego na zdarzeniach, gdy jest to możliwe. Istnieją jednak pewne wymagania, których wzorzec oparty na zdarzeniach nie może spełnić. W takich przypadkach może być <xref:System.IAsyncResult> konieczne zaimplementowanie wzorca oprócz wzorca opartego na zdarzeniach.

> [!NOTE]
> Rzadko jest dla <xref:System.IAsyncResult> wzorca, które mają być implementowane bez wzorca opartego na zdarzeniach również są implementowane.

## <a name="guidelines"></a>Wytyczne

Na poniższej liście opisano wskazówki dotyczące tego, kiedy należy zaimplementować wzorzec asynchroniczny oparty na zdarzeniach:

- Użyj wzorca opartego na zdarzeniach jako domyślnego interfejsu API, aby udostępnić zachowanie asynchroniczne dla twojej klasy.

- Nie uwidaczniawyszy <xref:System.IAsyncResult> wzorzec, gdy klasa jest używana głównie w aplikacji klienckiej, na przykład formularze systemu Windows.

- Tylko uwidaczniawywywek <xref:System.IAsyncResult> tylko wtedy, gdy jest to konieczne do spełnienia wymagań. Na przykład zgodność z istniejącym interfejsem API może wymagać udostępnienia wzorca. <xref:System.IAsyncResult>

- Nie należy <xref:System.IAsyncResult> ujawniać wzorzec bez również odsłaniając wzorzec oparty na zdarzeniach.

- Jeśli musisz udostępnić <xref:System.IAsyncResult> wzorzec, zrób to jako opcja zaawansowana. Na przykład jeśli zostanie wygenerowany obiekt proxy, należy domyślnie wygenerować wzorzec oparty na zdarzeniach z opcją wygenerowania wzorca. <xref:System.IAsyncResult>

- Skompiluj implementację <xref:System.IAsyncResult> wzorca opartego na zdarzeniach na implementacji wzorca.

- Należy unikać ujawniania zarówno wzorca <xref:System.IAsyncResult> opartego na zdarzeniach, jak i wzorca w tej samej klasie. Uwidaczniawy wzorzec <xref:System.IAsyncResult> oparty na zdarzeniach na klasach "wyższego poziomu" i wzorzec na klasach "niższego poziomu". Na przykład porównaj wzorzec <xref:System.Net.WebClient> oparty <xref:System.IAsyncResult> na zdarzeniu na składniku ze szykiem na <xref:System.Web.HttpRequest> klasie.

  - Uwidacz nia <xref:System.IAsyncResult> wzorca opartego na zdarzeniach i wzorzec w tej samej klasie, gdy wymaga tego zgodność. Na przykład jeśli już zwolniono interfejs API, który używa wzorca, <xref:System.IAsyncResult> należy zachować <xref:System.IAsyncResult> wzorzec dla zgodności z poprzednimi wersjami.

  - Uwidaczniaszy <xref:System.IAsyncResult> wzorzec oparty na zdarzeniach i wzorzec w tej samej klasie, jeśli wynikowa złożoność modelu obiektu przeważa nad korzyścią z oddzielenia implementacji. Lepiej jest udostępnić oba wzorce na jednej klasy, niż uniknąć ujawniania wzorca opartego na zdarzeniach.

  - Jeśli należy udostępnić zarówno wzorzec oparty na zdarzeniach, jak <xref:System.IAsyncResult> i wzorzec w jednej klasie, należy użyć <xref:System.ComponentModel.EditorBrowsableAttribute> zestawu do <xref:System.ComponentModel.EditorBrowsableState.Advanced> oznaczenia implementacji <xref:System.IAsyncResult> wzorca jako zaawansowanej funkcji. Oznacza to, że środowiska projektowe, takie jak Visual <xref:System.IAsyncResult> Studio IntelliSense, nie wyświetlają właściwości i metod. Te właściwości i metody są nadal w pełni użyteczne, ale deweloper pracujący za pośrednictwem IntelliSense ma jaśniejszy widok interfejsu API.

## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>Kryteria dotyczące uwzidłania wzorca Wyniku IAsync w uzupełnieniu do wzorca opartego na zdarzeniach

Podczas gdy wzorzec asynchroniczny oparty na zdarzeniach ma wiele korzyści w ramach wcześniej wymienionych scenariuszy, ma pewne wady, o których należy pamiętać, jeśli wydajność jest najważniejszym wymaganiem.

Istnieją trzy scenariusze, które wzorzec oparty na <xref:System.IAsyncResult> zdarzeniach nie odnosi się, jak również wzorzec:

- Blokowanie oczekiwania na jednym<xref:System.IAsyncResult>

- Blokowanie oczekiwania <xref:System.IAsyncResult> na wiele obiektów

- Sondowanie do zakończenia<xref:System.IAsyncResult>

Można rozwiązać te scenariusze przy użyciu wzorca opartego na zdarzeniach, <xref:System.IAsyncResult> ale w ten sposób jest bardziej kłopotliwe niż przy użyciu wzorca.

Deweloperzy często <xref:System.IAsyncResult> używają wzorca dla usług, które zazwyczaj mają bardzo wysokie wymagania dotyczące wydajności. Na przykład sondowanie dla scenariusza ukończenia jest techniką serwera o wysokiej wydajności.

Ponadto wzorzec oparty na zdarzeniach <xref:System.IAsyncResult> jest mniej wydajny niż <xref:System.EventArgs>wzorzec, ponieważ tworzy więcej obiektów, szczególnie , a ponieważ synchronizuje między wątkami.

Na poniższej liście przedstawiono kilka zaleceń <xref:System.IAsyncResult> do naśladowania, jeśli zdecydujesz się użyć wzorca:

- Tylko uwidaczniaszy <xref:System.IAsyncResult> wzorzec, gdy w szczególności wymagają obsługi <xref:System.Threading.WaitHandle> lub <xref:System.IAsyncResult> obiektów.

- Tylko uwidaczniaszy <xref:System.IAsyncResult> wzorzec, gdy masz istniejący interfejs API, który używa wzorca. <xref:System.IAsyncResult>

- Jeśli masz istniejący interfejs API oparty na wzorcu, <xref:System.IAsyncResult> należy również rozważyć ujawnienie wzorca opartego na zdarzeniach w następnej wersji.

- Tylko <xref:System.IAsyncResult> uwidaczniać wzorzec, jeśli masz wymagania wysokiej wydajności, które <xref:System.IAsyncResult> zostały zweryfikowane nie mogą być spełnione przez wzorzec oparty na zdarzeniach, ale mogą być spełnione przez wzorzec.

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
- [Implementowanie wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)
- [Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — przegląd](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
