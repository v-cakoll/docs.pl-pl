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
ms.openlocfilehash: af30f0d09ce772f20f342ec0936d0ca63f5465d7
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45750274"
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>Decydowanie o czasie implementacji klienta wzorca asynchronicznego opartego na zdarzeniach
Asynchroniczny wzorzec oparty na zdarzeniach dostarczają wzorzec publikowania zachowanie asynchroniczne klasy. Wraz z wprowadzeniem tego wzorca [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] definiuje dwa wzorce do udostępniania zachowanie asynchroniczne: asynchroniczny wzorzec oparty na <xref:System.IAsyncResult?displayProperty=nameWithType> interfejsu i wzorzec oparty na zdarzeniach. W tym temacie opisano, gdy jest ona odpowiednia dla można zaimplementować obu wzorców.  
  
 Aby uzyskać więcej informacji na temat programowania asynchronicznego przy użyciu <xref:System.IAsyncResult> interfejsu, zobacz [modelu programowania asynchronicznego (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).  
  
## <a name="general-principles"></a>Zasady ogólne  
 Ogólnie rzecz biorąc należy udostępnić funkcje asynchroniczne przy użyciu opartego na zdarzeniach wzorca asynchronicznego zawsze, gdy jest to możliwe. Istnieją jednak pewne wymagania, które nie spełniają wzorzec oparty na zdarzeniach. W takich przypadkach użytkownik może być konieczne wdrożenie <xref:System.IAsyncResult> wzorzec oprócz wzorzec oparty na zdarzeniach.  
  
> [!NOTE]
>  Rzadko <xref:System.IAsyncResult> wzorzec do zaimplementowania bez wzorzec oparty na zdarzeniach, również implementowany.  
  
## <a name="guidelines"></a>Wytyczne dotyczące  
 Na poniższej liście opisano wytyczne podczas należy zaimplementować wzorzec asynchroniczny oparty na zdarzeniach:  
  
-   Użyj wzorca opartego na zdarzeniach jako domyślny interfejs API do udostępnienia asynchronicznego zachowanie dla swojej klasy.  
  
-   Nie ujawniaj <xref:System.IAsyncResult> wzorca, gdy klasa jest używany głównie w aplikacji klienckiej, na przykład Windows Forms.  
  
-   Tylko udostępnianie <xref:System.IAsyncResult> wzorca, gdy konieczne jest spełnienie wymagań. Na przykład, zgodność z istniejącym interfejsem API mogą wymagać do udostępnienia <xref:System.IAsyncResult> wzorca.  
  
-   Nie ujawniaj <xref:System.IAsyncResult> wzorzec bez narażania również wzorzec oparty na zdarzeniach.  
  
-   Jeśli musisz ujawnić <xref:System.IAsyncResult> wzorca, w tym celu jako zaawansowana opcja. Na przykład, jeśli użytkownik generuje obiekt serwera proxy, generowanie wzorzec oparty na zdarzeniach domyślnie z opcją do generowania <xref:System.IAsyncResult> wzorca.  
  
-   Tworzenie implementacji wzorca opartego na zdarzeniach w swojej <xref:System.IAsyncResult> implementacji wzorca.  
  
-   Należy unikać udostępnianie wzorzec oparty na zdarzeniach i <xref:System.IAsyncResult> wzorca na tej samej klasy. Udostępnić wzorzec oparty na zdarzeniach w klasach "na wyższym poziomie" i <xref:System.IAsyncResult> wzorca na "obniżyć poziom" klasy. Na przykład porównać wzorzec oparty na zdarzeniach na <xref:System.Net.WebClient> składnika za pomocą <xref:System.IAsyncResult> wzorca na <xref:System.Web.HttpRequest> klasy.  
  
    -   Udostępnić wzorzec oparty na zdarzeniach i <xref:System.IAsyncResult> wzorca na tej samej klasy, gdy wymaga zgodności. Na przykład, jeśli już zostały wydane interfejsu API, który używa <xref:System.IAsyncResult> wzorzec, należy zachować <xref:System.IAsyncResult> wzorca dla zgodności z poprzednimi wersjami.  
  
    -   Udostępnić wzorzec oparty na zdarzeniach i <xref:System.IAsyncResult> wzorca na tej samej klasy, jeśli wynikowy złożoność modelu obiektu przewyższa korzyści oddzielenie implementacji. Zaleca się uwidocznić obu wzorców dotyczących jednej klasy niż Aby uniknąć ujawnienia wzorzec oparty na zdarzeniach.  
  
    -   Jeśli musisz ujawnić wzorzec oparty na zdarzeniach i <xref:System.IAsyncResult> wzorzec dotyczących jednej klasy, użyj <xref:System.ComponentModel.EditorBrowsableAttribute> równa <xref:System.ComponentModel.EditorBrowsableState.Advanced> do oznaczania <xref:System.IAsyncResult> implementacji wzorca jako funkcja zaawansowana. Oznacza to, aby środowiska projektowe, takie jak Visual Studio technologii IntelliSense, aby nie wyświetlać <xref:System.IAsyncResult> właściwości i metody. Te właściwości i metody są nadal w pełni użyteczne, ale Deweloper pracy za pomocą funkcji IntelliSense zawiera bardziej zrozumiały widok interfejsu API.  
  
## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>Kryteria udostępnianie wzorzec IAsyncResult oprócz wzorzec oparty na zdarzeniach  
 Gdy wzorzec asynchroniczny oparty na zdarzeniach ma wiele zalet w scenariuszach wymienionych wcześniej, ma pewne wady, które powinny być świadome Jeśli wydajność jest z najważniejszych wymagań.  
  
 Istnieją trzy scenariusze, w których nie opisano kwestii wzorzec oparty na zdarzeniach, jak również <xref:System.IAsyncResult> wzorca:  
  
-   Poczekaj na jednym blokowania <xref:System.IAsyncResult>  
  
-   Blokowanie oczekiwania na wielu <xref:System.IAsyncResult> obiektów  
  
-   Sondowanie na ukończenie <xref:System.IAsyncResult>  
  
 Można scenariuszy za pomocą wzorca opartego na zdarzeniach, ale jest bardziej skomplikowane niż użycie <xref:System.IAsyncResult> wzorca.  
  
 Deweloperzy często używają <xref:System.IAsyncResult> wzorca dla usług, które zwykle mają wymagania bardzo wysokiej wydajności. Na przykład sondowania ukończenia scenariusza jest to technika o wysokiej wydajności serwera.  
  
 Ponadto jest mniej wydajne niż wzorzec oparty na zdarzeniach <xref:System.IAsyncResult> wzorca, ponieważ tworzy on więcej obiektów, szczególnie <xref:System.EventArgs>, a ponieważ synchronizuje między wątkami.  
  
 Na poniższej liście przedstawiono kilka zaleceń, które należy wykonać, jeśli użytkownik zdecyduje się użyć <xref:System.IAsyncResult> wzorca:  
  
-   Tylko udostępnianie <xref:System.IAsyncResult> wzorca, gdy potrzebujesz specjalnie obsługę <xref:System.Threading.WaitHandle> lub <xref:System.IAsyncResult> obiektów.  
  
-   Tylko udostępnianie <xref:System.IAsyncResult> wzorca, gdy masz istniejących interfejsów API, który używa <xref:System.IAsyncResult> wzorca.  
  
-   W przypadku istniejącego interfejsu API na podstawie <xref:System.IAsyncResult> wzorca, należy wziąć pod uwagę także udostępnianie wzorzec oparty na zdarzeniach w swojej następnej wersji.  
  
-   Tylko udostępnianie <xref:System.IAsyncResult> wzorca, jeśli masz wymagania o wysokiej wydajności, które upewnieniu się, nie mogą zostać spełnione przez wzorzec oparty na zdarzeniach, ale mogą zostać spełnione przez <xref:System.IAsyncResult> wzorca.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
- [Implementowanie wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
- [Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
- [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
