---
title: Podstawy wyrzucania elementów bezużytecznych
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
ms.openlocfilehash: 1fdf7fcd61fb4bf9e8e0cbfe28842208f6eadd00
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102440"
---
# <a name="fundamentals-of-garbage-collection"></a>Podstawy wyrzucania elementów bezużytecznych

W czasie wykonywania języka wspólnego (CLR), moduł zbierający elementy bezużyteczne (GC) służy jako automatyczny menedżer pamięci. Moduł zbierający elementy bezużyteczne zarządza alokacji i zwalniania pamięci dla aplikacji. Dla deweloperów pracujących z kodem zarządzanym oznacza to, że nie trzeba pisać kodu do wykonywania zadań zarządzania pamięcią. Automatyczne zarządzanie pamięcią może wyeliminować typowe problemy, takie jak zapominanie o zwolnieniu obiektu i spowodowanie przecieku pamięci lub próba uzyskania dostępu do pamięci dla obiektu, który został już zwolniony.

W tym artykule opisano podstawowe pojęcia wyrzucania elementów bezużytecznych.

## <a name="benefits"></a>Korzyści

Moduł zbierający elementy bezużyteczne zapewnia następujące korzyści:

- Zwalnia programistów z konieczności ręcznego zwalniania pamięci.

- Wydajnie przydziela obiekty na zarządzanym stercie.

- Odzyskuje obiekty, które nie są już używane, czyści ich pamięci i utrzymuje pamięć dostępną dla przyszłych alokacji. Obiekty zarządzane automatycznie uzyskać czystą zawartość na początek, więc ich konstruktory nie trzeba inicjować każde pole danych.

- Zapewnia bezpieczeństwo pamięci, upewniając się, że obiekt nie może używać zawartości innego obiektu.

## <a name="fundamentals-of-memory"></a>Podstawy pamięci

Na poniższej liście podsumowano ważne pojęcia dotyczące pamięci CLR.

- Każdy proces ma własną, oddzielną wirtualną przestrzeń adresową. Wszystkie procesy na tym samym komputerze współużytkują tę samą pamięć fizyczną i plik stronicowu, jeśli taki istnieje.

- Domyślnie na komputerach 32-bitowych każdy proces ma wirtualną przestrzeń adresową w trybie użytkownika 2 GB.

- Jako deweloper aplikacji pracujesz tylko z wirtualną przestrzenią adresową i nigdy nie manipulujesz bezpośrednio pamięcią fizyczną. Moduł zbierający elementy bezużyteczne przydziela i zwalnia pamięć wirtualną dla Ciebie na zarządzanym stosie.

  Jeśli piszesz kod macierzysty, używasz funkcji systemu Windows do pracy z wirtualną przestrzenią adresową. Te funkcje przydzielają i zwalniają pamięć wirtualną na natywnych stertach.

- Pamięć wirtualna może być w trzech stanach:

  | Stan | Opis |
  |---------|---------|
  | Bezpłatna | Blok pamięci nie ma odwołań do niego i jest dostępny do alokacji. |
  | Zarezerwowano | Blok pamięci jest dostępny do użytku i nie może być używany dla innych żądań alokacji. Jednak nie można przechowywać danych do tego bloku pamięci, dopóki nie zostanie zatwierdzony. |
  | Committed | Blok pamięci jest przypisany do magazynu fizycznego. |

- Wirtualna przestrzeń adresowa może zostać pofragmentowana. Oznacza to, że w przestrzeni adresowej znajdują się wolne bloki, znane również jako otwory. Gdy wymagane jest alokacja pamięci wirtualnej, menedżer pamięci wirtualnej musi znaleźć pojedynczy wolny blok, który jest wystarczająco duży, aby spełnić to żądanie alokacji. Nawet jeśli masz 2 GB wolnego miejsca, alokacja, która wymaga 2 GB, zakończy się niepowodzeniem, chyba że całe to wolne miejsce znajduje się w jednym bloku adresów.

- Można zabraknąć pamięci, jeśli nie ma wystarczającej ilości wirtualnej przestrzeni adresowej do zarezerwowania lub fizycznej przestrzeni do zatwierdzenia.

  Plik strony jest używany nawet wtedy, gdy ciśnienie pamięci fizycznej (czyli zapotrzebowanie na pamięć fizyczną) jest niskie. Po raz pierwszy ciśnienie pamięci fizycznej jest wysokie, system operacyjny musi zrobić miejsce w pamięci fizycznej do przechowywania danych i kopii zapasowej niektórych danych, które znajdują się w pamięci fizycznej do pliku stronicowego. Te dane nie są stronicowane, dopóki nie są potrzebne, więc można napotkać stronicowanie w sytuacjach, gdy ciśnienie pamięci fizycznej jest niskie.
  
### <a name="memory-allocation"></a>Alokacja pamięci

Podczas inicjowania nowego procesu środowisko uruchomieniowe rezerwuje dla niego ciągły region przestrzeni adresowej. Zarezerwowana przestrzeń adresowa jest nazywana „zarządzanym stosem”. Zarządzany stos zawiera wskaźnik do adresu, w którym zostanie przydzielony następny obiekt ze stosu. Początkowo wskaźnik jest ustawiony na adres podstawowy zarządzanego stosu. Wszystkie typy odwołań są przydzielane na zarządzanym stosie. Gdy aplikacja tworzy pierwszy typ referencyjny, jest dla niego rezerwowana pamięć pod podstawowym adresem zarządzanego stosu. Podczas tworzenia następnego obiektu moduł odśmiecania pamięci przydziela mu pamięć w przestrzeni adresowej następującej bezpośrednio po pierwszym obiekcie. Tak długo, jak jest dostępna przestrzeń adresowa, moduł odśmiecania pamięci przydziela w ten sposób miejsce nowym obiektom.

Przydzielanie pamięci z zarządzanego stosu jest szybsze niż niezarządzane przydzielanie pamięci. Ponieważ środowisko wykonawcze przydziela pamięć dla obiektu, dodając wartość do wskaźnika, jest prawie tak szybko, jak przydzielanie pamięci ze stosu. Ponadto ponieważ nowe obiekty, które są przydzielane kolejno są przechowywane w sposób ciągły w zarządzanym stosie, aplikacja może szybko uzyskać dostęp do obiektów.

### <a name="memory-release"></a>Zwolnienie pamięci

Aparat optymalizacji w module odśmiecania pamięci ustala najlepszy moment na wykonanie procesu wyrzucania w oparciu o dokonywane przydziały. Gdy moduł odśmiecania wykonuje ten proces, zwalnia pamięć zajmowaną przez obiekty, które nie są już używane przez aplikację. Określa, które obiekty nie są już używane, badając *korzenie*aplikacji. Katalogi główne aplikacji obejmują pola statyczne, zmienne lokalne i parametry na stosie wątku oraz rejestry procesora CPU. Każdy obiekt główny odwołuje się do obiektu w zarządzanym stosie albo przyjmuje wartość null. Moduł zbierający elementy bezużyteczne ma dostęp do listy aktywnych katalogów głównych, które kompilator just-in-time (JIT) i zachowanie środowiska wykonawczego. Korzystając z tej listy, moduł zbierający elementy bezużyteczne tworzy wykres, który zawiera wszystkie obiekty, które są osiągalne z korzeni.

Obiekty nieobecne na liście są nieosiągalne z obiektów głównych aplikacji. Moduł zbierający elementy bezużyteczne uważa za nieosiągalne obiekty śmieci i zwalnia pamięć przydzieloną dla nich. Podczas wyrzucania elementów moduł odśmiecania pamięci analizuje zarządzany stos w poszukiwaniu bloków przestrzeni adresowej zajmowanych przez nieosiągalne obiekty. Po wykryciu niedostępnego obiektu moduł odśmiecania za pomocą funkcji kopiowania pamięci kompaktuje dostępne obiekty wewnątrz pamięci i jednoczenie zwalnia bloki przestrzeni adresowej przydzielone dotychczas nieosiągalnym obiektom. Po skompaktowaniu pamięci osiągalnych obiektów moduł odśmiecania pamięci dokonuje niezbędnych korekt wskaźników, tak aby obiekty główne aplikacji wskazywały obiekty w ich nowych lokalizacjach. Ponadto ustawia wskaźnik zarządzanego stosu za ostatnim dostępnym obiektem.

Pamięć jest kompaktowany tylko wtedy, gdy kolekcja odnajduje znaczną liczbę obiektów nieosiągalnych. Jeśli żaden obiekt w zarządzanym stosie nie wymaga wyrzucenia, nie ma też potrzeby kompaktowania pamięci.

W celu poprawy wydajności działania środowisko uruchomieniowe przydziela pamięć dużym obiektom w oddzielnym stosie. Moduł odśmiecania pamięci automatycznie zwalnia pamięć dla dużych obiektów. Jednak aby uniknąć przenoszenia dużych obiektów w pamięci, ta pamięć zwykle nie jest skompaktowana.

## <a name="conditions-for-a-garbage-collection"></a>Warunki wyrzucania elementów bezużytecznych

Wyrzucanie elementów bezużytecznych występuje, gdy spełniony jest jeden z następujących warunków:

- System ma mało pamięci fizycznej. Jest to wykrywane przez powiadomienie o braku pamięci z systemu operacyjnego lub braku pamięci wskazanej przez hosta.

- Pamięć, która jest używana przez przydzielone obiekty na zarządzanym stercie przekracza dopuszczalny próg. Próg ten jest stale dostosowywany w miarę przebiegu procesu.

- Metoda <xref:System.GC.Collect%2A?displayProperty=nameWithType> jest wywoływana. W prawie wszystkich przypadkach nie trzeba wywoływać tej metody, ponieważ moduł zbierający elementy bezużyteczne działa w sposób ciągły. Ta metoda jest używana głównie w unikatowych sytuacjach i testowaniu.

## <a name="the-managed-heap"></a>Zarządzane sterty

Po modułu zbierającego elementy bezużyteczne jest inicjowany przez clr, przydziela segment pamięci do przechowywania i zarządzania obiektami. Ta pamięć jest nazywana zarządzanego stosu, w przeciwieństwie do macierzystego stosu w systemie operacyjnym.

Istnieje zarządzane sterty dla każdego procesu zarządzanego. Wszystkie wątki w procesie przydzielić pamięć dla obiektów na tym samym stosie.

Aby zarezerwować pamięć, moduł zbierający elementy bezużyteczne wywołuje funkcję [Windows VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) i rezerwuje jeden segment pamięci naraz dla zarządzanych aplikacji. Moduł zbierający elementy bezużyteczne rezerwuje również segmenty, w razie potrzeby i zwalnia segmenty z powrotem do systemu operacyjnego (po wyczyszczeniu ich z dowolnych obiektów) przez wywołanie funkcji [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) systemu Windows.

> [!IMPORTANT]
> Rozmiar segmentów przydzielonych przez moduł zbierający elementy bezużyteczne jest specyficzne dla implementacji i może ulec zmianie w dowolnym momencie, w tym w okresowych aktualizacji. Aplikacja nigdy nie powinna zakładać ani zależeć od określonego rozmiaru segmentu, ani nie powinna próbować skonfigurować ilości pamięci dostępnej dla alokacji segmentów.

Im mniej obiektów przydzielonych na stercie, tym mniej pracy moduł zbierający elementy bezużyteczne ma do wykonania. Podczas przydzielania obiektów nie należy używać zaokrąglonych wartości, które przekraczają twoje potrzeby, takich jak przydzielanie tablicy 32 bajtów, gdy potrzebujesz tylko 15 bajtów.

Po wyzwoleniu wyrzucania elementów bezużytecznych moduł zbierający elementy bezużyteczne odzyskuje pamięć, która jest zajęta przez martwe obiekty. Proces odzyskiwania kompakuje żywe obiekty, dzięki czemu są one przenoszone razem, a martwa przestrzeń jest usuwana, zmniejszając w ten sposób stertę. Dzięki temu obiekty, które są przydzielane razem pozostają razem na zarządzanym stosie, aby zachować ich lokalizacji.

Natrędliwość (częstotliwość i czas trwania) wyrzucania elementów bezużytecznych jest wynikiem ilości alokacji i ilość zachowanej pamięci na zarządzanym stosie.

Sterty można uznać za kumulację dwóch sterty: [sterty dużego obiektu](large-object-heap.md) i sterty małych obiektów. Sterta dużych obiektów zawiera obiekty o rozmiarze 85 000 bajtów i większych, które są zwykle tablicami. Rzadko zdarza się, aby obiekt instancji był bardzo duży.

> [!TIP]
> Można [skonfigurować rozmiar progu](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) dla obiektów, aby przejść na stercie dużych obiektów.

## <a name="generations"></a>Pokoleń

Algorytm GC opiera się na kilku zagadnieniach:

- Jest szybsze kompaktowanie pamięci dla części zarządzanego stosu niż dla całego zarządzanego stosu.
- Nowsze obiekty mają krótsze okresy istnienia, a starsze obiekty mają dłuższe okresy istnienia.
- Nowsze obiekty wydają się być powiązane ze sobą i dostępne przez aplikację w tym samym czasie.

Wyrzucanie elementów bezużytecznych występuje przede wszystkim z rekultywacji obiektów krótkotrwałe. Aby zoptymalizować wydajność modułu zbierającego elementy bezużyteczne, zarządzany stos jest podzielony na trzy generacje, 0, 1 i 2, dzięki czemu może obsługiwać obiekty trwałe i krótkotrwałe oddzielnie. Moduł zbierający elementy bezużyteczne przechowuje nowe obiekty w generacji 0. Obiekty utworzone wcześniej w okresie istnienia aplikacji i nieusunięte przez moduł odśmiecania trafiają na wyższy poziom, do generacji 1 i 2. Ponieważ jest szybsze kompaktowanie część zarządzanego stosu niż cały stos, ten schemat umożliwia modułowi zbierającemu pamięć zwolnić pamięć w określonej generacji, a nie zwolnić pamięć dla całego zarządzanego stosu za każdym razem, gdy wykonuje kolekcję.

- **Generacja 0**. Jest to najmłodsze pokolenie i zawiera krótkotrwałe obiekty. Przykładem obiektu krótkotrwałego jest zmienna tymczasowa. Wyrzucanie elementów bezużytecznych występuje najczęściej w tej generacji.

  Nowo przydzielone obiekty tworzą nową generację obiektów i są niejawnie generacji 0 kolekcji. Jednak jeśli są one duże obiekty, idą na stercie dużych obiektów w kolekcji generacji 2.

  Większość obiektów są odzyskane do wyrzucania elementów bezużytecznych w generacji 0 i nie przetrwać do następnej generacji.
  
  Jeśli aplikacja próbuje utworzyć nowy obiekt, gdy generacja 0 jest pełna, moduł odśmiecania elementów bezużytecznych wykonuje kolekcję w próbie wolnego miejsca adresu dla obiektu. Rozpoczyna od zbadania obiektów w generacji 0, a nie wszystkich obiektów w zarządzanym stosie. Tylko kolekcja generacji 0 często odzyskuje wystarczającą ilość pamięci, aby umożliwić aplikacji dalsze tworzenie nowych obiektów.

- **Generacja 1**. Ta generacja zawiera obiekty krótkotrwałe i służy jako bufor między obiektów krótkotrwałe i obiekty długowieczne.

  Po moduł zbierający elementy bezużyteczne wykonuje kolekcję generacji 0, kompakuje pamięć dla obiektów osiągalnych i promuje je do generacji 1. Ponieważ obiekty, które pozostały po procesie wyrzucania elementów, zwykle mają dłuższe okresy istnienia, podwyższenie im poziomu o generację jest jak najbardziej uzasadnione. Moduł zbierający elementy bezużyteczne nie musi ponownie zbadać obiektów w pokoleniach 1 i 2 za każdym razem, gdy wykonuje kolekcję generacji 0.
  
  Jeśli kolekcja generacji 0 nie odzyskuje wystarczającej ilości pamięci dla aplikacji, aby utworzyć nowy obiekt, moduł zbierający elementy bezużyteczne można wykonać kolekcję generacji 1, a następnie generacji 2. Obiekty w generacji 1, które nie zostały wyrzucone, są przenoszone do generacji 2.

- **Generacja 2**. Ta generacja zawiera obiekty o długiej żywotnej żywotnej. Przykładem obiektu długotrwałego jest obiekt w aplikacji serwera, który zawiera dane statyczne, które są aktywne przez cały czas trwania procesu.

  Obiekty w generacji 2, które przetrwają kolekcję pozostają w generacji 2, dopóki nie zostaną uznane za nieosiągalne w przyszłej kolekcji.

Wyrzucanie elementów bezużytecznych występuje w określonych pokoleniach, zgodnie z warunkami. Zbieranie pokolenia oznacza zbieranie przedmiotów w tym pokoleniu i wszystkich jego młodszych pokoleniach. Wyrzucanie elementów bezużytecznych generacji 2 jest również znany jako pełne wyrzucania elementów bezużytecznych, ponieważ odzyskuje obiekty we wszystkich pokoleniach (oznacza to, że wszystkie obiekty w zarządzanym stosie).

### <a name="survival-and-promotions"></a>Przetrwanie i promocje

Obiekty, które nie są odzyskane w wyrzucania elementów bezużytecznych są znane jako ocalałych i są promowane do następnej generacji:

- Obiekty, które przetrwają generacji 0 wyrzucania elementów bezużytecznych są promowane do generacji 1.
- Obiekty, które przetrwają generacji 1 wyrzucania elementów bezużytecznych są promowane do generacji 2.
- Obiekty, które przetrwają generacji 2 wyrzucania elementów bezużytecznych pozostają w generacji 2.

Gdy moduł zbierający elementy bezużyteczne wykryje, że przeżywalność jest wysoka w generacji, zwiększa próg alokacji dla tej generacji. Następna kolekcja pobiera znaczny rozmiar odzyskanej pamięci. Clr stale równoważy dwa priorytety: nie pozwalając zestawu roboczego aplikacji uzyskać zbyt duże, opóźniając wyrzucania elementów bezużytecznych i nie pozwalając wyrzucania elementów bezużytecznych uruchomić zbyt często.

### <a name="ephemeral-generations-and-segments"></a>Efemeryczne generacje i segmenty

Ponieważ obiekty w pokoleniach 0 i 1 są krótkotrwałe, te pokolenia są znane jako *efemeryczne pokolenia.*

Efemeryczne generacje są przydzielane w segmencie pamięci, który jest znany jako segment efemeryczny. Każdy nowy segment nabyty przez moduł zbierający elementy bezużyteczne staje się nowy segment efemeryczny i zawiera obiekty, które przetrwały generacji 0 wyrzucania elementów bezużytecznych. Stary segment efemeryczny staje się segmentem nowej generacji 2.

Rozmiar segmentu efemerycznego różni się w zależności od tego, czy system jest 32-bitowy czy 64-bitowy, a także od typu działającego modułu zbierającego elementy bezużyteczne[(stacja robocza lub serwer GC](workstation-server-gc.md)). W poniższej tabeli przedstawiono domyślne rozmiary segmentu efemerycznego.

|Stacja robocza/serwer GC|32-bitowa|64-bitowy|
|-|-------------|-------------|
|Stacja robocza GC|16 MB|256 MB|
|GC serwera|64 MB|4 GB|
|Serwer GC z > 4 procesorami logicznymi|32 MB|2 GB|
|Serwer GC z > 8 procesorów logicznych|16 MB|1 GB|

Segment efemeryczny może zawierać obiekty generacji 2. Obiekty generacji 2 mogą używać wielu segmentów (tyle, ile wymaga proces i pozwala na to pamięć).

Ilość zwolnionej pamięci z efemerycznego wyrzucania elementów bezużytecznych jest ograniczona do rozmiaru segmentu efemerycznego. Ilość pamięci, która jest zwolniona jest proporcjonalna do miejsca, które zostało zajęte przez martwe obiekty.

## <a name="what-happens-during-a-garbage-collection"></a>Co się dzieje podczas wyrzucania elementów bezużytecznych

Wyrzucanie elementów bezużytecznych ma następujące fazy:

- Faza oznaczania, która znajduje i tworzy listę wszystkich obiektów aktywne.

- Faza przenoszenia, która aktualizuje odwołania do obiektów, które zostaną skompaktowane.

- Faza zagęszczania, która odzyskuje przestrzeń zajmowaną przez martwe obiekty i kompakuje ocalałe obiekty. Faza kompacjowania przenosi obiekty, które przetrwały wyrzucanie elementów bezużytecznych w kierunku starszego końca segmentu.

  Ponieważ kolekcje generacji 2 mogą zajmować wiele segmentów, obiekty, które są promowane do generacji 2, mogą być przenoszone do starszego segmentu. Zarówno pokolenia 1, jak i pokolenia 2 ocalałych można przenieść do innego segmentu, ponieważ są one promowane do generacji 2.

  Zwykle sterty dużych obiektów (LOH) nie jest skompaktowany, ponieważ kopiowanie dużych obiektów nakłada karę wykonania. Jednak w .NET Core i w programie .NET Framework 4.5.1 i nowszych można użyć <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> właściwości do kompaktowania sterty dużych obiektów na żądanie. Ponadto LOH jest automatycznie kompaktowany, gdy ustawiony jest twardy limit, określając:

  - Limit pamięci w kontenerze.
  - Opcje konfiguracji w czasie wykonywania [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) lub [GCHeapHardLimitPercent.](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent)

Moduł zbierający elementy bezużyteczne używa następujących informacji, aby ustalić, czy obiekty są aktywne:

- **Stos korzenie**. Stos zmiennych dostarczonych przez kompilator just-in-time (JIT) i walker stosu. Optymalizacje JIT można wydłużyć lub skrócić regiony kodu, w którym zmienne stosu są zgłaszane do modułu zbierającego elementy bezużyteczne.

- **Uchwyty wyrzucania elementów bezużytecznych**. Obsługuje, które wskazują na obiekty zarządzane i które mogą być przydzielane przez kod użytkownika lub przez środowisko uruchomieniowe języka wspólnego.

- **Dane statyczne**. Obiekty statyczne w domenach aplikacji, które mogą odwoływać się do innych obiektów. Każda domena aplikacji śledzi swoje obiekty statyczne.

Przed uruchomieniem wyrzucania elementów bezużytecznych wszystkie wątki zarządzane są zawieszone z wyjątkiem wątku, który wyzwolił wyrzucanie elementów bezużytecznych.

Na poniższej ilustracji przedstawiono wątek, który wyzwala wyrzucania elementów bezużytecznych i powoduje, że inne wątki mają zostać zawieszone.

![Gdy wątek wyzwala wyrzucanie elementów bezużytecznych](./media/gc-triggered.png)

## <a name="unmanaged-resources"></a>Zasoby niezarządzane

Dla większości obiektów, które tworzy aplikacja, można polegać na wyrzucania elementów bezużytecznych, aby automatycznie wykonywać niezbędne zadania zarządzania pamięcią. Zasoby niezarządzane wymagają jednak jawnego usuwania z pamięci. Najpopularniejszym typem niezarządzanego zasobu jest obiekt opakowujący zasób systemu operacyjnego, taki jak dojście do pliku, uchwyt okna lub połączenie sieciowe. Mimo że moduł zbierający elementy bezużyteczne jest w stanie śledzić okres istnienia obiektu zarządzanego, który hermetyzuje niezarządzanego zasobu, nie ma określonej wiedzy na temat sposobu czyszczenia zasobu.

Podczas tworzenia obiektu, który hermetyzuje niezarządzanego zasobu, zaleca się podanie kodu niezbędnego do oczyszczenia zasobu niezarządzanego w metodzie publicznej. `Dispose` Zapewniając `Dispose` metodę, można włączyć użytkowników obiektu jawnie zwolnić jego pamięci po zakończeniu z obiektu. Korzystając z obiektu, który hermetyzuje niezarządzany zasób, upewnij się, że wywołasz `Dispose` w razie potrzeby.

Należy również zapewnić sposób, aby niezarządzane zasoby zostały zwolnione w przypadku, `Dispose`gdy konsument typu zapomni zadzwonić . Można użyć bezpiecznego dojścia do zawijania zasobu niezarządzanego <xref:System.Object.Finalize?displayProperty=nameWithType> lub zastąpienia metody.

Aby uzyskać więcej informacji na temat czyszczenia zasobów niezarządzanych, zobacz [Czyszczenie zasobów niezarządzanych](unmanaged.md).

## <a name="see-also"></a>Zobacz też

- [Wyrzucanie elementów bezużytecznych stacji roboczych i serwera](workstation-server-gc.md)
- [Wyrzucanie elementów bezużytecznych w tle](background-gc.md)
- [Opcje konfiguracji gc](../../core/run-time-config/garbage-collector.md)
- [Wyrzucanie elementów bezużytecznych](index.md)
