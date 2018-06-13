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
ms.openlocfilehash: 3f9b18b3362155e256c922a84f3f1cdb6d255a4b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570981"
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>Decydowanie o czasie implementacji klienta wzorca asynchronicznego opartego na zdarzeniach
Asynchroniczny wzorzec oparty na zdarzeniach dostarczają wzorzec publikowania asynchroniczne zachowanie klasy. Wraz z wprowadzeniem strony tego wzorca [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] definiuje dwa wzorce asynchroniczne zachowanie publikowania: wzorzec asynchroniczny oparty na <xref:System.IAsyncResult?displayProperty=nameWithType> interfejsu i wzorzec oparty na zdarzeniach. W tym temacie opisano, gdy jest ona odpowiednia dla można zapewnić oba wzorce.  
  
 Aby uzyskać więcej informacji o programowanie asynchroniczne z <xref:System.IAsyncResult> interfejsu, zobacz [oparty na zdarzeniach asynchroniczny wzorzec (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).  
  
## <a name="general-principles"></a>Zasady ogólne  
 Ogólnie rzecz biorąc powinny ujawniać funkcji asynchronicznych za pomocą opartego na zdarzeniach wzorca asynchronicznego zawsze, gdy jest to możliwe. Istnieją jednak niektóre wymagania, które nie spełniają wzorzec oparty na zdarzeniach. W takich przypadkach może być konieczne wdrożenie <xref:System.IAsyncResult> wzorzec oprócz wzorzec oparty na zdarzeniach.  
  
> [!NOTE]
>  Rzadko <xref:System.IAsyncResult> wzorzec do zaimplementowania bez wzorzec oparty na zdarzeniach, również implementowana.  
  
## <a name="guidelines"></a>Wytyczne dotyczące  
 Na poniższej liście opisano wskazówki dotyczące po powinien implementować wzorzec asynchroniczny oparty na zdarzeniach:  
  
-   Użyj wzorzec oparty na zdarzeniach jako domyślnego interfejsu API do udostępnienia asynchroniczne zachowanie dla klasy.  
  
-   Nie ujawniaj <xref:System.IAsyncResult> wzorca po klasie służy głównie w aplikacji klienckiej, na przykład formularze systemu Windows.  
  
-   Udostępniają tylko <xref:System.IAsyncResult> wzorca, gdy jest to niezbędne do zaspokojenia wymagań. Na przykład zgodność z istniejącą interfejsu API może wymagać ujawnia <xref:System.IAsyncResult> wzorca.  
  
-   Nie ujawniaj <xref:System.IAsyncResult> wzorzec bez również udostępnianie wzorzec oparty na zdarzeniach.  
  
-   Jeśli musi ujawniać <xref:System.IAsyncResult> wzorca, zrobić jako zaawansowana opcja. Na przykład, jeśli użytkownik generuje obiekt serwera proxy, generowanie wzorzec oparty na zdarzeniach domyślnie z opcją Generowanie <xref:System.IAsyncResult> wzorca.  
  
-   Tworzenie implementacji wzorca oparty na zdarzeniach na Twojej <xref:System.IAsyncResult> implementacji wzorca.  
  
-   Unikaj udostępnianie wzorzec oparty na zdarzeniach i <xref:System.IAsyncResult> wzorzec na tej samej klasy. Udostępnianie wzorzec oparty na zdarzeniach na klasach "wyższy poziom" i <xref:System.IAsyncResult> wzorca na "obniżyć poziom" klasy. Na przykład porównać wzorzec oparty na zdarzeniach na <xref:System.Net.WebClient> składnik o <xref:System.IAsyncResult> wzorca na <xref:System.Web.HttpRequest> klasy.  
  
    -   Udostępnianie wzorzec oparty na zdarzeniach i <xref:System.IAsyncResult> wzorzec na tej samej klasy, gdy wymaga zgodności. Na przykład, jeśli już zostały wydane interfejs API, który używa <xref:System.IAsyncResult> wzorzec, należy zachować <xref:System.IAsyncResult> wzorca dla zgodności z poprzednimi wersjami.  
  
    -   Udostępnianie wzorzec oparty na zdarzeniach i <xref:System.IAsyncResult> wzorca w tej samej klasy, jeśli zaletą oddzielanie implementacje przeważa nad wynikowy złożoności modelu obiektu. Warto udostępnić oba wzorce dotyczących jednej klasy niż Aby uniknąć udostępnianie wzorzec oparty na zdarzeniach.  
  
    -   Jeśli musi ujawniać wzorzec oparty na zdarzeniach i <xref:System.IAsyncResult> wzorzec na jedną klasę, użyj <xref:System.ComponentModel.EditorBrowsableAttribute> ustawioną <xref:System.ComponentModel.EditorBrowsableState.Advanced> do oznaczania <xref:System.IAsyncResult> implementacji wzorca jako funkcja zaawansowana. Wskazuje środowisk projektowania, takie jak Visual Studio IntelliSense, aby nie wyświetlać <xref:System.IAsyncResult> właściwości i metody. Te właściwości i metody są nadal pełni użyteczne, ale używająca za pomocą funkcji IntelliSense ma jaśniejszy widoku interfejsu API.  
  
## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>Kryteria udostępnianie wzorzec IAsyncResult oprócz wzorzec oparty na zdarzeniach  
 Podczas wzorca asynchronicznego opartego na zdarzeniach ma wiele zalet w scenariuszach wcześniej wspomniano, ma kilka wad, które należy zwrócić uwagę w przypadku wydajność najważniejszych wymagań.  
  
 Istnieją trzy scenariusze, które nie dotyczą wzorzec oparty na zdarzeniach, jak również <xref:System.IAsyncResult> wzorca:  
  
-   Blokowanie oczekiwania na jednym <xref:System.IAsyncResult>  
  
-   Blokowanie oczekiwanie na wiele <xref:System.IAsyncResult> obiektów  
  
-   Sondowanie ukończenia na <xref:System.IAsyncResult>  
  
 Te scenariusze można rozwiązać przy użyciu wzorca oparty na zdarzeniach, ale jest bardziej skomplikowane niż użycie <xref:System.IAsyncResult> wzorca.  
  
 Deweloperzy często używają <xref:System.IAsyncResult> wzorca dla usług, które zwykle mają wymagania bardzo wysokiej wydajności. Na przykład sondowania dla scenariusza ukończenia to technika wysokiej wydajności serwera.  
  
 Ponadto wzorzec oparty na zdarzeniach jest mniej wydajne niż <xref:System.IAsyncResult> wzorca, ponieważ tworzy on więcej obiektów, szczególnie <xref:System.EventArgs>, i dlatego synchronizacji między wątkami.  
  
 Na poniższej liście przedstawiono kilka zaleceń, które należy wykonać, jeśli zdecydujesz się używać <xref:System.IAsyncResult> wzorca:  
  
-   Udostępniają tylko <xref:System.IAsyncResult> wzorca w szczególności integralność obsługę <xref:System.Threading.WaitHandle> lub <xref:System.IAsyncResult> obiektów.  
  
-   Udostępniają tylko <xref:System.IAsyncResult> wzorca, jeśli masz istniejące interfejsu API, który używa <xref:System.IAsyncResult> wzorca.  
  
-   Jeśli masz istniejące interfejsu API na podstawie <xref:System.IAsyncResult> wzorca, należy rozważyć również udostępnianie wzorzec oparty na zdarzeniach w Twojej następnej wersji.  
  
-   Udostępniają tylko <xref:System.IAsyncResult> wzorzec, jeśli masz wymagania wysokiej wydajności, które upewnieniu się, nie może spełnić wzorzec oparty na zdarzeniach, ale można spełnić przez <xref:System.IAsyncResult> wzorca.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [Programowanie wielowątkowości za pomocą wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Implementowanie wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 [Implementacja wzorca asynchronicznego opartego na zdarzeniach — najlepsze rozwiązania](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [Asynchroniczny wzorzec oparty na zdarzeniach — omówienie](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
