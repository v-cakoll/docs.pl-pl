---
title: Ograniczanie dystrybucji komunikatów
ms.date: 03/30/2017
ms.assetid: 8b5ec4b8-1ce9-45ef-bb90-2c840456bcc1
ms.openlocfilehash: 113244e6c7eb356d70e9ffb7b85367e9feb34c54
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64750653"
---
# <a name="limiting-message-distribution"></a>Ograniczanie dystrybucji komunikatów

Kanał elementu równorzędnego jest celowe emisji siatki. Jego podstawowy model powodziom obejmuje dystrybucja każdy komunikat wysyłany przez dowolnego członka siatki dla wszystkich członków tej siatki. Jest to idealne rozwiązanie w sytuacjach, w którym każdy komunikat generowany przez element członkowski ma zastosowanie i jest przydatne do wszystkich innych elementów członkowskich (na przykład pokoju rozmów). Jednak wiele aplikacji mają sporadyczne potrzebę ograniczanie dystrybucji komunikatów. Na przykład jeśli nowy element członkowski sprzężenia siatki i chce, aby pobrać ostatnią wiadomością wysłaną za pośrednictwem sieci, to żądanie nie trzeba propagowane do każdego członka siatkę. Żądanie może być ograniczona do umieszczonej blisko sąsiadów lub odfiltrowane wiadomości wygenerowaną lokalnie. Komunikaty mogą być również wysyłane do jednego węzła na siatkę. W tym temacie omówiono użycie liczba przeskoków, filtr Propagacja komunikatów, Filtr lokalny lub bezpośrednie połączenie do kontrolowania, jak wiadomości są przekazywane w całej sieci i zapewnia ogólne wskazówki dotyczące wybierania podejście.

## <a name="hop-counts"></a>Liczba przeskoków

Pojęcie `PeerHopCount` jest podobny do czasu wygaśnięcia (Time-To-Live) używane w protokole IP. Wartość `PeerHopCount` jest powiązany z wystąpienia wiadomości i określa, ile razy komunikat powinien zostać przekazany pakiet przed porzucana. Każdorazowo, wiadomość zostaje odebrana przez kanał elementu równorzędnego klienta, klient sprawdza, czy komunikat, aby sprawdzić, czy `PeerHopCount` jest określony. Jeśli zostanie określony, następnie zmniejsza klienta przeskok wartości liczby za pomocą jednej przed przekazaniem wiadomości do sąsiedniego węzłów. Kiedy klient otrzymuje komunikat, liczba przeskoków wartość zero, klient przetworzy komunikat, ale nie przekazuje komunikat do sąsiadów.

Liczba przeskoków mogą być dodawane do wiadomości, dodając `PeerHopCount` jako atrybut do odpowiednich właściwości lub pól w implementacji klasy wiadomości. Możesz ustawić określoną wartość przed wysłaniem wiadomości do siatki. W ten sposób można użyć liczby przeskoków ograniczyć rozłożenia komunikatów w całej sieci, gdy jest to konieczne, potencjalnie unikanie duplikowania zbędnych komunikatów. Jest to przydatne w przypadkach, w którym siatkę znajduje wysokiej ilość nadmiarowych danych lub wysyłania komunikatu do natychmiastowego sąsiadów lub sąsiadów w obrębie kilka przeskoków.

- Fragmenty kodu i powiązane informacje, zobacz [blogu kanał elementu równorzędnego](https://go.microsoft.com/fwlink/?LinkID=114531).

## <a name="message-propagation-filter"></a>Filtr Propagacja komunikatów

`MessagePropagationFilter` może służyć do niestandardowych kontroli komunikat o przepełnieniu, szczególnie w przypadku, gdy treść komunikatu lub innych określonych scenariuszy określają propagacji. Filtr podejmuje decyzje propagacji dla każdego komunikatu, który przechodzi przez węzeł. Ta zasada obowiązuje dla komunikatów pochodzących gdzie indziej w siatce, Twój węzeł otrzymał oraz komunikaty tworzone przez testowaną aplikację. Filtr ma dostęp do wiadomości i jego pochodzenia, więc decyzji dotyczących przekazywania lub porzuca wiadomość może bazować na pełne informacje dostępne.

<xref:System.ServiceModel.PeerMessagePropagationFilter> jest abstrakcyjna klasa bazowa przy użyciu funkcji pojedynczego, <xref:System.ServiceModel.PeerMessagePropagationFilter.ShouldMessagePropagate%2A>. Pierwszy argument wywołania metody które przekazuje pełną kopię wiadomości. Wszelkie zmiany wprowadzone do wiadomości nie wpływają na komunikat rzeczywiste. Ostatni argument wywołania metody które określa źródło wiadomości (`PeerMessageOrigination.Local` lub `PeerMessageOrigination.Remote`). Konkretne implementacje tej metody musi zwracać stałej z <xref:System.ServiceModel.PeerMessagePropagation> wyliczenie co oznacza, że wiadomości były przekazywane do aplikacji lokalnej (`Local`), są przekazywane z klientami zdalnymi (`Remote`), zarówno (`LocalAndRemote`), żaden z tych (`None`). Ten filtr można zastosować, uzyskując dostęp do odpowiednich `PeerNode` obiektu i określając wystąpienia pochodne propagacji filtrowania klasy w `PeerNode.MessagePropagationFilter` właściwości. Upewnij się, że filtr propagacji jest dołączony przed otwarciem kanał elementu równorzędnego.

- Fragmenty kodu i powiązane informacje, zobacz [blogu kanał elementu równorzędnego](https://go.microsoft.com/fwlink/?LinkID=114532).

## <a name="contacting-an-individual-node-in-the-mesh"></a>Nawiązywanie kontaktu z poszczególnych węzłów w siatce

Można się skontaktować poszczególnych węzeł w siatce, konfigurując Filtr lokalny lub przez ustawienie bezpośredniego połączenia z programem.

Jeśli węzły w siatce każdego Identyfikatora poszczególnych, można określić identyfikator docelowego w implementacji wiadomości. Filtr lokalny można skonfigurować pod kątem przez pisanie funkcji w swojej kontraktu komunikatu, które będą wyświetlane tylko wiadomości do bieżącego węzła, jeśli określony identyfikator docelowy pasuje do Identyfikatora. Siatkę służy do transportu komunikatów, dzięki czemu obciążenie Konfigurowanie nowego połączenia nie musi być naliczane. Jednak istnieje utraty wydajności, ponieważ komunikat jest wysyłany wiele razy w całej sieci. Działa to dobrze w przypadku wysyłania wiadomości do poszczególnych elementów siatki, tak długo, jak długo komunikaty nie są zbyt duże ani zbyt często.

W przypadku długotrwałych i dużej przepustowości połączeń bezpośrednich połączeń są preferowane w porównaniu. Możesz wysłać informacje dotyczące połączenia za pośrednictwem sieci i następnie skonfigurować połączenie bezpośrednie Wybieranie funkcję wysyłania i odbierania komunikatów.

## <a name="choosing-an-approach-for-limiting-message-distribution"></a>Wybieranie podejścia do ograniczanie dystrybucji komunikatów

Po odnalezieniu scenariusz, w której chcesz ograniczyć dystrybucji komunikatów odpowiedzieć sobie na następujące pytania:

- **Kto** musi otrzymać wiadomość? Sąsiadujące tylko jeden węzeł? Węzeł gdzieś w sieci? Połowa siatki?

- **Jak często** będzie można wysłać tej wiadomości?

- Jakiego rodzaju elementu **przepustowości** użyje tej wiadomości?

Odpowiedzi na te pytania mogą pomóc w określeniu, czy ma być używany, liczba przeskoków, filtr Propagacja komunikatów, Filtr lokalny lub bezpośrednie połączenie. Należy rozważyć następujące ogólne wytyczne:

- **Kto**

  - *Pojedynczych węzłów*:  Filtr lokalny lub bezpośrednie połączenie.

  - *Sąsiadów w niektórych sąsiedztwa*:  PeerHopCount.

  - *Złożone podzbiór siatkę*:  MessagePropagationFilter.

- **Jak często**

  - *Bardzo często*:  Bezpośrednie połączenie, PeerHopCount, MessagePropagationFilter.

  - *Sporadyczne*:  Filtr lokalny.

- **Wykorzystanie przepustowości**

  - *Wysoka*:  Bezpośrednie połączenie, mniej wskazane zastosowanie MessagePropagationFilter lub lokalnego filtru.

  - *Niska*:  Istnieje bezpośrednie połączenie prawdopodobnie nie jest wymagane.

## <a name="see-also"></a>Zobacz także

- [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
