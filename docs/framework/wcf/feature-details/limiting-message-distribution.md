---
title: Ograniczanie dystrybucji komunikatów
ms.date: 03/30/2017
ms.assetid: 8b5ec4b8-1ce9-45ef-bb90-2c840456bcc1
ms.openlocfilehash: 36d9d43760e68f6bcf0099ac17dec5a8278d0e49
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2020
ms.locfileid: "76211907"
---
# <a name="limiting-message-distribution"></a>Ograniczanie dystrybucji komunikatów

Kanałem równorzędnym jest zaprojektowanie siatki emisji. Jego podstawowy model zalewania obejmuje dystrybuowanie każdej wiadomości wysyłanej przez dowolnego członka siatki do wszystkich innych członków tej siatki. Jest to idealne rozwiązanie w sytuacjach, gdy każdy komunikat generowany przez członka jest istotny i przydatny dla wszystkich innych członków (na przykład pokoju rozmów). Jednak wiele aplikacji ma sporadyczną potrzebę do ograniczania dystrybucji komunikatów. Na przykład jeśli nowy element członkowski łączy siatkę i chce pobrać ostatnią wiadomość wysłaną przez siatkę, to żądanie nie musi być zalewana do każdego elementu członkowskiego siatki. Żądanie może być ograniczone do bliskich sąsiadów lub można odfiltrować lokalnie wygenerowane komunikaty. Komunikaty mogą być również wysyłane do poszczególnych węzłów siatki. W tym temacie omówiono użycie liczby przeskoków, filtru propagacji komunikatów, lokalnego filtru lub bezpośredniego połączenia w celu kontrolowania sposobu przekazywania komunikatów w całej sieci i przedstawiono ogólne wytyczne dotyczące wybierania podejścia.

## <a name="hop-counts"></a>Liczba przeskoków

Koncepcja `PeerHopCount` jest podobna do czasu wygaśnięcia (Time-to-Live) używanego w protokole IP. Wartość `PeerHopCount` jest powiązana z wystąpieniem komunikatu i określa, ile razy wiadomość powinna być przekazywana przed porzuceniem. Za każdym razem, gdy komunikat jest odbierany przez klienta kanału równorzędnego, klient analizuje komunikat, aby zobaczyć, czy `PeerHopCount` jest określony. Jeśli jest określona, klient zmniejsza wartość liczby przeskoków o jeden przed przekazaniem komunikatu do sąsiednich węzłów. Gdy klient otrzymuje komunikat z wartością liczby przeskoków równą zero, Klient przetwarza komunikat, ale nie przekazuje komunikatu do sąsiadów.

Licznik przeskoków może zostać dodany do komunikatu przez dodanie `PeerHopCount` jako atrybutu do odpowiedniej właściwości lub pola w implementacji klasy komunikatów. Można ją ustawić na określoną wartość przed wysłaniem komunikatu do siatki. W ten sposób można użyć liczby przeskoków, aby ograniczyć dystrybucję komunikatów w sieci w razie potrzeby, potencjalnie unikając niepotrzebne duplikowanie komunikatów. Jest to przydatne w przypadkach, gdy siatka zawiera dużą ilość danych nadmiarowych lub do wysyłania komunikatów do bezpośrednich sąsiadów lub sąsiadów w ciągu kilku przeskoków.

- Fragmenty kodu i powiązane informacje można znaleźć w [atrybucie PeerHopCount: kontrolowanie wpisu dystrybucji komunikatów](https://docs.microsoft.com/archive/blogs/peerchan/the-peerhopcount-attribute-controlling-message-distribution) na blogu kanału równorzędnego.

## <a name="message-propagation-filter"></a>Filtr propagacji komunikatów

`MessagePropagationFilter` może służyć do dostosowanej kontroli zalewania komunikatów, szczególnie w przypadku, gdy zawartość wiadomości lub innych określonych scenariuszy decyduje o propagacji. Filtr wykonuje decyzje propagacji dla każdego komunikatu, który przechodzi przez węzeł. Jest to prawdziwe w przypadku komunikatów, które pochodzą z innych miejsc w siatce, które zostały odebrane przez ten węzeł, a także wiadomości utworzonych przez aplikację. Filtr ma dostęp zarówno do wiadomości, jak i jej pochodzenia, dlatego decyzje dotyczące przekazywania lub porzucania wiadomości mogą opierać się na pełnych dostępnych informacjach.

<xref:System.ServiceModel.PeerMessagePropagationFilter> jest podstawową klasą abstrakcyjną z pojedynczą funkcją, <xref:System.ServiceModel.PeerMessagePropagationFilter.ShouldMessagePropagate%2A>. Pierwszy argument wywołania metody przekazuje pełną kopię wiadomości. Wszelkie zmiany wprowadzone w komunikacie nie wpływają na rzeczywistą wiadomość. Ostatni argument wywołania metody Określa początek komunikatu (`PeerMessageOrigination.Local` lub `PeerMessageOrigination.Remote`). Konkretne implementacje tej metody muszą zwracać stałą z wyliczenia <xref:System.ServiceModel.PeerMessagePropagation> wskazujący, że wiadomość ma być przekazywana do lokalnej aplikacji (`Local`), przesyłana dalej do klientów zdalnych (`Remote`), obu (`LocalAndRemote`) lub żadnego (`None`). Ten filtr można zastosować, uzyskując dostęp do odpowiedniego obiektu `PeerNode` i określając wystąpienie klasy filtru propagacji pochodnej we właściwości `PeerNode.MessagePropagationFilter`. Przed otwarciem kanału równorzędnego upewnij się, że jest dołączony filtr propagacji.

- Fragmenty kodu i powiązane informacje znajdują się w witrynie [peer Channel i MessagePropagationFilter](https://docs.microsoft.com/archive/blogs/peerchan/peer-channel-and-messagepropagationfilter) post na blogu kanału równorzędnego.

## <a name="contacting-an-individual-node-in-the-mesh"></a>Kontaktowanie się z pojedynczym węzłem w sieci

Można skontaktować się z pojedynczym węzłem w siatce przez skonfigurowanie lokalnego filtru lub przez skonfigurowanie połączenia bezpośredniego.

Jeśli węzły w siatce mają poszczególne identyfikatory, w implementacji wiadomości można określić identyfikator docelowy. Filtr lokalny można skonfigurować przez napisanie funkcji w kontrakcie wiadomości, która będzie wyświetlać komunikat tylko do bieżącego węzła, jeśli jego identyfikator jest zgodny z określonym IDENTYFIKATORem docelowym. Siatka transportuje komunikat, dzięki czemu obciążenie związane z konfigurowaniem nowego połączenia nie musi być naliczane. Istnieje jednak utrata wydajności, ponieważ wiadomość jest wysyłana wiele razy w całej sieci. Jest to dobre rozwiązanie w przypadku wysyłania komunikatów do poszczególnych elementów członkowskich siatki, o ile komunikaty nie są zbyt duże ani zbyt częste.

W przypadku długotrwałych połączeń o dużej przepustowości preferowane są bezpośrednie połączenia. Informacje o połączeniu można wysłać przez siatkę, a następnie skonfigurować bezpośrednie połączenie z wybieraniem do wysyłania/odbierania wiadomości.

## <a name="choosing-an-approach-for-limiting-message-distribution"></a>Wybieranie podejścia do ograniczania dystrybucji komunikatów

Po znalezieniu scenariusza, w którym należy ograniczyć dystrybucję wiadomości, należy zadać sobie następujące pytania:

- **Kto** musi odebrać komunikat? Tylko jeden węzeł sąsiada? Węzeł w innym miejscu siatki? Połowa siatki?

- **Jak często** będzie wysyłany ten komunikat?

- Jakiego rodzaju **przepustowość** będzie używać ten komunikat?

Odpowiedzi na te pytania mogą pomóc w ustaleniu, czy użyć liczby przeskoków, filtru propagacji komunikatów, lokalnego filtru czy połączenia bezpośredniego. Należy wziąć pod uwagę następujące ogólne wytyczne:

- **Którzy**

  - *Pojedynczy węzeł*: filtr lokalny lub bezpośrednie połączenie.

  - *Sąsiedzi w określonym sąsiedztwie*: PeerHopCount.

  - *Złożony podzestaw siatki*: MessagePropagationFilter.

- **Jak często**

  - *Bardzo częste*: połączenie bezpośrednie, PeerHopCount, MessagePropagationFilter.

  - *Sporadycznie*: filtr lokalny.

- **Wykorzystanie przepustowości**

  - *Wysoki*: bezpośrednie połączenie, mniej zalecane do użycia MessagePropagationFilter lub filtru lokalnego.

  - *Niska*: dowolne, bezpośrednie połączenie prawdopodobnie nie jest potrzebne.

## <a name="see-also"></a>Zobacz także

- [Tworzenie aplikacji kanału równorzędnego](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
