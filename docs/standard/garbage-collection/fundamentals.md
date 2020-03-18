---
title: Podstawy wyrzucania śmieci
description: Dowiedz się, jak działa moduł zbierający elementy bezużyteczne i jak można go skonfigurować w celu uzyskania optymalnej wydajności.
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400541"
---
# <a name="fundamentals-of-garbage-collection"></a>Podstawy wyrzucania śmieci

W czasie wykonywania języka wspólnego (CLR), moduł zbierający elementy bezużyteczne (GC) służy jako automatyczny menedżer pamięci. Zapewnia następujące korzyści:

- Umożliwia tworzenie aplikacji bez konieczności ręcznego zwalniania pamięci.

- Przydziela obiekty na zarządzanym stercie wydajnie.

- Odzyskuje obiekty, które nie są już używane, czyści ich pamięci i przechowuje pamięć dostępną dla przyszłych alokacji. Zarządzane obiekty automatycznie uzyskać czystą zawartość na początek, więc ich konstruktory nie trzeba inicjować każde pole danych.

- Zapewnia bezpieczeństwo pamięci, upewniając się, że obiekt nie może używać zawartości innego obiektu.

W tym artykule opisano podstawowe pojęcia wyrzucania elementów bezużytecznych.

## <a name="fundamentals-of-memory"></a>Podstawy pamięci

Poniższa lista zawiera podsumowanie ważnych pojęć pamięci CLR.

- Każdy proces ma własną, oddzielną wirtualną przestrzeń adresową. Wszystkie procesy na tym samym komputerze mają tę samą pamięć fizyczną i plik strony, jeśli taki istnieje.

- Domyślnie na komputerach 32-bitowych każdy proces ma wirtualną przestrzeń adresową w trybie użytkownika o pojemności 2 GB.

- Jako deweloper aplikacji pracujesz tylko z wirtualną przestrzenią adresową i nigdy nie manipulujesz bezpośrednio pamięcią fizyczną. Moduł zbierający elementy bezużyteczne przydziela i zwalnia pamięć wirtualną na zarządzanym stercie.

  Jeśli piszesz kod macierzysty, używasz funkcji systemu Windows do pracy z wirtualną przestrzenią adresową. Te funkcje przydzielają i zwalniają pamięć wirtualną na rodzimych stertach.

- Pamięć wirtualna może być w trzech stanach:

  - Wolna. Blok pamięci nie ma odwołań do niego i jest dostępny do alokacji.

  - Zarezerwowany. Blok pamięci jest dostępny do użytku i nie może być używany dla żadnego innego żądania alokacji. Jednak nie można przechowywać danych do tego bloku pamięci, dopóki nie zostanie zatwierdzona.

  - Popełnione. Blok pamięci jest przypisany do pamięci fizycznej.

- Wirtualna przestrzeń adresowa może zostać pofragmentowana. Oznacza to, że w przestrzeni adresowej znajdują się wolne bloki, znane również jako dziury. Gdy zażądana jest alokacja pamięci wirtualnej, menedżer pamięci wirtualnej musi znaleźć pojedynczy wolny blok, który jest wystarczająco duży, aby spełnić to żądanie alokacji. Nawet jeśli masz 2 GB wolnego miejsca, alokacja, która wymaga 2 GB, zakończy się niepowodzeniem, chyba że całe wolne miejsce znajduje się w jednym bloku adresów.

- Możesz zabraknąć pamięci, jeśli nie ma wystarczającej ilości wirtualnej przestrzeni adresowej do zarezerwowania lub fizycznej przestrzeni do zatwierdzenia.

  Plik strony jest używany, nawet jeśli ciśnienie pamięci fizycznej (czyli zapotrzebowanie na pamięć fizyczną) jest niskie. Po raz pierwszy ciśnienie pamięci fizycznej jest wysoka, system operacyjny musi zrobić miejsce w pamięci fizycznej do przechowywania danych i tworzenia tworzenia archiwizacji niektórych danych, które znajduje się w pamięci fizycznej do pliku strony. Te dane nie są stronicowane, dopóki nie są potrzebne, więc można napotkać stronicowania w sytuacjach, gdy ciśnienie pamięci fizycznej jest niski.

## <a name="conditions-for-a-garbage-collection"></a>Warunki wyrzucania elementów bezużytecznych

Wyrzucanie elementów bezużytecznych występuje, gdy spełniony jest jeden z następujących warunków:

- System ma małą pamięć fizyczną. Jest to wykrywane przez powiadomienie o małej ilości pamięci z os lub małej ilości pamięci wskazane przez hosta.

- Pamięć używana przez przydzielone obiekty na zarządzanym stercie przekracza dopuszczalny próg. Ten próg jest stale dostosowywany podczas procesu.

- Metoda <xref:System.GC.Collect%2A?displayProperty=nameWithType> jest wywoływana. W prawie wszystkich przypadkach nie trzeba wywołać tej metody, ponieważ moduł zbierający elementy bezużyteczne działa w sposób ciągły. Ta metoda jest używana głównie w sytuacjach unikatowych i testowania.

## <a name="the-managed-heap"></a>Zarządzana sterta

Po zainicjowaniu modułu odśmiecania pamięci przez program CLR przydziela segment pamięci do przechowywania obiektów i zarządzania nimi. Ta pamięć jest nazywana stertą zarządzaną, w przeciwieństwie do natywnej sterty w systemie operacyjnym.

Dla każdego zarządzanego procesu istnieje sterta zarządzana. Wszystkie wątki w procesie przydziel alokacji pamięci dla obiektów na tej samej stercie.

Aby zarezerwować pamięć, moduł zbierający elementy bezużyteczne wywołuje funkcję [Windows VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) i rezerwuje jeden segment pamięci naraz dla aplikacji zarządzanych. Moduł zbierający elementy bezużyteczne rezerwuje również segmenty, w razie potrzeby, i zwalnia segmenty z powrotem do systemu operacyjnego (po wyczyszczeniu ich z jakichkolwiek obiektów), wywołując funkcję [Windows VirtualFree.](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree)

> [!IMPORTANT]
> Rozmiar segmentów przydzielonych przez moduł odśmiecania pamięci jest specyficzne dla implementacji i może ulec zmianie w dowolnym momencie, w tym w okresowych aktualizacji. Aplikacja nigdy nie należy zakładać o lub zależy od określonego rozmiaru segmentu, ani nie należy próbować skonfigurować ilość pamięci dostępnej dla alokacji segmentów.

Im mniej obiektów przydzielonych na stercie, tym mniej pracy ma moduł zbierający elementy bezużyteczne. Podczas przydzielania obiektów nie należy używać zaokrąglonych wartości, które przekraczają twoje potrzeby, takich jak przydzielanie tablicy 32 bajtów, gdy potrzebujesz tylko 15 bajtów.

Po wyzwoleniu wyrzucania elementów bezużytecznych moduł zbierający elementy bezużyteczne odzyskuje pamięć zajmowaną przez martwe obiekty. Proces odzyskiwania kompaktuje obiekty aktywne tak, że są one przenoszone razem, a martwa przestrzeń jest usuwana, co zmniejsza stertę. Dzięki temu obiekty, które są przydzielane razem pozostają razem na zarządzanym stercie, aby zachować ich lokalizację.

Natrętność (częstotliwość i czas trwania) wyrzucania elementów bezużytecznych jest wynikiem objętości alokacji i ilości pamięci przetrwania na zarządzanym stercie.

Sterty można uznać za nagromadzenie dwóch stert: [sterty dużego obiektu](large-object-heap.md) i sterty małego obiektu.

Sterta [dużych obiektów](large-object-heap.md) zawiera bardzo duże obiekty, które są 85.000 bajtów i większe. Obiekty na stercie dużych obiektów są zwykle tablice. Rzadko jest obiekt wystąpienia jest bardzo duży.

> [!TIP]
> Można [skonfigurować rozmiar progu](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) dla obiektów, aby przejść na stercie dużego obiektu.

## <a name="generations"></a>Pokoleń

Sterta jest zorganizowana w pokolenia, dzięki czemu może obsługiwać obiekty długotrwałe i krótkotrwałe. Wyrzucanie elementów bezużytecznych występuje głównie z rekultywacji krótkotrwałych obiektów, które zazwyczaj zajmują tylko niewielką część sterty. Istnieją trzy generacje obiektów na stercie:

- **Generacja 0**. Jest to najmłodsze pokolenie i zawiera krótkotrwałe przedmioty. Przykładem krótkotrwałego obiektu jest zmienna tymczasowa. Wyrzucanie elementów bezużytecznych występuje najczęściej w tej generacji.

  Nowo przydzielone obiekty tworzą nową generację obiektów i są niejawnie generacji 0 kolekcji. Jednak jeśli są one duże obiekty, idą na stercie dużych obiektów w kolekcji generacji 2.

  Większość obiektów są odzyskiwane do wyrzucania elementów bezużytecznych w generacji 0 i nie przetrwać do następnej generacji.

- **Generacja 1**. Ta generacja zawiera obiekty krótkotrwałe i służy jako bufor między krótkotrwałymi obiektami i długowiecznymi obiektami.

- **Generacja 2**. Ta generacja zawiera obiekty długowieczne. Przykładem obiektu długotrwałego jest obiekt w aplikacji serwera, który zawiera dane statyczne, które są aktywne przez czas trwania procesu.

Wyrzucanie elementów bezużytecznych występują w określonych generacjach, zgodnie z warunkami. Zbieranie pokolenia oznacza zbieranie przedmiotów w tym pokoleniu i wszystkich jego młodszych pokoleniach. Kolekcja elementów bezużytecznych generacji 2 jest również znany jako pełne wyrzucania elementów bezużytecznych, ponieważ odzyskuje wszystkie obiekty we wszystkich generacjach (oznacza to, że wszystkie obiekty w stercie zarządzane).

### <a name="survival-and-promotions"></a>Przetrwanie i promocje

Obiekty, które nie są odzyskane w wyrzucania elementów bezużytecznych są znane jako ocalałych i są promowane do następnej generacji. Obiekty, które przetrwają generacji 0 wyrzucania elementów bezużytecznych są promowane do generacji 1; obiekty, które przetrwają wyrzucanie elementów bezużytecznych generacji 1 są promowane do generacji 2; i obiekty, które przetrwają generacji 2 wyrzucania elementów bezużytecznych pozostają w generacji 2.

Gdy moduł zbierający elementy bezużyteczne wykryje, że wskaźnik przeżycia jest wysoki w generacji, zwiększa próg alokacji dla tej generacji. Następna kolekcja pobiera znaczny rozmiar odzyskanej pamięci. CLR stale równoważy dwa priorytety: nie pozwalając aplikacji zestaw roboczy uzyskać zbyt duże, opóźniając wyrzucania elementów bezużytecznych i nie pozwalając wyrzucania elementów bezużytecznych uruchomić zbyt często.

### <a name="ephemeral-generations-and-segments"></a>Efemery i segmenty

Ponieważ obiekty w pokoleniach 0 i 1 są krótkotrwałe, pokolenia te są znane jako pokolenia efemeralne.

Pokolenia efemeralne muszą być przydzielane w segmencie pamięci, który jest znany jako segment efemeryczny. Każdy nowy segment nabyty przez moduł zbierający elementy bezużyteczne staje się nowym segmentem efemerycznym i zawiera obiekty, które przetrwały wyrzucanie elementów bezużytecznych generacji 0. Stary segment efemeryczny staje się segmentem nowej generacji 2.

Rozmiar segmentu efemeralnego różni się w zależności od tego, czy system jest 32-bitowy czy 64-bitowy, a także od typu modułu odśmiecania pamięci, który jest uruchomiony. Wartości domyślne są wyświetlane w poniższej tabeli.

||32-bitowa|64-bitowy|
|-|-------------|-------------|
|Stacja robocza GC|16 MB|256 MB|
|Gc serwera|64 MB|4 GB|
|Serwer GC z > 4 procesorami logicznymi|32 MB|2 GB|
|Serwer GC z procesorami logicznymi > 8|16 MB|1 GB|

Segment efemeryczny może zawierać obiekty generacji 2. Obiekty generacji 2 mogą używać wielu segmentów (tyle, ile wymaga proces i pamięć).

Ilość uwolnionej pamięci z ulotnej kolekcji elementów bezużytecznych jest ograniczona do rozmiaru segmentu efemeralnego. Ilość pamięci, która jest zwalniana jest proporcjonalna do miejsca zajmowanego przez martwe obiekty.

## <a name="what-happens-during-a-garbage-collection"></a>Co się dzieje podczas wyrzucania elementów bezużytecznych

Wyrzucanie elementów bezużytecznych ma następujące fazy:

- Faza oznaczania, która wyszukuje i tworzy listę wszystkich obiektów na żywo.

- Faza przenoszenia, która aktualizuje odwołania do obiektów, które zostaną skompaktowane.

- Faza zagęszczania, która odzyskuje przestrzeń zajmowaną przez martwe obiekty i zagęszcza ocalałe obiekty. Faza kompaktowania przenosi obiekty, które przetrwały wyrzucanie elementów bezużytecznych w kierunku starszego końca segmentu.

  Ponieważ kolekcje 2 generacji mogą zajmować wiele segmentów, obiekty, które są promowane do generacji 2 można przenieść do starszego segmentu. Zarówno ocalałych z pokolenia 1, jak i drugiej generacji można przenieść do innego segmentu, ponieważ są one promowane do pokolenia 2.

  Zwykle sterty dużych obiektów (LOH) nie jest skompaktowany, ponieważ kopiowanie dużych obiektów nakłada karę wydajności. Jednak w .NET Core i .NET Framework 4.5.1 i <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> nowszych, można użyć właściwości do kompaktowania sterty dużych obiektów na żądanie. Ponadto LOH jest automatycznie zagęszczany, gdy ustawiono twardy limit, określając:

  - ograniczenie pamięci w pojemniku, lub
  - opcje konfiguracji [programu GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) lub [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent)

Moduł zbierający elementy bezużyteczne używa następujących informacji, aby określić, czy obiekty są aktywne:

- **Stos korzeni**. Stos zmiennych dostarczonych przez kompilator just-in-time (JIT) i walker stosu. Optymalizacje JIT można wydłużyć lub skrócić regiony kodu, w którym zmienne stosu są zgłaszane do modułu odśmiecania pamięci.

- **Uchwyty wyrzucania elementów bezużytecznych**. Obsługuje ten punkt do obiektów zarządzanych i które mogą być przydzielane przez kod użytkownika lub przez środowisko uruchomieniowe języka wspólnego.

- **Dane statyczne**. Obiekty statyczne w domenach aplikacji, które mogą odwoływać się do innych obiektów. Każda domena aplikacji śledzi jej obiekty statyczne.

Przed rozpoczęciem wyrzucania elementów bezużytecznych wszystkie wątki zarządzane są zawieszone z wyjątkiem wątku, który wyzwolił wyrzucanie elementów bezużytecznych.

Na poniższej ilustracji przedstawiono wątek, który wyzwala wyrzucania elementów bezużytecznych i powoduje, że inne wątki, które mają zostać zawieszone.

![Gdy wątek wyzwala wyrzucanie elementów bezużytecznych](./media/gc-triggered.png)

## <a name="manipulate-unmanaged-resources"></a>Manipulowanie zasobami niezarządzanymi

Jeśli obiekty zarządzane odwołują się do obiektów niezarządzanych przy użyciu ich natywnych dojścia do plików, musisz jawnie zwolnić obiekty niezarządzane, ponieważ moduł zbierający elementy bezużyteczne śledzi tylko pamięć na zarządzanym stercie.

Użytkownicy obiektu zarządzanego nie mogą usuwać natywnych zasobów używanych przez obiekt. Aby wykonać oczyszczanie, można sprawić, że obiekt zarządzany będzie sfinalizowany. Finalizacja składa się z akcji oczyszczania, które są wykonywane, gdy obiekt nie jest już używany. Gdy obiekt zarządzany umiera, wykonuje akcje oczyszczania, które są określone w jego finalizator metody.

Gdy finalizable obiekt jest wykrywany jako martwy, jego finalizator jest umieszczany w kolejce, tak aby jego akcje oczyszczania są wykonywane, ale sam obiekt jest promowany do następnej generacji. W związku z tym należy poczekać do następnego wyrzucania elementów bezużytecznych, który występuje w tej generacji (co nie jest koniecznie następnego wyrzucania elementów bezużytecznych), aby ustalić, czy obiekt został odzyskany.

Aby uzyskać więcej informacji <xref:System.Object.Finalize?displayProperty=nameWithType>na temat finalizacji, zobacz .

## <a name="workstation-and-server-garbage-collection"></a>Stacja robocza i wyrzucanie elementów bezużytecznych serwera

Moduł zbierający elementy bezużyteczne jest samodostrajanie i może pracować w wielu różnych scenariuszach. Można użyć [ustawienia pliku konfiguracji,](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) aby ustawić typ wyrzucania elementów bezużytecznych na podstawie właściwości obciążenia. CLR zawiera następujące typy wyrzucania elementów bezużytecznych:

- Wyrzucanie elementów bezużytecznych stacji roboczej (GC) jest przeznaczony dla aplikacji klienckich. Jest to domyślny smak GC dla aplikacji autonomicznych. W przypadku hostowanych aplikacji, na przykład hostowanych przez ASP.NET, host określa domyślny smak GC.

  Wyrzucanie elementów bezużytecznych stacji roboczej może być równoczesne lub niejednoczesne. Równoczesne wyrzucanie elementów bezużytecznych umożliwia zarządzanych wątków, aby kontynuować operacje podczas wyrzucania elementów bezużytecznych. [Wyrzucanie elementów bezużytecznych w tle](#background-workstation-garbage-collection) zastępuje [równoczesne wyrzucanie elementów bezużytecznych](#concurrent-garbage-collection) w .NET Framework 4 i nowszych wersjach.

- Wyrzucanie elementów bezużytecznych serwera, który jest przeznaczony dla aplikacji serwera, które wymagają wysokiej przepływności i skalowalności.

  - W .NET Core wyrzucanie elementów bezużytecznych serwera może być niewspółbieżne lub w tle.

  - W .NET Framework 4.5 i nowszych wersjach wyrzucanie elementów bezużytecznych serwera może być niewspółbieżne lub w tle (wyrzucanie elementów bezużytecznych w tle zastępuje równoczesne wyrzucanie elementów bezużytecznych). W .NET Framework 4 i poprzednich wersjach wyrzucanie elementów bezużytecznych serwera jest niewspółbieżne.

Na poniższej ilustracji przedstawiono dedykowane wątki, które wykonują wyrzucanie elementów bezużytecznych na serwerze:

![Wątki wyrzucania elementów bezużytecznych serwera](./media/gc-server.png)

### <a name="compare-workstation-and-server-garbage-collection"></a>Porównanie stacji roboczej i wyrzucania elementów bezużytecznych serwera

Poniżej przedstawiono zagadnienia dotyczące wątków i wydajności wyrzucania elementów bezużytecznych stacji roboczej:

- Kolekcja występuje w wątku użytkownika, który wyzwolił wyrzucania elementów bezużytecznych i pozostaje na tym samym priorytecie. Ponieważ wątki użytkownika zazwyczaj działają z normalnym priorytetem, moduł zbierający elementy bezużyteczne (który działa w wątku o normalnym priorytecie) musi konkurować z innymi wątkami dla czasu procesora CPU. (Wątki, które uruchamiają kod macierzysty nie są zawieszone na serwerze lub stacji roboczej wyrzucania elementów bezużytecznych.)

- Wyrzucanie elementów bezużytecznych stacji roboczej jest zawsze używane na komputerze, który ma tylko jeden procesor, niezależnie od [ustawienia konfiguracji](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver).

Poniżej przedstawiono zagadnienia dotyczące wątków i wydajności dla wyrzucania elementów bezużytecznych serwera:

- Kolekcja występuje na wielu dedykowanych wątków, które są uruchomione na `THREAD_PRIORITY_HIGHEST` poziomie priorytetu.

- Sterty i dedykowany wątek do wykonywania wyrzucania elementów bezużytecznych są przewidziane dla każdego procesora CPU, a sterty są zbierane w tym samym czasie. Każda sterta zawiera stos małych obiektów i sterty dużych obiektów, a wszystkie sterty są dostępne za pomocą kodu użytkownika. Obiekty na różnych stertach mogą odnosić się do siebie.

- Ponieważ wiele wątków wyrzucania elementów bezużytecznych współpracują ze sobą, wyrzucanie elementów bezużytecznych serwera jest szybsze niż wyrzucanie elementów bezużytecznych stacji roboczej na tym samym stosie rozmiaru.

- Wyrzucanie elementów bezużytecznych serwera często ma większe segmenty rozmiaru. Jest to jednak tylko uogólnienie: rozmiar segmentu jest specyficzny dla implementacji i może ulec zmianie. Nie należy zakładać o rozmiar segmentów przydzielonych przez moduł zbierający elementy bezużyteczne podczas dostrajania aplikacji.

- Wyrzucanie elementów bezużytecznych serwera może być intensywnie korzystających z zasobów. Załóżmy na przykład, że istnieje 12 procesów, które używają serwera GC uruchomionego na komputerze, który ma 4 procesory. Jeśli wszystkie procesy zdarzają się zbierać śmieci w tym samym czasie, będą one kolidować ze sobą, jak byłoby 12 wątków zaplanowanych na tym samym procesorze. Jeśli procesy są aktywne, nie jest dobrym pomysłem, aby wszystkie one używać gc serwera.

Jeśli używasz setki wystąpień aplikacji, należy rozważyć użycie wyrzucania elementów bezużytecznych stacji roboczej z równoczesnych wyrzucania elementów bezużytecznych wyłączone. Spowoduje to mniej przełączania kontekstu, co może zwiększyć wydajność.

## <a name="background-workstation-garbage-collection"></a>Wyrzucanie elementów bezużytecznych stacji roboczej w tle

W tle workstation wyrzucania elementów bezużytecznych efemerycznych pokoleń (0 i 1) są zbierane zgodnie z potrzebami, gdy kolekcja generacji 2 jest w toku. Wyrzucanie elementów bezużytecznych stacji roboczej w tle jest wykonywane w dedykowanym wątku i ma zastosowanie tylko do kolekcji generacji 2.

Wyrzucanie elementów bezużytecznych w tle jest domyślnie włączone i można je włączyć lub wyłączyć za pomocą ustawienia konfiguracji [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) w aplikacjach .NET Framework lub w ustawieniu [System.GC.Concurrent](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) w aplikacjach .NET Core.

> [!NOTE]
> Wyrzucanie elementów bezużytecznych w tle zastępuje [równoczesne wyrzucanie elementów bezużytecznych](#concurrent-garbage-collection) i jest dostępne w .NET Framework 4 i nowszych wersjach. W .NET Framework 4 jest obsługiwana tylko dla wyrzucania elementów bezużytecznych stacji roboczej. Począwszy od .NET Framework 4.5, wyrzucanie elementów bezużytecznych w tle jest dostępna zarówno dla stacji roboczej, jak i wyrzucania elementów bezużytecznych serwera.

Kolekcja na efemerycznych pokoleń podczas wyrzucania elementów bezużytecznych w tle jest znany jako wyrzucania elementów bezużytecznych pierwszego planu. Po wystąpieniu wyrzucania elementów bezużytecznych pierwszego planu wszystkie wątki zarządzane są zawieszone.

Gdy wyrzucanie elementów bezużytecznych w tle jest w toku i przydzielono wystarczającą liczbę obiektów w generacji 0, CLR wykonuje generacji 0 lub generacji 1 wyrzucania elementów bezużytecznych pierwszego planu. Dedykowane wątku wyrzucania elementów bezużytecznych w tle sprawdza w częstych bezpiecznych punktach, aby ustalić, czy istnieje żądanie wyrzucania elementów bezużytecznych pierwszego planu. Jeśli istnieje, kolekcja w tle zawiesza się tak, że może wystąpić wyrzucanie elementów bezużytecznych pierwszego planu. Po zakończeniu wyrzucania elementów bezużytecznych pierwszego planu dedykowany wątek wyrzucania elementów bezużytecznych w tle i wątki użytkownika zostaną wznowione.

Wyrzucanie elementów bezużytecznych w tle usuwa ograniczenia alokacji nałożone przez równoczesne wyrzucanie elementów bezużytecznych, ponieważ podczas wyrzucania elementów bezużytecznych w tle mogą wystąpić efemeralne wyrzucanie elementów bezużytecznych. Wyrzucanie elementów bezużytecznych w tle można usunąć martwe obiekty w efemerycznych pokoleń. Można również rozwinąć sterty w razie potrzeby podczas wyrzucania elementów bezużytecznych generacji 1.

Na poniższej ilustracji przedstawiono wyrzucanie elementów bezużytecznych w tle wykonywane w oddzielnym dedykowanym wątku na stacji roboczej:

![Wyrzucanie elementów bezużytecznych stacji roboczej w tle](./media/fundamentals/background-workstation-garbage-collection.png)

### <a name="background-server-garbage-collection"></a>Wyrzucanie elementów bezużytecznych serwera w tle

Począwszy od .NET Framework 4.5, wyrzucanie elementów bezużytecznych serwera w tle jest domyślnym trybem wyrzucania elementów bezużytecznych serwera.

Funkcje wyrzucania elementów bezużytecznych serwera w tle podobnie jak wyrzucanie elementów bezużytecznych stacji roboczej w tle, opisane w poprzedniej sekcji, ale istnieje kilka różnic:

- Wyrzucanie elementów bezużytecznych stacji roboczej w tle używa jednego dedykowanego wątku wyrzucania elementów bezużytecznych w tle, podczas gdy wyrzucanie elementów bezużytecznych serwera w tle używa wielu wątków. Zazwyczaj istnieje dedykowany wątek dla każdego procesora logicznego.

- W przeciwieństwie do wątku wyrzucania elementów bezużytecznych w tle stacji roboczej, te wątki nie uchylić.

Na poniższej ilustracji przedstawiono wyrzucanie elementów bezużytecznych w tle wykonywane w oddzielnym wątku dedykowanym na serwerze:

![Wyrzucanie elementów bezużytecznych serwera w tle](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Równoczesne wyrzucanie elementów bezużytecznych

> [!TIP]
> Niniejsza sekcja dotyczy:
>
> - .NET Framework 3.5 i wcześniejszy dla wyrzucania elementów bezużytecznych stacji roboczej
> - .NET Framework 4 i wcześniejszy dla wyrzucania elementów bezużytecznych serwera
>
> Równoczesne wyrzucanie elementów bezużytecznych jest zastępowane przez [wyrzucanie elementów bezużytecznych](#background-workstation-garbage-collection) w tle w nowszych wersjach.

W stacji roboczej lub wyrzucania elementów bezużytecznych serwera, można [włączyć równoczesne wyrzucania elementów bezużytecznych](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md), co umożliwia wątki uruchamiane jednocześnie z dedykowanego wątku, który wykonuje wyrzucania elementów bezużytecznych przez większość czasu trwania kolekcji. Ta opcja dotyczy tylko wyrzucania elementów bezużytecznych w generacji 2; generacje 0 i 1 są zawsze niejednoczesne, ponieważ kończą się bardzo szybko.

Równoczesne wyrzucanie elementów bezużytecznych umożliwia interakcyjne aplikacje, aby być bardziej elastyczne, minimalizując pauzy dla kolekcji. Zarządzane wątki można kontynuować uruchamianie przez większość czasu, gdy działa wątek wyrzucania elementów bezużytecznych równoczesnych. Powoduje to krótsze przerwy podczas wyrzucania elementów bezużytecznych występuje.

Równoczesne wyrzucanie elementów bezużytecznych jest wykonywane w dedykowanym wątku. Domyślnie CLR uruchamia wyrzucanie elementów bezużytecznych stacji roboczej z włączoną równoczesną wyrzucaniem elementów bezużytecznych. Dotyczy to komputerów jednoprocesorowych i wieloprocesorowych.

Na poniższej ilustracji przedstawiono równoczesne wyrzucanie elementów bezużytecznych wykonywane w oddzielnym dedykowanym wątku.

![Równoczesne wątki wyrzucania elementów bezużytecznych](./media/gc-concurrent.png)

## <a name="see-also"></a>Zobacz też

- [Opcje konfiguracji dla GC](../../core/run-time-config/garbage-collector.md)
- [Wyrzucanie elementów bezużytecznych](index.md)
