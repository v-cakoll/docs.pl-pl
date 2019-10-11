---
title: Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych
description: Dowiedz się, jak działa moduł zbierający elementy bezużyteczne i jak można go skonfigurować pod kątem optymalnej wydajności.
ms.date: 03/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background garbage collection
- garbage collection, concurrent garbage collection
- garbage collection, server garbage collection
- garbage collection, workstation garbage collection
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0c0fa0e2c59856beda65ec5804b8896352db98b3
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/09/2019
ms.locfileid: "72180194"
---
# <a name="fundamentals-of-garbage-collection"></a>Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych

<a name="top"></a>W środowisku uruchomieniowym języka wspólnego (CLR) Moduł wyrzucania elementów bezużytecznych służy jako automatyczne Menedżera pamięci. Zapewnia następujące korzyści:

- Umożliwia tworzenie aplikacji bez konieczności ręcznego zwalniania pamięci dla utworzonych obiektów.

- Efektywnie przydziela obiekty na stosie zarządzanym.

- Reoświadczenia obiektów, które nie są już używane, czyści ich pamięć i utrzymuje dostępną pamięć do przyszłych alokacji. Obiekty zarządzane automatycznie pobierają czystą zawartość do początku, więc ich konstruktory nie muszą inicjować każdego pola danych.

- Zapewnia bezpieczeństwo pamięci, upewniając się, że obiekt nie może użyć zawartości innego obiektu.

 W tym temacie opisano podstawowe pojęcia dotyczące wyrzucania elementów bezużytecznych.

<a name="fundamentals_of_memory"></a>

## <a name="fundamentals-of-memory"></a>Podstawowe informacje o pamięci

Poniższa lista zawiera podsumowanie ważnych pojęć dotyczących pamięci środowiska CLR.

- Każdy proces ma własną, oddzielną wirtualną przestrzeń adresową. Wszystkie procesy na tym samym komputerze współużytkują tę samą pamięć fizyczną i udostępniają plik stronicowania, jeśli taki istnieje.

- Domyślnie na komputerach 32-bitowych każdy proces ma 2 GB wirtualnej przestrzeni adresowej w trybie użytkownika.

- Jako deweloper aplikacji pracujesz tylko z wirtualną przestrzenią adresową i nigdy nie manipulujesz bezpośrednio pamięci fizycznej. Moduł wyrzucania elementów bezużytecznych przydziela i zwalnia pamięć wirtualną na zarządzanym stosie.

  Jeśli piszesz kod natywny, używasz funkcji Win32 do pracy z wirtualną przestrzenią adresową. Te funkcje przydzielą i zwalniają pamięć wirtualną na stertach natywnych.

- Pamięć wirtualna może mieć trzy stany:

  - Bezpłatnie. Blok pamięci nie ma odwołań do niego i jest dostępny do alokacji.

  - Rezerwacj. Blok pamięci jest dostępny do użycia i nie może być używany w żadnym innym żądaniu alokacji. Nie można jednak przechowywać danych w tym bloku pamięci, dopóki nie zostanie on zatwierdzony.

  - Prowadzono. Blok pamięci jest przypisany do magazynu fizycznego.

- Wirtualne przestrzenie adresowe mogą zostać pofragmentowane. Oznacza to, że w przestrzeni adresowej istnieją wolne bloki, znane także jako otwory. Po zażądaniu alokacji pamięci wirtualnej Menedżer pamięci wirtualnej musi znaleźć pojedynczy bezpłatny blok, który jest wystarczająco duży, aby spełnić to żądanie alokacji. Nawet jeśli masz 2 GB wolnego miejsca, alokacja, która wymaga 2 GB, nie powiedzie się, chyba że wszystkie te wolne miejsca znajdują się w jednym bloku adresów.

- Można wypróbować za mało pamięci, jeśli zabrakło wirtualnej przestrzeni adresowej do zarezerwowania lub miejsca fizycznego do zatwierdzenia.

Plik stronicowania jest używany nawet w przypadku niskiej ilości pamięci fizycznej (to jest zapotrzebowanie na ilość pamięci fizycznej). Gdy wykorzystanie pamięci fizycznej odbywa się po raz pierwszy, system operacyjny musi zwolnić miejsce w pamięci fizycznej do przechowywania danych, a następnie tworzy kopię zapasową niektórych danych znajdujących się w pamięci fizycznej do pliku stronicowania. Te dane nie są stronicowane, dopóki nie jest to konieczne, więc można napotkać stronicowanie w sytuacjach, gdy wykorzystanie pamięci fizycznej jest bardzo niskie.

[Powrót do początku](#top)

<a name="conditions_for_a_garbage_collection"></a>

## <a name="conditions-for-a-garbage-collection"></a>Warunki dla wyrzucania elementów bezużytecznych

Odzyskiwanie pamięci występuje, gdy spełniony jest jeden z następujących warunków:

- System ma małą ilość pamięci fizycznej. Jest on wykrywany przez powiadomienie o braku pamięci z systemu operacyjnego lub małej ilości pamięci wskazanej przez hosta.

- Pamięć używana przez przydzielone obiekty na zarządzanej stercie przekracza akceptowalny próg. Ten próg jest ciągle dostosowywany podczas uruchamiania procesu.

- Metoda <xref:System.GC.Collect%2A?displayProperty=nameWithType> jest wywoływana. W prawie wszystkich przypadkach nie trzeba wywoływać tej metody, ponieważ moduł wyrzucania elementów bezużytecznych działa w sposób ciągły. Ta metoda jest używana głównie do unikatowych sytuacji i testowania.

[Powrót do początku](#top)

<a name="the_managed_heap"></a>

## <a name="the-managed-heap"></a>Zarządzane sterty

Po zainicjowaniu modułu wyrzucania elementów bezużytecznych przez środowisko CLR przydziela on segment pamięci do przechowywania obiektów i zarządzania nimi. Ta pamięć jest nazywana stertą zarządzaną, w przeciwieństwie do sterty natywnej w systemie operacyjnym.

Istnieje sterta zarządzana dla każdego procesu zarządzanego. Wszystkie wątki w procesie przydzielają pamięć dla obiektów na tym samym stosie.

W celu zarezerwowania pamięci moduł zbierający elementy bezużyteczne wywołuje funkcję Win32 [Funkcja VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) i rezerwuje jeden segment pamięci w czasie dla aplikacji zarządzanych. Moduł wyrzucania elementów bezużytecznych rezerwuje również segmenty w miarę potrzeby i zwalnia segmenty z powrotem do systemu operacyjnego (po wyczyszczeniu ich z dowolnego obiektu), wywołując funkcję Win32 [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) .

> [!IMPORTANT]
> Rozmiar segmentów przydzielone przez moduł wyrzucania elementów bezużytecznych jest specyficzny dla implementacji i może ulec zmianie w dowolnym momencie, łącznie z okresowymi aktualizacjami. Aplikacja nigdy nie powinna mieć założeń lub zależeć od określonego rozmiaru segmentu ani nie powinna próbować skonfigurować ilości pamięci dostępnej dla alokacji segmentu.

Im mniejsza liczba obiektów przypadających na stosie, tym mniejsza ilość pracy do wykonania przez moduł zbierający elementy bezużyteczne. W przypadku przydzielania obiektów nie należy używać wartości zaokrąglonych, które przekraczają Twoje potrzeby, na przykład przydzielając tablicę 32 bajtów, gdy potrzebne są tylko 15 bajtów.

Po wyzwoleniu wyrzucania elementów bezużytecznych moduł zbierający elementy bezużyteczne odzyskuje pamięć, która jest zajęta przez obiekty martwe. Proces odzyskiwania kompaktuje obiekty na żywo, dzięki czemu są one przenoszone razem, a wolne miejsce zostaje usunięte, co sprawia, że sterta jest mniejsza. Dzięki temu obiekty, które są przydzielane razem, pozostają razem na zarządzanym stosie, aby zachować ich miejscowość.

Nietrwałość (częstotliwość i czas trwania) wyrzucania elementów bezużytecznych to wynik ilości alokacji i ilości pamięci przeprowadzonej w zarządzanym stosie.

Sterta może być traktowana jako akumulacja dwóch stert: [sterty dużych obiektów](large-object-heap.md) i sterty małego obiektu.

[Sterta dużego obiektu](large-object-heap.md) zawiera bardzo duże obiekty, które są 85 000 bajtów i większych. Obiekty na stosie dużego obiektu są zazwyczaj tablicami. Wystąpienie obiektu wystąpienia jest rzadkim zdarzeniem bardzo duże.

[Powrót do początku](#top)

<a name="generations"></a>

## <a name="generations"></a>Generacje

Stos jest zorganizowany do generacji, aby mógł obsługiwać długotrwałe i krótkotrwałe obiekty. Wyrzucanie elementów bezużytecznych odbywa się głównie z odzyskiwaniem obiektów krótkoterminowych, które zwykle zajmują tylko małą część sterty. Na stercie znajdują się trzy generacje obiektów:

- **Generacja 0**. Jest to najmłodsze generowanie i zawiera obiekty krótkotrwałe. Przykładem obiektu krótkotrwałego jest zmienna tymczasowa. Wyrzucanie elementów bezużytecznych występuje najczęściej w tej generacji.

  Nowo przydzielono obiekty tworzą nową generację obiektów i wyrzucają niejawnie kolekcje 0, chyba że są to duże obiekty, w takim przypadku przechodzą na stertę dużego obiektu w kolekcji generacji 2.

  Większość obiektów jest odzyskiwana do wyrzucania elementów bezużytecznych w generacji 0 i nie przechodzenia do nowej generacji.

- **Generacja 1**. Ta generacja zawiera obiekty krótkoterminowe i służy jako bufor między obiektami krótko-i długotrwałymi.

- **Generacja 2**. Ta generacja zawiera obiekty długotrwałe. Przykładem obiektu o długim czasie istnienia jest obiekt w aplikacji serwera, który zawiera dane statyczne na żywo na czas trwania procesu.

Wyrzucanie elementów bezużytecznych odbywa się w określonych generacjach, gdy jest to warunki Zbieranie generacji oznacza gromadzenie obiektów w tej generacji i wszystkich jej młodszych generacjach. Wyrzucanie elementów bezużytecznych generacji 2 jest również znane jako pełne wyrzucanie elementów bezużytecznych, ponieważ przejmuje wszystkie obiekty we wszystkich generacjach (czyli wszystkie obiekty w stercie zarządzanym).

### <a name="survival-and-promotions"></a>Przeżycia i promocja

Obiekty, które nie są odzyskiwane w wyrzucaniu elementów bezużytecznych, są znane jako osoby do wygenerowania i są promowane do następnej generacji. Obiekty, które przeżyły wyrzucanie elementów bezużytecznych generacji 0, zostały podwyższone do generacji 1; obiekty, które przeżyły wyrzucanie elementów bezużytecznych generacji 1, są podwyższane do generacji 2; i obiekty, które przeżyły wyrzucanie elementów bezużytecznych generacji 2, pozostają w generacji 2.

Gdy moduł wyrzucania elementów bezużytecznych wykryje, że stopień przeżycia jest wysoki w generacji, zwiększa próg alokacji dla tej generacji, więc Następna kolekcja pobiera znaczny rozmiar odzyskiwanej pamięci. Środowisko CLR ciągle równoważy dwa priorytety: nie pozwala to na zbyt duży zestaw roboczy aplikacji, co nie pozwala na wyrzucanie elementów bezużytecznych.

### <a name="ephemeral-generations-and-segments"></a>Pokoleń tymczasowych i segmentów

Ponieważ obiekty w generacji 0 i 1 są krótkoterminowe, te generacje są znane jako generacja tymczasowych.

Pokoleń tymczasowych należy przydzielić w segmencie pamięci, który jest znany jako segment tymczasowych. Każdy nowy segment uzyskany przez moduł wyrzucania elementów bezużytecznych stał się nowym segmentem tymczasowych i zawiera obiekty, które przeżyły wyrzucanie elementów bezużytecznych generacji 0. Stary segment tymczasowych zostanie segmentem nowej generacji 2.

Rozmiar segmentu tymczasowych różni się w zależności od tego, czy system jest 32-czy 64-bitowy, i na typie modułu wyrzucania elementów bezużytecznych, który jest uruchomiony. Wartości domyślne są pokazane w poniższej tabeli.

||32 — bit|64 — bit|
|-|-------------|-------------|
|Stacja robocza GC|16 MB|256 MB|
|Serwer GC|64 MB|4 GB|
|Serwer GC z procesorami logicznymi > 4|32 MB|2 GB|
|Serwer GC z > 8 procesorami logicznymi|16 MB|1 GB|

Segment tymczasowych może obejmować obiekty generacji 2. Obiekty generacji 2 mogą korzystać z wielu segmentów (tyle, ile wymaga proces i czy pamięć zezwala na system).

Ilość zwolnionej pamięci z tymczasowego wyrzucania elementów bezużytecznych jest ograniczona do rozmiaru segmentu tymczasowych. Ilość wolnej pamięci jest proporcjonalna do miejsca, które było zajęte przez obiekty martwe.

[Powrót do początku](#top)

<a name="what_happens_during_a_garbage_collection"></a>

## <a name="what-happens-during-a-garbage-collection"></a>Co się dzieje podczas wyrzucania elementów bezużytecznych

Wyrzucanie elementów bezużytecznych ma następujące fazy:

- Faza oznaczania, która wyszukuje i tworzy listę wszystkich obiektów na żywo.

- Faza zmiany lokalizacji, która aktualizuje odwołania do obiektów, które zostaną skompaktowane.

- Faza kompaktowania, która odzyskuje miejsce zajęte przez obiekty martwe i kompaktuje pozostałe obiekty. Faza kompaktowania przenosi obiekty, które przeżyły wyrzucanie elementów bezużytecznych do starszych końców segmentu.

  Ponieważ kolekcje generacji 2 mogą zajmować wiele segmentów, obiekty, które są promowane do generacji 2 można przenieść do starszego segmentu. Zarówno osoby przestające 1, jak i 2 mogą zostać przeniesione do innego segmentu, ponieważ są one podwyższane do generacji 2.

  Zwykle sterta dużego obiektu nie jest kompaktowa, ponieważ kopiowanie dużych obiektów nakłada spadek wydajności. Jednak rozpoczynając od .NET Framework 4.5.1, można użyć właściwości <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>, aby skompaktować stertę dużego obiektu na żądanie.

Moduł wyrzucania elementów bezużytecznych używa następujących informacji, aby określić, czy obiekty są aktywne:

- Elementy **Główne stosu**. Zmienne stosu udostępniane przez kompilator just-in-Time (JIT) i Analizator stosu. Należy zauważyć, że optymalizacje JIT mogą wydłużać lub skracać regiony kodu, w których zmienne stosu są zgłaszane do modułu wyrzucania elementów bezużytecznych.

- **Dojść do wyrzucania elementów bezużytecznych**. Obsługuje obiekty zarządzane, które mogą być przydzielone przez kod użytkownika lub przez środowisko uruchomieniowe języka wspólnego.

- **Dane statyczne**. Obiekty statyczne w domenach aplikacji, które mogą odwoływać się do innych obiektów. Każda domena aplikacji śledzi swoje obiekty statyczne.

Przed uruchomieniem odzyskiwania pamięci wszystkie zarządzane wątki są zawieszane z wyjątkiem wątku, który wyzwolił wyrzucanie elementów bezużytecznych.

Na poniższej ilustracji przedstawiono wątek wyzwalający wyrzucanie elementów bezużytecznych i powoduje zawieszenie innych wątków.

![Gdy wątek wyzwala wyrzucanie elementów bezużytecznych],(../../../docs/standard/garbage-collection/media/gc-triggered.png "gdy wątek wyzwala wyrzucanie elementów bezużytecznych")

[Powrót do początku](#top)

<a name="manipulating_unmanaged_resources"></a>

## <a name="manipulating-unmanaged-resources"></a>Manipulowanie niezarządzanymi zasobami

Jeśli obiekty zarządzane odwołują się do niezarządzanych obiektów przy użyciu natywnych uchwytów plików, należy jawnie zwolnić obiekty niezarządzane, ponieważ moduł wyrzucania elementów bezużytecznych śledzi pamięć tylko na stercie zarządzanym.

Użytkownicy obiektu zarządzanego nie mogą zlikwidować zasobów natywnych używanych przez obiekt. Aby przeprowadzić oczyszczanie, można sprawić, aby obiekt zarządzany został sfinalizowany. Finalizowanie składa się z akcji oczyszczania, które są wykonywane, gdy obiekt nie jest już używany. Gdy zarządzany obiekt jest realizowany, wykonuje akcje oczyszczania, które są określone w jego metodzie finalizatora.

Gdy odnaleziony obiekt jest niemartwy, jego finalizator jest umieszczany w kolejce, aby zostały wykonane akcje oczyszczania, ale sam obiekt zostanie podwyższony do nowej generacji. W związku z tym należy poczekać na następne wyrzucanie elementów bezużytecznych w tej generacji (co nie musi być następną kolekcją elementów bezużytecznych), aby określić, czy obiekt został odrzucony.

[Powrót do początku](#top)

<a name="workstation_and_server_garbage_collection"></a>

## <a name="workstation-and-server-garbage-collection"></a>Stacja robocza i odzyskiwanie pamięci serwera

Moduł wyrzucania elementów bezużytecznych jest samodostrajania i może współpracować w wielu różnych scenariuszach. Możesz użyć ustawienia pliku konfiguracji, aby ustawić typ wyrzucania elementów bezużytecznych na podstawie charakterystyki obciążenia. Środowisko CLR udostępnia następujące typy wyrzucania elementów bezużytecznych:

- Wyrzucanie elementów bezużytecznych stacji roboczej dla wszystkich stacji roboczych klienta i komputerów autonomicznych. Jest to ustawienie domyślne dla [elementu \<gcServer >](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) w schemacie konfiguracji środowiska uruchomieniowego.

  Wyrzucanie elementów bezużytecznych stacji roboczej może być współbieżne lub niewspółbieżne. Współbieżne wyrzucanie elementów bezużytecznych umożliwia zarządzanym wątkom kontynuowanie operacji podczas odzyskiwania pamięci.

  Począwszy od .NET Framework 4, wyrzucanie elementów bezużytecznych w tle zastępuje współbieżne odzyskiwanie pamięci.

- Odzyskiwanie pamięci serwera, które jest przeznaczone dla aplikacji serwerowych, które potrzebują dużej przepływności i skalowalności. Zbieranie elementów bezużytecznych serwera może być niewspółbieżne lub niezgodne.

Na poniższej ilustracji przedstawiono dedykowane wątki, które wykonują wyrzucanie elementów bezużytecznych na serwerze.

Wątki odzyskiwania ![pamięci serwera wątki](../../../docs/standard/garbage-collection/media/gc-server.png "odzyskiwania pamięci serwera")

### <a name="configuring-garbage-collection"></a>Konfigurowanie wyrzucania elementów bezużytecznych

Można użyć [elementu \<gcServer >](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) schematu konfiguracji środowiska uruchomieniowego, aby określić typ wyrzucania elementów bezużytecznych, które ma wykonywać środowisko CLR. Gdy atrybut `enabled` tego elementu ma ustawioną wartość `false` (wartość domyślna), środowisko CLR wykonuje wyrzucanie elementów bezużytecznych stacji roboczej. Po ustawieniu atrybutu `enabled` na `true` środowisko CLR wykonuje wyrzucanie elementów bezużytecznych serwera.

Współbieżne wyrzucanie elementów bezużytecznych jest określone za pomocą [elementu \<gcConcurrent >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) schemacie konfiguracji środowiska uruchomieniowego. Ustawieniem domyślnym jest `enabled`. To ustawienie określa współbieżne i wyrzucanie elementów bezużytecznych w tle.

Można również określić wyrzucanie elementów bezużytecznych serwera za pomocą niezarządzanych interfejsów hostingu. Należy pamiętać, że ASP.NET i SQL Server Włącz automatyczne odzyskiwanie serwera, jeśli aplikacja jest hostowana w jednym z tych środowisk.

### <a name="comparing-workstation-and-server-garbage-collection"></a>Porównywanie wyrzucania elementów roboczych stacji roboczej i serwera

Poniżej przedstawiono zagadnienia dotyczące wątkowości i wydajności dotyczące wyrzucania elementów bezużytecznych stacji roboczej:

- Kolekcja odbywa się w wątku użytkownika, który wyzwolił wyrzucanie elementów bezużytecznych i pozostaje na tym samym priorytecie. Ponieważ wątki użytkownika zwykle działają przy normalnym priorytecie, Moduł wyrzucania elementów bezużytecznych (który jest uruchamiany w wątku o normalnym priorytecie) musi konkurować z innymi wątkami czasu procesora CPU.

  Wątki, na których działa kod natywny, nie są wstrzymane.

- Wyrzucanie elementów bezużytecznych stacji roboczej jest zawsze używane na komputerze, który ma tylko jeden procesor, niezależnie od ustawienia [> \<gcServer](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) . W przypadku określenia wyrzucania elementów bezużytecznych serwera środowisko CLR używa wyrzucania elementów bezużytecznych stacji roboczej z wyłączonym

Poniżej przedstawiono zagadnienia związane z wątkami i wydajnością dla wyrzucania elementów bezużytecznych serwera:

- Kolekcja odbywa się na wielu dedykowanych wątkach, które są uruchomione na poziomie priorytetu `THREAD_PRIORITY_HIGHEST`.

- Sterta i dedykowany wątek służący do wykonywania wyrzucania elementów bezużytecznych są udostępniane dla każdego procesora, a sterty są zbierane w tym samym czasie. Każda sterta zawiera niewielką stertę obiektu i stertę dużego obiektu, a wszystkie sterty są dostępne przez kod użytkownika. Obiekty na różnych stertach mogą odwoływać się do siebie nawzajem.

- Ponieważ wielokrotne wątki odzyskiwania pamięci współpracują ze sobą, wyrzucanie elementów bezużytecznych serwera jest szybsze niż wyrzucanie elementów bezużytecznych stacji roboczej.

- Wyrzucanie elementów bezużytecznych serwera często ma większe rozmiary segmentów. Należy jednak pamiętać, że jest to tylko Generalizacja: rozmiar segmentu jest specyficzny dla implementacji i może ulec zmianie. Nie należy wprowadzać żadnych założeń dotyczących rozmiaru segmentów przydzielonej przez moduł zbierający elementy bezużyteczne podczas dostrajania aplikacji.

- Zbieranie elementów bezużytecznych serwera może być czasochłonne. Na przykład jeśli masz 12 procesów uruchomionych na komputerze, który ma 4 procesory, będzie 48 dedykowane wątki wyrzucania elementów bezużytecznych, jeśli wszystkie używają wyrzucania elementów bezużytecznych serwera. W przypadku dużej ilości pamięci, jeśli wszystkie procesy uruchamiają wyrzucanie elementów bezużytecznych, Moduł wyrzucania elementów bezużytecznych będzie miał 48 wątków do zaplanowania.

Jeśli używasz setek wystąpień aplikacji, rozważ użycie wyrzucania elementów bezużytecznych stacji roboczej z wyłączonym współbieżnym wyrzucaniem elementów bezużytecznych. Spowoduje to przełączenie do mniej kontekstu, co może poprawić wydajność.

[Powrót do początku](#top)

<a name="concurrent_garbage_collection"></a>

## <a name="concurrent-garbage-collection"></a>Jednoczesne wyrzucanie elementów bezużytecznych

W systemie stacja robocza lub wyrzucanie elementów bezużytecznych serwera można włączyć współbieżne wyrzucanie elementów bezużytecznych, dzięki czemu wątki mogą działać równolegle z dedykowanym wątkiem, który wykonuje wyrzucanie elementów bezużytecznych przez większość czasu trwania kolekcji. Ta opcja ma wpływ tylko na wyrzucanie elementów bezużytecznych w generacji 2; generacji 0 i 1 są zawsze niewspółbieżne, ponieważ kończą się bardzo szybko.

Współbieżne wyrzucanie elementów bezużytecznych umożliwia lepsze reagowanie aplikacji interaktywnych przez zminimalizowanie przerw w kolekcji. Zarządzane wątki mogą nadal uruchamiać większość czasu, gdy wątek współbieżnego odzyskiwania pamięci jest uruchomiony. Powoduje to krótsze pauzy podczas wyrzucania elementów bezużytecznych.

Aby zwiększyć wydajność w przypadku uruchomienia kilku procesów, należy wyłączyć współbieżne wyrzucanie elementów bezużytecznych. Można to zrobić przez dodanie [elementu \<gcConcurrent >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) do pliku konfiguracji aplikacji i ustawienie wartości jego atrybutu `enabled` do `"false"`.

Współbieżne wyrzucanie elementów bezużytecznych jest wykonywane w ramach dedykowanego wątku. Domyślnie środowisko CLR uruchamia odzyskiwanie pamięci stacji roboczej z włączonym współbieżnym wyrzucaniem elementów bezużytecznych. Dotyczy to komputerów z pojedynczym procesorem i wieloprocesorem.

Możliwość przydzielenia małych obiektów na stercie podczas współbieżnego wyrzucania elementów bezużytecznych jest ograniczona przez obiekty pozostawione w segmencie tymczasowych podczas uruchamiania współbieżnego wyrzucania elementów bezużytecznych. Gdy tylko osiągniesz koniec segmentu, musisz poczekać na zakończenie równoczesnego wyrzucania elementów bezużytecznych, gdy zarządzane wątki, które muszą zapewnić alokacje małych obiektów, będą zawieszone.

Współbieżne wyrzucanie elementów bezużytecznych ma nieco większy zestaw roboczy (w porównaniu z niewspółbieżnym wyrzucaniem elementów bezużytecznych), ponieważ obiekty można przydzielić podczas współbieżnych kolekcji. Może to jednak mieć wpływ na wydajność, ponieważ obiekty przydzielone stają się częścią zestawu roboczego. Zasadniczo współbieżne wyrzucanie elementów bezużytecznych wymienia kilka procesorów i pamięci w celu skrócenia czasu wstrzymania.

Na poniższej ilustracji przedstawiono współbieżne wyrzucanie elementów bezużytecznych wykonywane w osobnym dedykowanym wątku.

Współbieżne wątki ![wyrzucania elementów bezużytecznych],(../../../docs/standard/garbage-collection/media/gc-concurrent.png "współbieżne odzyskiwanie pamięci")

[Powrót do początku](#top)

<a name="background_garbage_collection"></a>

## <a name="background-workstation-garbage-collection"></a>Wyrzucanie elementów bezużytecznych stacji roboczej

Wyrzucanie elementów bezużytecznych w tle zastępuje współbieżne wyrzucanie elementów bezużytecznych stacji roboczej, rozpoczynając od .NET Framework 4 i zastępuje współbieżne wyrzucanie elementów bez4,5 .NET Framework użytecznych serwera  W wyrzucaniu elementów bezużytecznych w tle generacje tymczasowe (0 i 1) są zbierane zgodnie z wymaganiami, gdy trwa zbieranie danych generacji 2. Jest wykonywane w ramach dedykowanego wątku i ma zastosowanie tylko do kolekcji generacji 2. Automatyczne wyrzucanie elementów bezużytecznych w tle jest domyślnie włączone i można je włączyć lub wyłączyć za pomocą ustawienia konfiguracji [> \<gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) w .NET Framework aplikacjach. 

> [!NOTE]
> Wyrzucanie elementów bezużytecznych w tle jest dostępne tylko w .NET Framework 4 i nowszych wersjach. W .NET Framework 4 jest obsługiwana tylko w przypadku wyrzucania elementów bezużytecznych stacji roboczej. Począwszy od .NET Framework 4,5, wyrzucanie elementów bezużytecznych w tle jest dostępne zarówno dla stacji roboczej, jak i serwera.

Kolekcja tymczasowych generacji podczas wyrzucania elementów bezużytecznych w tle jest znana jako wyrzucanie elementów bezużytecznych pierwszego planu. Gdy wystąpią wyrzucanie elementów bezużytecznych pierwszego planu, wszystkie zarządzane wątki są zawieszane.

Gdy wyrzucanie elementów bezużytecznych w tle jest w toku i przydzielono wystarczającą liczbę obiektów w generacji 0, środowisko CLR wykonuje wyrzucanie elementów bezużytecznych generacji 0 lub generacji 1. Nieznaczny wątek wyrzucania elementów bezużytecznych w tle sprawdza, czy występuje żądanie wyrzucania elementów bezużytecznych na pierwszym planie. Jeśli istnieje, kolekcja w tle zawiesza się tak, aby mogły wystąpić wyrzucanie elementów bezużytecznych na pierwszym planie. Po ukończeniu wyrzucania elementów bezużytecznych na pierwszym planie wątek i wątki użytkownika są wznawiane.

Wyrzucanie elementów bezużytecznych w tle usuwa ograniczenia alokacji narzucone przez współbieżne wyrzucanie elementów bezużytecznych, ponieważ tymczasowe wyrzucanie elementów bezużytecznych Oznacza to, że wyrzucanie elementów bezużytecznych w tle umożliwia usuwanie martwych obiektów z pokoleń tymczasowych i rozszerza stertę, jeśli jest to potrzebne podczas wyrzucania elementów bezużytecznych generacji 1.

Poniższa ilustracja przedstawia wyrzucanie elementów bezużytecznych w tle wykonywane w osobnym dedykowanym wątku na stacji roboczej:

![Diagram przedstawiający wyrzucanie elementów bezużytecznych stacji roboczej.](./media/fundamentals/background-workstation-garbage-collection.png "Diagram przedstawiający wyrzucanie elementów bezużytecznych stacji roboczej.")

[Powrót do początku](#top)

<a name="background_server_garbage_collection"></a>

## <a name="background-server-garbage-collection"></a>Odzyskiwanie pamięci serwera w tle

Począwszy od .NET Framework 4,5, wyrzucanie elementów bezużytecznych serwera w tle jest trybem domyślnym dla wyrzucania elementów bezużytecznych serwera. Aby wybrać ten tryb, ustaw atrybut `enabled` [> elementu \<gcServer](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) na `true` w schemacie konfiguracji środowiska uruchomieniowego. Ten tryb działa podobnie do wyrzucania elementów bezużytecznych stacji roboczej w tle, opisanych w poprzedniej sekcji, ale istnieje kilka różnic. Wyrzucanie elementów bezużytecznych stacji roboczej w tle używa jednego dedykowanego wątku wyrzucania elementów bezużytecznych w tle, natomiast wyrzucanie elementów bezużytecznych serwera w tle używa wielu wątków, zwykle W przeciwieństwie do wątku wyrzucania elementów bezużytecznych w tle stacji roboczej te wątki nie przekroczą limitu czasu.

Poniższa ilustracja przedstawia wyrzucanie elementów bezużytecznych w tle wykonywane w osobnym dedykowanym wątku na serwerze:

![Diagram przedstawiający wyrzucanie elementów bezużytecznych serwera w tle.](./media/fundamentals/background-server-garbage-collection.png "Diagram przedstawiający wyrzucanie elementów bezużytecznych serwera w tle.")

## <a name="see-also"></a>Zobacz także

- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
