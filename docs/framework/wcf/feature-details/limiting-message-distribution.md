---
title: Ograniczanie dystrybucji komunikatów
ms.date: 03/30/2017
ms.assetid: 8b5ec4b8-1ce9-45ef-bb90-2c840456bcc1
ms.openlocfilehash: 006cfaffe02752bb91e9f7d780477aecbaeb9c9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="limiting-message-distribution"></a>Ograniczanie dystrybucji komunikatów
Kanał elementu równorzędnego jest celowe emisji siatki. Jego podstawowy model powodziom obejmuje dystrybucja każdy komunikat wysyłany przez dowolnego członka siatki dla wszystkich członków tej siatki. Jest to idealne rozwiązanie w sytuacjach, w którym każdej wiadomości generowany przez element członkowski ma zastosowanie i jest przydatne do wszystkich innych członków (na przykład pokoju rozmów). Wiele aplikacji jednak okazjonalne potrzebę ograniczanie dystrybucji komunikatów. Na przykład jeśli nowy element członkowski przyłączy siatki i chce pobierać ostatnią wiadomością wysłaną za pośrednictwem sieci, tego żądania nie musi być propagowane do każdego elementu siatki. Żądanie może być ograniczona do umieszczonej blisko sąsiadów lub odfiltrowane wiadomości wygenerowaną lokalnie. Komunikaty mogą być również wysyłane do oddzielnego węzła w sieci. W tym temacie omówiono kontrolowania, jak komunikaty są przekazywane w całej sieci za pomocą liczby przeskoków, filtr propagacji komunikatu, Filtr lokalny lub połączenie bezpośrednie i zawiera ogólne wskazówki dotyczące wybierania podejście.  
  
## <a name="hop-counts"></a>Liczba przeskoków  
 Pojęcie `PeerHopCount` jest podobny do czas wygaśnięcia (Time-To-Live) używany w protokole IP. Wartość `PeerHopCount` jest powiązany z wystąpieniem komunikatu i określa, ile razy komunikat powinien zostać przekazany pakiet przed usuwane. Zawsze wiadomość zostanie odebrana przez kanał elementu równorzędnego klienta, klient sprawdza, czy komunikat, aby sprawdzić, czy `PeerHopCount` jest określona. Jeśli zostanie określony, następnie zmniejsza klienta przeskoków liczba wartości przez jeden przed przekazaniem wiadomości do sąsiednich węzłów. Kiedy klient otrzymuje wiadomość z liczby przeskoków wartość zero, Klient przetwarza wiadomości, ale nie przekazuje komunikat do sąsiadów.  
  
 Liczba przeskoków mogą być dodawane do wiadomości, dodając `PeerHopCount` jako atrybut do odpowiednich właściwości lub pola w implementacji klasy wiadomości. Możesz ustawić określoną wartość przed wysłaniem wiadomości do siatki. W ten sposób można użyć liczba przeskoków ograniczenie dystrybucji wiadomości w całej sieci, gdy jest to konieczne, potencjalnie unikanie niepotrzebnych wiadomości dublowania. Jest to przydatne w sytuacjach, gdy sieci zawiera wysokie zużycie nadmiarowych danych lub wysyłania komunikatu do natychmiastowego sąsiadów lub sąsiadów w kilka przeskoków.  
  
-   Wstawki kodu i powiązane informacje, zobacz [kanału równorzędnego blog](http://go.microsoft.com/fwlink/?LinkID=114531) (http://go.microsoft.com/fwlink/?LinkID=114531).  
  
## <a name="message-propagation-filter"></a>Filtr propagacji komunikatu  
 `MessagePropagationFilter` może służyć do niestandardowych kontroli zalewania wiadomości, szczególnie w przypadku, gdy zawartość komunikatu lub innych określonych scenariuszy określają propagacji. Filtr podejmowania decyzji w procesie propagacji dla każdego komunikatu, który przechodzi przez węzeł. Dotyczy to wiadomości pochodzących w innym miejscu siatki czy węzeł otrzymał oraz komunikatów utworzonych przez aplikację. Filtr ma dostęp do wiadomości oraz jego utworzenia, więc decyzji dotyczących przekazywania lub porzuca komunikat może być oparta na pełne informacje dostępne.  
  
 <xref:System.ServiceModel.PeerMessagePropagationFilter> to abstrakcyjna klasa podstawowa z jednej funkcji, <xref:System.ServiceModel.PeerMessagePropagationFilter.ShouldMessagePropagate%2A>. Pierwszy argument wywołania metody przekazuje w pełna kopia wiadomości. Wszelkie zmiany wprowadzone w komunikacie nie wpływają na rzeczywiste wiadomości. Ostatni argument wywołania metody, które identyfikuje źródło komunikatu (`PeerMessageOrigination.Local` lub `PeerMessageOrigination.Remote`). Konkretne implementacje tej metody musi zwracać stałej z <xref:System.ServiceModel.PeerMessagePropagation> wyliczenia wskazująca, że wiadomość jest do przekazania do aplikacji lokalnych (`Local`), są przekazywane do klientów zdalnych (`Remote`), oba (`LocalAndRemote`), żaden z tych (`None`). Ten filtr można zastosować uzyskując dostęp do odpowiadającego `PeerNode` obiektu i określanie wystąpienia pochodne propagacji filtrów klasy w `PeerNode.MessagePropagationFilter` właściwości. Upewnij się, że filtr propagacji jest dołączony przed otwarciem kanał elementu równorzędnego.  
  
-   Wstawki kodu i powiązane informacje, zobacz [kanału równorzędnego blog](http://go.microsoft.com/fwlink/?LinkID=114532) (http://go.microsoft.com/fwlink/?LinkID=114532).  
  
## <a name="contacting-an-individual-node-in-the-mesh"></a>Trwa nawiązywanie kontaktu z oddzielnego węzła w siatce  
 Konfigurując filtr lokalny lub konfigurując bezpośrednie połączenie można nawiązać połączenie oddzielnego węzła w siatkę.  
  
 Jeśli w węzłach siatki każdego Identyfikatora poszczególnych, identyfikator docelowy może określonej w implementacji wiadomości. Filtr lokalnych można skonfigurować przez pisanie funkcji w Twojej kontraktu komunikatu, które będą wyświetlane tylko wiadomości do bieżącego węzła Jeśli podany identyfikator docelowy pasuje do Identyfikatora. Siatki transportu wiadomości, więc obciążenie konfigurowania nowego połączenia nie ma powstać. Ponieważ komunikat jest wysyłany wiele razy w całej sieci istnieje jednak utraty wydajności. Działa to również do wysyłania wiadomości do poszczególnych elementów siatki, jak długo komunikaty nie są zbyt duże ani zbyt często.  
  
 Dla połączeń długotrwała, wysokiej przepustowości bezpośrednich połączeń są preferowane. Można wysłać informacje dotyczące połączenia za pośrednictwem sieci, a następnie skonfigurować bezpośrednie połączenie Wybieranie wysyłania i odbierania wiadomości.  
  
## <a name="choosing-an-approach-for-limiting-message-distribution"></a>Wybieranie metody dla ograniczanie dystrybucji komunikatów  
 Po odnalezieniu scenariusz, w którym należy ograniczyć dystrybucji komunikatów sobie na następujące pytania:  
  
-   **Kto** musi otrzymać wiadomość? Sąsiada tylko jeden węzeł? Węzeł gdzieś w sieci? Połowa sieci?  
  
-   **Jak często** otrzyma tę wiadomość?  
  
-   Jakiego rodzaju z **przepustowości** użyje tę wiadomość?  
  
 Odpowiedzi na te pytania mogą pomóc w określeniu, liczba przeskoków, filtr propagacji komunikatu, Filtr lokalny lub połączenie bezpośrednie. Należy rozważyć następujące ogólne wytyczne:  
  
-   **Kto**  
  
    -   *Oddzielnego węzła*: Filtr lokalny lub bezpośrednie połączenie.  
  
    -   *Sąsiadów w niektórych sąsiedztwa*: PeerHopCount.  
  
    -   *Złożone podzbiór siatkę*: Element MessagePropagationFilter.  
  
-   **Jak często**  
  
    -   *Bardzo często*: bezpośrednie połączenie, PeerHopCount, Element MessagePropagationFilter.  
  
    -   *Okazjonalne*: Filtr lokalny.  
  
-   **Wykorzystanie przepustowości**  
  
    -   *Wysoka*: bezpośrednie połączenie mniej wskazane zastosowanie Element MessagePropagationFilter lub Filtr lokalny.  
  
    -   *Niski*:, bezpośredniego połączenia prawdopodobnie nie jest wymagane.  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
