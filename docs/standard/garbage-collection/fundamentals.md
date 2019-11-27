---
title: Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych
description: Dowiedz się, jak działa moduł zbierający elementy bezużyteczne i jak można go skonfigurować pod kątem optymalnej wydajności.
ms.date: 11/15/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- garbage collection, generations
- garbage collection, background
- garbage collection, concurrent
- garbage collection, server
- garbage collection, workstation
- garbage collection, managed heap
ms.assetid: 67c5a20d-1be1-4ea7-8a9a-92b0b08658d2
ms.openlocfilehash: ea8aef03d2f5837f35ecb31209e57853c0c8257b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330416"
---
# <a name="fundamentals-of-garbage-collection"></a>Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych

W środowisku uruchomieniowym języka wspólnego (CLR) Moduł wyrzucania elementów bezużytecznych (GC) służy jako automatyczny Menedżer pamięci. Zapewnia następujące korzyści:

- Umożliwia tworzenie aplikacji bez konieczności ręcznego zwalniania pamięci.

- Efektywnie przydziela obiekty na stosie zarządzanym.

- Reoświadczenia obiektów, które nie są już używane, czyści ich pamięć i utrzymuje dostępną pamięć do przyszłych alokacji. Obiekty zarządzane automatycznie pobierają czystą zawartość do początku, więc ich konstruktory nie muszą inicjować każdego pola danych.

- Zapewnia bezpieczeństwo pamięci, upewniając się, że obiekt nie może użyć zawartości innego obiektu.

W tym artykule opisano podstawowe pojęcia dotyczące wyrzucania elementów bezużytecznych.

## <a name="fundamentals-of-memory"></a>Podstawowe informacje o pamięci

Poniższa lista zawiera podsumowanie ważnych pojęć dotyczących pamięci środowiska CLR.

- Każdy proces ma własną, oddzielną wirtualną przestrzeń adresową. Wszystkie procesy na tym samym komputerze współużytkują tę samą pamięć fizyczną i plik stronicowania, jeśli istnieje.

- Domyślnie na komputerach 32-bitowych każdy proces ma 2 GB wirtualnej przestrzeni adresowej w trybie użytkownika.

- Jako deweloper aplikacji pracujesz tylko z wirtualną przestrzenią adresową i nigdy nie manipulujesz bezpośrednio pamięci fizycznej. Moduł wyrzucania elementów bezużytecznych przydziela i zwalnia pamięć wirtualną na zarządzanym stosie.

  Jeśli piszesz kod natywny, używasz funkcji systemu Windows do pracy z wirtualną przestrzenią adresową. Te funkcje przydzielą i zwalniają pamięć wirtualną na stertach natywnych.

- Pamięć wirtualna może mieć trzy stany:

  - Zwolniony. Blok pamięci nie ma odwołań do niego i jest dostępny do alokacji.

  - Rezerwacj. Blok pamięci jest dostępny do użycia i nie może być używany w żadnym innym żądaniu alokacji. Nie można jednak przechowywać danych w tym bloku pamięci, dopóki nie zostanie on zatwierdzony.

  - Prowadzono. Blok pamięci jest przypisany do magazynu fizycznego.

- Wirtualne przestrzenie adresowe mogą zostać pofragmentowane. Oznacza to, że w przestrzeni adresowej istnieją wolne bloki, znane także jako otwory. Po zażądaniu alokacji pamięci wirtualnej Menedżer pamięci wirtualnej musi znaleźć pojedynczy bezpłatny blok, który jest wystarczająco duży, aby spełnić to żądanie alokacji. Nawet jeśli masz 2 GB wolnego miejsca, alokacja, która wymaga 2 GB, nie powiedzie się, chyba że wszystkie te wolne miejsca znajdują się w jednym bloku adresów.

- Jeśli nie ma wystarczającej ilości wirtualnej przestrzeni adresowej do zarezerwowania lub miejsca fizycznego do zatwierdzenia, można wypróbować za mało pamięci.

  Plik stronicowania jest używany nawet w przypadku niskiej ilości pamięci fizycznej (to jest zapotrzebowanie na ilość pamięci fizycznej). Pierwszy raz, gdy wykorzystanie pamięci fizycznej jest wysokie, system operacyjny musi zwolnić miejsce w pamięci fizycznej do przechowywania danych, a następnie tworzy kopię zapasową niektórych danych znajdujących się w pamięci fizycznej do pliku stronicowania. Te dane nie są stronicowane, dopóki nie jest to konieczne, więc można napotkać stronicowanie w sytuacjach, gdy wykorzystanie pamięci fizycznej jest niskie.

## <a name="conditions-for-a-garbage-collection"></a>Warunki dla wyrzucania elementów bezużytecznych

Odzyskiwanie pamięci występuje, gdy spełniony jest jeden z następujących warunków:

- System ma małą ilość pamięci fizycznej. Jest on wykrywany przez powiadomienie o niskim poziomie z systemu operacyjnego lub z niską ilością pamięci, jak wskazano na hoście.

- Pamięć używana przez przydzielone obiekty na zarządzanej stercie przekracza akceptowalny próg. Ten próg jest ciągle dostosowywany podczas uruchamiania procesu.

- Metoda <xref:System.GC.Collect%2A?displayProperty=nameWithType> jest wywoływana. W prawie wszystkich przypadkach nie trzeba wywoływać tej metody, ponieważ moduł wyrzucania elementów bezużytecznych działa w sposób ciągły. Ta metoda jest używana głównie do unikatowych sytuacji i testowania.

## <a name="the-managed-heap"></a>Zarządzane sterty

Po zainicjowaniu modułu wyrzucania elementów bezużytecznych przez środowisko CLR przydziela on segment pamięci do przechowywania obiektów i zarządzania nimi. Ta pamięć jest nazywana stertą zarządzaną, w przeciwieństwie do sterty natywnej w systemie operacyjnym.

Istnieje sterta zarządzana dla każdego procesu zarządzanego. Wszystkie wątki w procesie przydzielają pamięć dla obiektów na tym samym stosie.

W celu zarezerwowania pamięci moduł zbierający elementy bezużyteczne wywołuje funkcję [Funkcja VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) systemu Windows i rezerwuje jeden segment pamięci w czasie dla aplikacji zarządzanych. Moduł wyrzucania elementów bezużytecznych rezerwuje również segmenty, a następnie zwalnia segmenty z powrotem do systemu operacyjnego (po wyczyszczeniu ich z dowolnego obiektu), wywołując funkcję [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) systemu Windows.

> [!IMPORTANT]
> Rozmiar segmentów przydzielone przez moduł wyrzucania elementów bezużytecznych jest specyficzny dla implementacji i może ulec zmianie w dowolnym momencie, łącznie z okresowymi aktualizacjami. Aplikacja nigdy nie powinna mieć założeń lub zależeć od określonego rozmiaru segmentu ani nie powinna próbować skonfigurować ilości pamięci dostępnej dla alokacji segmentu.

Im mniejsza liczba obiektów przypadających na stosie, tym mniejsza ilość pracy do wykonania przez moduł zbierający elementy bezużyteczne. W przypadku przydzielania obiektów nie należy używać wartości zaokrąglonych, które przekraczają Twoje potrzeby, na przykład przydzielając tablicę 32 bajtów, gdy potrzebne są tylko 15 bajtów.

Po wyzwoleniu wyrzucania elementów bezużytecznych moduł zbierający elementy bezużyteczne odzyskuje pamięć, która jest zajęta przez obiekty martwe. Proces odzyskiwania kompaktuje obiekty na żywo, dzięki czemu są one przenoszone razem, a wolne miejsce zostaje usunięte, co sprawia, że sterta jest mniejsza. Dzięki temu obiekty, które są przydzielane razem, pozostają razem na zarządzanym stosie, aby zachować ich miejscowość.

Nietrwałość (częstotliwość i czas trwania) wyrzucania elementów bezużytecznych to wynik ilości alokacji i ilości pamięci przeprowadzonej w zarządzanym stosie.

Sterta może być traktowana jako akumulacja dwóch stert: [sterty dużych obiektów](large-object-heap.md) i sterty małego obiektu.

[Sterta dużego obiektu](large-object-heap.md) zawiera bardzo duże obiekty, które są 85 000 bajtów i większych. Obiekty na stosie dużego obiektu są zazwyczaj tablicami. Wystąpienie obiektu wystąpienia jest rzadkim zdarzeniem bardzo duże.

> [!TIP]
> Można [skonfigurować rozmiar progu](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) obiektów do przechodzenia do sterty dużego obiektu.

## <a name="generations"></a>Generacje

Stos jest zorganizowany do generacji, aby mógł obsługiwać długotrwałe i krótkotrwałe obiekty. Wyrzucanie elementów bezużytecznych odbywa się głównie z odzyskiwaniem obiektów krótkoterminowych, które zwykle zajmują tylko małą część sterty. Na stercie znajdują się trzy generacje obiektów:

- **Generacja 0**. Jest to najmłodsze generowanie i zawiera obiekty krótkotrwałe. Przykładem obiektu krótkotrwałego jest zmienna tymczasowa. Wyrzucanie elementów bezużytecznych występuje najczęściej w tej generacji.

  Nowo przydzielono obiekty tworzą nową generację obiektów i są kolekcjami niejawnie generacji 0. Jednak jeśli są to duże obiekty, przechodzą na stertę dużego obiektu w kolekcji generacji 2.

  Większość obiektów jest odzyskiwana do wyrzucania elementów bezużytecznych w generacji 0 i nie przechodzenia do nowej generacji.

- **Generacja 1**. Ta generacja zawiera obiekty krótkoterminowe i służy jako bufor między obiektami krótko-i długotrwałymi.

- **Generacja 2**. Ta generacja zawiera obiekty długotrwałe. Przykładem obiektu długotrwałego jest obiekt w aplikacji serwera, który zawiera dane statyczne, które są przechowywane na czas trwania procesu.

Wyrzucanie elementów bezużytecznych odbywa się w określonych generacjach, gdy jest to warunki Zbieranie generacji oznacza gromadzenie obiektów w tej generacji i wszystkich jej młodszych generacjach. Wyrzucanie elementów bezużytecznych generacji 2 jest również znane jako pełne wyrzucanie elementów bezużytecznych, ponieważ przejmuje wszystkie obiekty we wszystkich generacjach (czyli wszystkie obiekty w stercie zarządzanym).

### <a name="survival-and-promotions"></a>Przeżycia i promocja

Obiekty, które nie są odzyskiwane w wyrzucaniu elementów bezużytecznych, są znane jako osoby do wygenerowania i są promowane do nowej generacji. Obiekty, które przeżyły wyrzucanie elementów bezużytecznych generacji 0, zostały podwyższone do generacji 1; obiekty, które przeżyły wyrzucanie elementów bezużytecznych generacji 1, są podwyższane do generacji 2; i obiekty, które przeżyły wyrzucanie elementów bezużytecznych generacji 2, pozostają w generacji 2.

Gdy moduł wyrzucania elementów bezużytecznych wykryje, że stopień przeżycia jest wysoki w generacji, zwiększa próg alokacji dla tej generacji. Następna kolekcja pobiera znaczny rozmiar odzyskiwanej pamięci. Środowisko CLR ciągle równoważy dwa priorytety: nie pozwala to na zbyt duże działanie zestawu roboczego aplikacji przez opóźnione wyrzucanie elementów bezużytecznych i niezezwalanie na zbyt częste uruchamianie wyrzucania elementów bezużytecznych.

### <a name="ephemeral-generations-and-segments"></a>Pokoleń tymczasowych i segmentów

Ponieważ obiekty w generacji 0 i 1 są krótkoterminowe, te generacje są znane jako generacja tymczasowych.

Pokoleń tymczasowych należy przydzielić w segmencie pamięci, który jest znany jako segment tymczasowych. Każdy nowy segment uzyskany przez moduł wyrzucania elementów bezużytecznych stał się nowym segmentem tymczasowych i zawiera obiekty, które przeżyły wyrzucanie elementów bezużytecznych generacji 0. Stary segment tymczasowych zostanie segmentem nowej generacji 2.

Rozmiar segmentu tymczasowych różni się w zależności od tego, czy system jest 32-bitowy czy 64-bitowy, i na typie modułu wyrzucania elementów bezużytecznych, który jest uruchomiony. Wartości domyślne są pokazane w poniższej tabeli.

||32-bitowa|64-bitowy|
|-|-------------|-------------|
|Stacja robocza GC|16 MB|256 MB|
|Serwer GC|64 MB|4 GB|
|Serwer GC z procesorami logicznymi > 4|32 MB|2 GB|
|Serwer GC z > 8 procesorami logicznymi|16 MB|1 GB|

Segment tymczasowych może obejmować obiekty generacji 2. Obiekty generacji 2 mogą korzystać z wielu segmentów (tyle, ile wymaga proces i czy pamięć zezwala na system).

Ilość zwolnionej pamięci z tymczasowego wyrzucania elementów bezużytecznych jest ograniczona do rozmiaru segmentu tymczasowych. Ilość wolnej pamięci jest proporcjonalna do miejsca, które było zajęte przez obiekty martwe.

## <a name="what-happens-during-a-garbage-collection"></a>Co się dzieje podczas wyrzucania elementów bezużytecznych

Wyrzucanie elementów bezużytecznych ma następujące fazy:

- Faza oznaczania, która wyszukuje i tworzy listę wszystkich obiektów na żywo.

- Faza zmiany lokalizacji, która aktualizuje odwołania do obiektów, które zostaną skompaktowane.

- Faza kompaktowania, która odzyskuje miejsce zajęte przez obiekty martwe i kompaktuje pozostałe obiekty. Faza kompaktowania przenosi obiekty, które przeżyły wyrzucanie elementów bezużytecznych do starszych końców segmentu.

  Ponieważ kolekcje generacji 2 mogą zajmować wiele segmentów, obiekty, które są promowane do generacji 2 można przenieść do starszego segmentu. Zarówno osoby przestające 1, jak i 2 mogą zostać przeniesione do innego segmentu, ponieważ są one podwyższane do generacji 2.

  Zwykle sterta dużego obiektu (LOH) nie jest kompaktowa, ponieważ kopiowanie dużych obiektów nakłada spadek wydajności. Jednak w oprogramowaniu .NET Core i w .NET Framework 4.5.1 i nowszych można użyć właściwości <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>, aby skompaktować stertę dużego obiektu na żądanie. Ponadto LOH jest automatycznie kompaktowana, gdy ustalono limit, określając jedną z:

  - limit pamięci dla kontenera lub
  - Opcje konfiguracji [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) lub [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) w czasie wykonywania

Moduł wyrzucania elementów bezużytecznych używa następujących informacji, aby określić, czy obiekty są aktywne:

- Elementy **Główne stosu**. Zmienne stosu udostępniane przez kompilator just-in-Time (JIT) i Analizator stosu. Optymalizacje JIT mogą wydłużać lub skracać regiony kodu, w których zmienne stosu są zgłaszane do modułu wyrzucania elementów bezużytecznych.

- **Dojść do wyrzucania elementów bezużytecznych**. Obsługuje obiekty zarządzane, które mogą być przydzielone przez kod użytkownika lub przez środowisko uruchomieniowe języka wspólnego.

- **Dane statyczne**. Obiekty statyczne w domenach aplikacji, które mogą odwoływać się do innych obiektów. Każda domena aplikacji śledzi swoje obiekty statyczne.

Przed uruchomieniem odzyskiwania pamięci wszystkie zarządzane wątki są zawieszane z wyjątkiem wątku, który wyzwolił wyrzucanie elementów bezużytecznych.

Na poniższej ilustracji przedstawiono wątek wyzwalający wyrzucanie elementów bezużytecznych i powoduje zawieszenie innych wątków.

![Gdy wątek wyzwala odzyskiwanie pamięci](./media/gc-triggered.png)

## <a name="manipulate-unmanaged-resources"></a>Manipulowanie niezarządzanymi zasobami

Jeśli obiekty zarządzane odwołują się do obiektów niezarządzanych przy użyciu ich natywnych uchwytów plików, należy jawnie zwolnić obiekty niezarządzane, ponieważ moduł wyrzucania elementów bezużytecznych śledzi pamięć tylko na stosie zarządzanym.

Użytkownicy obiektu zarządzanego nie mogą zlikwidować zasobów natywnych używanych przez obiekt. Aby przeprowadzić oczyszczanie, można sprawić, aby obiekt zarządzany został sfinalizowany. Finalizowanie składa się z akcji oczyszczania, które są wykonywane, gdy obiekt nie jest już używany. Gdy zarządzany obiekt jest realizowany, wykonuje akcje oczyszczania, które są określone w jego metodzie finalizatora.

Gdy odnaleziony obiekt jest niemartwy, jego finalizator jest umieszczany w kolejce, aby zostały wykonane akcje oczyszczania, ale sam obiekt zostanie podwyższony do nowej generacji. W związku z tym należy poczekać na następne wyrzucanie elementów bezużytecznych w tej generacji (co nie musi być następną kolekcją elementów bezużytecznych), aby określić, czy obiekt został odrzucony.

Aby uzyskać więcej informacji na temat finalizacji, zobacz <xref:System.Object.Finalize?displayProperty=nameWithType>.

## <a name="workstation-and-server-garbage-collection"></a>Stacja robocza i odzyskiwanie pamięci serwera

Moduł wyrzucania elementów bezużytecznych jest samodostrajania i może współpracować w wielu różnych scenariuszach. Możesz użyć [Ustawienia pliku konfiguracji](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) , aby ustawić typ wyrzucania elementów bezużytecznych na podstawie charakterystyki obciążenia. Środowisko CLR udostępnia następujące typy wyrzucania elementów bezużytecznych:

- Wyrzucanie elementów bezużytecznych stacji roboczej jest przeznaczone dla aplikacji klienckich. Jest to domyślna wersja GC dla aplikacji autonomicznych. Na przykład w przypadku aplikacji hostowanych przez ASP.NET host Określa domyślną wersję GC.

  Wyrzucanie elementów bezużytecznych stacji roboczej może być współbieżne lub niewspółbieżne. Współbieżne wyrzucanie elementów bezużytecznych umożliwia zarządzanym wątkom kontynuowanie operacji podczas odzyskiwania pamięci. [Wyrzucanie elementów bezużytecznych w tle](#background-workstation-garbage-collection) zastępuje [współbieżne odzyskiwanie pamięci](#concurrent-garbage-collection) w .NET Framework 4 i nowszych wersjach.

- Odzyskiwanie pamięci serwera, które jest przeznaczone dla aplikacji serwerowych, które potrzebują dużej przepływności i skalowalności.

  - W programie .NET Core zbieranie elementów bezużytecznych serwera może być niewspółbieżne lub niezgodne.

  - W .NET Framework 4,5 i nowszych wersjach wyrzucanie elementów bezużytecznych serwera może być niewspółbieżne lub w tle (wyrzucanie elementów bezużytecznych w tle zastępuje współbieżne odzyskiwanie pamięci). W .NET Framework 4 i poprzednich wersjach zbieranie elementów bezużytecznych serwera nie jest współbieżne.

Na poniższej ilustracji przedstawiono dedykowane wątki, które wykonują wyrzucanie elementów bezużytecznych na serwerze:

![Wątki odzyskiwania pamięci serwera](./media/gc-server.png)

### <a name="compare-workstation-and-server-garbage-collection"></a>Porównanie stacji roboczej i wyrzucania elementów bezużytecznych serwera

Poniżej przedstawiono zagadnienia dotyczące wątkowości i wydajności dotyczące wyrzucania elementów bezużytecznych stacji roboczej:

- Kolekcja odbywa się w wątku użytkownika, który wyzwolił wyrzucanie elementów bezużytecznych i pozostaje na tym samym priorytecie. Ponieważ wątki użytkownika zwykle działają przy normalnym priorytecie, Moduł wyrzucania elementów bezużytecznych (który jest uruchamiany w wątku o normalnym priorytecie) musi konkurować z innymi wątkami czasu procesora CPU. (Wątki, które uruchamiają kod natywny nie są zawieszone na serwerze lub w wyrzucaniu elementów bezużytecznych stacji roboczych).

- Wyrzucanie elementów bezużytecznych stacji roboczej jest zawsze używane na komputerze z tylko jednym procesorem, niezależnie od [Ustawienia konfiguracji](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

Poniżej przedstawiono zagadnienia związane z wątkami i wydajnością dla wyrzucania elementów bezużytecznych serwera:

- Kolekcja odbywa się na wielu dedykowanych wątkach, które są uruchomione na poziomie priorytetu `THREAD_PRIORITY_HIGHEST`.

- Sterta i dedykowany wątek służący do wykonywania wyrzucania elementów bezużytecznych są udostępniane dla każdego procesora, a sterty są zbierane w tym samym czasie. Każda sterta zawiera niewielką stertę obiektu i stertę dużego obiektu, a wszystkie sterty są dostępne przez kod użytkownika. Obiekty na różnych stertach mogą odwoływać się do siebie nawzajem.

- Ponieważ wielokrotne wątki odzyskiwania pamięci współpracują ze sobą, wyrzucanie elementów bezużytecznych serwera jest szybsze niż wyrzucanie elementów bezużytecznych stacji roboczej.

- Wyrzucanie elementów bezużytecznych serwera często ma większe rozmiary segmentów. Jest to jednak tylko Generalizacja: rozmiar segmentu jest specyficzny dla implementacji i może ulec zmianie. Nie należy tworzyć założeń dotyczących rozmiaru segmentów przydzielonej przez moduł zbierający elementy bezużyteczne podczas dostrajania aplikacji.

- Zbieranie elementów bezużytecznych serwera może być czasochłonne. Załóżmy na przykład, że istnieją 12 procesów korzystających z serwera GC uruchomionego na komputerze, który ma 4 procesory. Jeśli wszystkie procesy mają w tym samym czasie zbierać elementy bezużyteczne, mogą one zakłócać sobie nawzajem, ponieważ na tym samym procesorze zaplanowano 12 wątków. Jeśli procesy są aktywne, nie jest dobrym pomysłem na korzystanie z serwera GC.

Jeśli używasz setek wystąpień aplikacji, rozważ użycie wyrzucania elementów bezużytecznych stacji roboczej z wyłączonym współbieżnym wyrzucaniem elementów bezużytecznych. Spowoduje to przełączenie do mniej kontekstu, co może poprawić wydajność.

## <a name="background-workstation-garbage-collection"></a>Wyrzucanie elementów bezużytecznych stacji roboczej

W tle wyrzucanie elementów bezużytecznych, generacja tymczasowych (0 i 1) są zbierane zgodnie z wymaganiami, gdy trwa zbieranie danych generacji 2. Wyrzucanie elementów bezużytecznych stacji roboczej w tle jest wykonywane w ramach dedykowanego wątku i ma zastosowanie tylko do kolekcji generacji 2.

Wyrzucanie elementów bezużytecznych w tle jest domyślnie włączone i można je włączyć lub wyłączyć za pomocą ustawienia konfiguracji [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) w aplikacjach .NET Framework lub ustawienia [System. GC. współbieżne](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) w aplikacjach .NET Core.

> [!NOTE]
> Wyrzucanie elementów bezużytecznych w tle zastępuje [współbieżne odzyskiwanie pamięci](#concurrent-garbage-collection) i jest dostępne w .NET Framework 4 i nowszych wersjach. W .NET Framework 4 jest obsługiwana tylko dla wyrzucania elementów bezużytecznych stacji roboczej. Począwszy od .NET Framework 4,5, wyrzucanie elementów bezużytecznych w tle jest dostępne zarówno dla stacji roboczej, jak i serwera.

Kolekcja tymczasowych generacji podczas wyrzucania elementów bezużytecznych w tle jest znana jako wyrzucanie elementów bezużytecznych pierwszego planu. Gdy wystąpią wyrzucanie elementów bezużytecznych pierwszego planu, wszystkie zarządzane wątki są zawieszane.

Gdy wyrzucanie elementów bezużytecznych w tle jest w toku i przydzielono wystarczającą liczbę obiektów w generacji 0, środowisko CLR wykonuje wyrzucanie elementów bezużytecznych generacji 0 lub generacji 1. Nieznaczny wątek wyrzucania elementów bezużytecznych w tle sprawdza, czy występuje żądanie wyrzucania elementów bezużytecznych na pierwszym planie. Jeśli istnieje, kolekcja w tle zawiesza się tak, aby mogły wystąpić wyrzucanie elementów bezużytecznych na pierwszym planie. Po ukończeniu wyrzucania elementów bezużytecznych na pierwszym planie wątek i wątki użytkownika są wznawiane.

Wyrzucanie elementów bezużytecznych w tle usuwa ograniczenia alokacji narzucone przez współbieżne wyrzucanie elementów bezużytecznych, ponieważ tymczasowe wyrzucanie elementów bezużytecznych Wyrzucanie elementów bezużytecznych w tle umożliwia usuwanie martwych obiektów z generacji tymczasowych. Można również rozszerzyć stertę, jeśli jest to konieczne podczas wyrzucania elementów bezużytecznych generacji 1.

Poniższa ilustracja przedstawia wyrzucanie elementów bezużytecznych w tle wykonywane w osobnym dedykowanym wątku na stacji roboczej:

![Wyrzucanie elementów bezużytecznych stacji roboczej](./media/fundamentals/background-workstation-garbage-collection.png)

### <a name="background-server-garbage-collection"></a>Odzyskiwanie pamięci serwera w tle

Począwszy od .NET Framework 4,5, odzyskiwanie pamięci serwera w tle jest domyślnym trybem do wyrzucania elementów bezużytecznych serwera.

Odzyskiwanie pamięci serwera w tle działa podobnie do wyrzucania elementów bezużytecznych stacji roboczej w tle, opisanych w poprzedniej sekcji, ale istnieją pewne różnice:

- Wyrzucanie elementów bezużytecznych stacji roboczej w tle używa jednego dedykowanego wątku wyrzucania elementów bezużytecznych w tle, podczas gdy odzyskiwanie pamięci serwera Zwykle istnieje dedykowany wątek dla każdego procesora logicznego.

- W przeciwieństwie do wątku wyrzucania elementów bezużytecznych w tle stacji roboczej te wątki nie przekroczą limitu czasu.

Poniższa ilustracja przedstawia wyrzucanie elementów bezużytecznych w tle wykonywane w osobnym dedykowanym wątku na serwerze:

![Odzyskiwanie pamięci serwera w tle](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Jednoczesne wyrzucanie elementów bezużytecznych

> [!TIP]
> Ta sekcja ma zastosowanie do:
>
> - .NET Framework 3,5 i wcześniejszy dla wyrzucania elementów bezużytecznych stacji roboczych
> - .NET Framework 4 i starsze do wyrzucania elementów bezużytecznych serwera
>
> Współbieżne elementy bezużyteczne są zastępowane przez [odzyskiwanie pamięci w tle](#background-workstation-garbage-collection) w nowszych wersjach.

W systemie stacja robocza lub wyrzucanie elementów bezużytecznych serwera można [włączyć współbieżne wyrzucanie elementów bezużytecznych](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), dzięki czemu wątki mogą działać równolegle z dedykowanym wątkiem, który wykonuje wyrzucanie elementów bezużytecznych przez większość czasu trwania kolekcji. Ta opcja ma wpływ tylko na wyrzucanie elementów bezużytecznych w generacji 2; generacji 0 i 1 są zawsze niewspółbieżne, ponieważ kończą się bardzo szybko.

Współbieżne wyrzucanie elementów bezużytecznych umożliwia lepsze reagowanie aplikacji interaktywnych przez zminimalizowanie przerw w kolekcji. Zarządzane wątki mogą nadal uruchamiać większość czasu, gdy wątek współbieżnego odzyskiwania pamięci jest uruchomiony. Powoduje to krótsze pauzy podczas wyrzucania elementów bezużytecznych.

Współbieżne wyrzucanie elementów bezużytecznych jest wykonywane w ramach dedykowanego wątku. Domyślnie środowisko CLR uruchamia odzyskiwanie pamięci stacji roboczej z włączonym współbieżnym wyrzucaniem elementów bezużytecznych. Dotyczy to komputerów z pojedynczym procesorem i wieloprocesorem.

Na poniższej ilustracji przedstawiono współbieżne wyrzucanie elementów bezużytecznych wykonywane w osobnym dedykowanym wątku.

![Współbieżne wątki odzyskiwania pamięci](./media/gc-concurrent.png)

## <a name="see-also"></a>Zobacz także

- [Opcje konfiguracji dla usługi GC](../../core/run-time-config/garbage-collector.md)
- [Odzyskiwanie pamięci](index.md)
