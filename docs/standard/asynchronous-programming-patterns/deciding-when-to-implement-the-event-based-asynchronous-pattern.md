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
ms.openlocfilehash: c235a838504889a105ef98df47f7373a145503da
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289450"
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>Decydowanie o czasie implementacji klienta wzorca asynchronicznego opartego na zdarzeniach

Wzorzec asynchroniczny oparty na zdarzeniach udostępnia wzorzec do ujawniania asynchronicznego zachowania klasy. Wraz z wprowadzeniem tego wzorca .NET Framework definiuje dwa wzorce na potrzeby ujawniania zachowań asynchronicznych: wzorzec asynchroniczny oparty na <xref:System.IAsyncResult?displayProperty=nameWithType> interfejsie oraz wzorzec oparty na zdarzeniach. W tym temacie opisano, kiedy jest to odpowiednie dla implementacji obu wzorców.

Aby uzyskać więcej informacji o programowaniu asynchronicznym z <xref:System.IAsyncResult> interfejsem, zobacz [asynchroniczny model programowania (APM)](asynchronous-programming-model-apm.md).

## <a name="general-principles"></a>Zasady ogólne

Ogólnie rzecz biorąc, należy uwidocznić funkcje asynchroniczne za pomocą wzorca asynchronicznego opartego na zdarzeniach, gdy jest to możliwe. Jednak istnieją pewne wymagania, których wzorzec oparty na zdarzeniach nie może spełnić. W takich przypadkach może być konieczne zaimplementowanie <xref:System.IAsyncResult> wzorca oprócz wzorca opartego na zdarzeniach.

> [!NOTE]
> Jest to rzadki, aby <xref:System.IAsyncResult> wzorzec był zaimplementowany bez implementacji wzorca opartego na zdarzeniach.

## <a name="guidelines"></a>Wytyczne

Na poniższej liście przedstawiono wskazówki dotyczące sytuacji, w których należy zaimplementować wzorzec asynchroniczny oparty na zdarzeniach:

- Użyj wzorca opartego na zdarzeniach jako domyślnego interfejsu API, aby uwidocznić zachowanie asynchroniczne dla klasy.

- Nie ujawniaj <xref:System.IAsyncResult> wzorca, gdy Klasa jest używana głównie w aplikacji klienckiej, na przykład Windows Forms.

- Uwidaczniaj <xref:System.IAsyncResult> wzorzec tylko wtedy, gdy jest to niezbędne do spełnienia wymagań. Na przykład zgodność z istniejącym interfejsem API może wymagać uwidocznienia <xref:System.IAsyncResult> wzorca.

- Nie ujawniaj <xref:System.IAsyncResult> wzorca bez również ujawniania wzorca opartego na zdarzeniach.

- Jeśli musisz uwidocznić <xref:System.IAsyncResult> wzorzec, zrób to jako zaawansowaną opcję. Na przykład, jeśli wygenerujesz obiekt proxy, wygeneruj domyślnie wzorzec oparty na zdarzeniach z opcją wygenerowania <xref:System.IAsyncResult> wzorca.

- Kompiluj implementację wzorca opartego na zdarzeniach w <xref:System.IAsyncResult> implementacji wzorca.

- Należy unikać ujawniania wzorca opartego na zdarzeniach i <xref:System.IAsyncResult> wzorca w tej samej klasie. Uwidocznić wzorzec oparty na zdarzeniach dla klas "wyższego poziomu" i <xref:System.IAsyncResult> wzorzec dla klas "niższego poziomu". Na przykład Porównaj wzorzec oparty na zdarzeniach w <xref:System.Net.WebClient> składniku ze <xref:System.IAsyncResult> wzorcem w <xref:System.Web.HttpRequest> klasie.

  - Uwidocznić wzorzec oparty na zdarzeniach i <xref:System.IAsyncResult> wzorzec dla tej samej klasy, gdy wymaga tego zgodności. Jeśli na przykład już wydano interfejs API, który używa <xref:System.IAsyncResult> wzorca, należy zachować <xref:System.IAsyncResult> wzorzec zgodności z poprzednimi wersjami.

  - Uwidocznij wzorzec oparty na zdarzeniach i <xref:System.IAsyncResult> wzorzec dla tej samej klasy, jeśli złożoność modelu obiektów powstała w efekcie przewagi korzyści wynikające z oddzielenia implementacji. Lepiej jest uwidocznić oba wzorce na pojedynczej klasie, aby uniknąć ujawniania wzorca opartego na zdarzeniach.

  - Jeśli musisz uwidocznić wzorzec oparty na zdarzeniach i <xref:System.IAsyncResult> wzorzec dla pojedynczej klasy, użyj opcji <xref:System.ComponentModel.EditorBrowsableAttribute> Ustaw, aby <xref:System.ComponentModel.EditorBrowsableState.Advanced> oznaczyć <xref:System.IAsyncResult> implementację wzorca jako funkcję zaawansowaną. Wskazuje to na środowiska projektowania, takie jak Visual Studio IntelliSense, nie wyświetla <xref:System.IAsyncResult> właściwości i metod. Te właściwości i metody są nadal w pełni użyteczne, ale deweloper pracujący za pomocą technologii IntelliSense ma wyraźniejszy widok interfejsu API.

## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>Kryteria udostępniania wzorca IAsyncResult oprócz wzorca opartego na zdarzeniach

Chociaż wzorzec asynchroniczny oparty na zdarzeniach ma wiele korzyści w ramach wyżej wymienionych scenariuszy, ma pewne wady, których należy wiedzieć, jeśli wydajność jest najważniejszym wymaganiem.

Istnieją trzy scenariusze, w których wzorzec oparty na zdarzeniach nie dotyczy i <xref:System.IAsyncResult> wzorca:

- Blokowanie oczekiwania na jeden<xref:System.IAsyncResult>

- Blokowanie oczekiwania na wiele <xref:System.IAsyncResult> obiektów

- Sondowanie w celu ukończenia<xref:System.IAsyncResult>

Te scenariusze można rozwiązać przy użyciu wzorca zdarzeń, ale robi to bardziej skomplikowany niż używanie <xref:System.IAsyncResult> wzorca.

Deweloperzy często używają <xref:System.IAsyncResult> wzorca dla usług, które zwykle mają bardzo wysokie wymagania dotyczące wydajności. Na przykład scenariusz sondowania dla ukończenia jest techniką serwera o wysokiej wydajności.

Ponadto wzorzec oparty na zdarzeniach jest mniej wydajny niż <xref:System.IAsyncResult> wzorzec, ponieważ tworzy więcej obiektów, szczególnie <xref:System.EventArgs> i ponieważ synchronizuje się między wątkami.

Na poniższej liście przedstawiono zalecenia, które należy wykonać, jeśli zdecydujesz się użyć <xref:System.IAsyncResult> wzorca:

- Uwidocznić <xref:System.IAsyncResult> wzorzec tylko wtedy, gdy użytkownik wymaga obsługi <xref:System.Threading.WaitHandle> <xref:System.IAsyncResult> obiektów lub.

- Uwidaczniaj <xref:System.IAsyncResult> wzorzec tylko wtedy, gdy masz istniejący interfejs API, który używa <xref:System.IAsyncResult> wzorca.

- Jeśli masz istniejący interfejs API oparty na <xref:System.IAsyncResult> wzorcu, rozważ także udostępnienie wzorca opartego na zdarzeniach w następnej wersji.

- Uwidaczniaj tylko <xref:System.IAsyncResult> wzorzec, jeśli masz wymagania o wysokiej wydajności, które nie mogą być spełnione przez wzorzec oparty na zdarzeniach, ale mogą być spełnione przez wzorzec <xref:System.IAsyncResult> .

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](component-that-supports-the-event-based-asynchronous-pattern.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](event-based-asynchronous-pattern-eap.md)
- [Implementowanie wzorca asynchronicznego opartego na zdarzeniach](implementing-the-event-based-asynchronous-pattern.md)
- [Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach — przegląd](event-based-asynchronous-pattern-overview.md)
