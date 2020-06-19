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
ms.openlocfilehash: 438188b6d694bdeab772c43ef92e5621c68facff
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990214"
---
# <a name="fundamentals-of-garbage-collection"></a>Podstawowe informacje dotyczące wyrzucania elementów bezużytecznych

W środowisku uruchomieniowym języka wspólnego (CLR) Moduł wyrzucania elementów bezużytecznych (GC) służy jako automatyczny Menedżer pamięci. Moduł zbierający elementy bezużyteczne zarządza alokacją i ilością pamięci dla aplikacji. W przypadku deweloperów pracujących z kodem zarządzanym oznacza to, że nie trzeba pisać kodu w celu wykonywania zadań zarządzania pamięcią. Automatyczne zarządzanie pamięcią może wyeliminować typowe problemy, takie jak zapominanie o zwolnieniu obiektu i spowodowanie przeciekiem pamięci lub próbą uzyskania dostępu do pamięci dla obiektu, który został już zwolniony.

W tym artykule opisano podstawowe pojęcia dotyczące wyrzucania elementów bezużytecznych.

## <a name="benefits"></a>Korzyści

Moduł wyrzucania elementów bezużytecznych zapewnia następujące korzyści:

- Zwalnia deweloperów od konieczności ręcznego zwolnienia pamięci.

- Efektywnie przydziela obiekty na stosie zarządzanym.

- Reoświadczenia obiektów, które nie są już używane, czyści ich pamięć i utrzymuje dostępną pamięć do przyszłych alokacji. Obiekty zarządzane automatycznie pobierają czystą zawartość do początku, więc ich konstruktory nie muszą inicjować każdego pola danych.

- Zapewnia bezpieczeństwo pamięci, upewniając się, że obiekt nie może użyć zawartości innego obiektu.

## <a name="fundamentals-of-memory"></a>Podstawowe informacje o pamięci

Poniższa lista zawiera podsumowanie ważnych pojęć dotyczących pamięci środowiska CLR.

- Każdy proces ma własną, oddzielną wirtualną przestrzeń adresową. Wszystkie procesy na tym samym komputerze współużytkują tę samą pamięć fizyczną i plik stronicowania, jeśli istnieje.

- Domyślnie na komputerach 32-bitowych każdy proces ma 2 GB wirtualnej przestrzeni adresowej w trybie użytkownika.

- Jako deweloper aplikacji pracujesz tylko z wirtualną przestrzenią adresową i nigdy nie manipulujesz bezpośrednio pamięci fizycznej. Moduł wyrzucania elementów bezużytecznych przydziela i zwalnia pamięć wirtualną na zarządzanym stosie.

  Jeśli piszesz kod natywny, używasz funkcji systemu Windows do pracy z wirtualną przestrzenią adresową. Te funkcje przydzielą i zwalniają pamięć wirtualną na stertach natywnych.

- Pamięć wirtualna może mieć trzy stany:

  | Stan | Opis |
  |---------|---------|
  | Bezpłatna | Blok pamięci nie ma odwołań do niego i jest dostępny do alokacji. |
  | Zarezerwowano | Blok pamięci jest dostępny do użycia i nie może być używany w żadnym innym żądaniu alokacji. Nie można jednak przechowywać danych w tym bloku pamięci, dopóki nie zostanie on zatwierdzony. |
  | Committed | Blok pamięci jest przypisany do magazynu fizycznego. |

- Wirtualne przestrzenie adresowe mogą zostać pofragmentowane. Oznacza to, że w przestrzeni adresowej istnieją wolne bloki, znane także jako otwory. Po zażądaniu alokacji pamięci wirtualnej Menedżer pamięci wirtualnej musi znaleźć pojedynczy bezpłatny blok, który jest wystarczająco duży, aby spełnić to żądanie alokacji. Nawet jeśli masz 2 GB wolnego miejsca, alokacja, która wymaga 2 GB, nie powiedzie się, chyba że wszystkie te wolne miejsca znajdują się w jednym bloku adresów.

- Jeśli nie ma wystarczającej ilości wirtualnej przestrzeni adresowej do zarezerwowania lub miejsca fizycznego do zatwierdzenia, można wypróbować za mało pamięci.

  Plik stronicowania jest używany nawet w przypadku niskiej ilości pamięci fizycznej (to jest zapotrzebowanie na ilość pamięci fizycznej). Pierwszy raz, gdy wykorzystanie pamięci fizycznej jest wysokie, system operacyjny musi zwolnić miejsce w pamięci fizycznej do przechowywania danych, a następnie tworzy kopię zapasową niektórych danych znajdujących się w pamięci fizycznej do pliku stronicowania. Te dane nie są stronicowane, dopóki nie jest to konieczne, więc można napotkać stronicowanie w sytuacjach, gdy wykorzystanie pamięci fizycznej jest niskie.
  
### <a name="memory-allocation"></a>Alokacja pamięci

Podczas inicjowania nowego procesu środowisko uruchomieniowe rezerwuje dla niego ciągły region przestrzeni adresowej. Zarezerwowana przestrzeń adresowa jest nazywana „zarządzanym stosem”. Zarządzany stos zawiera wskaźnik do adresu, w którym zostanie przydzielony następny obiekt ze stosu. Początkowo wskaźnik jest ustawiony na adres podstawowy zarządzanego stosu. Wszystkie typy odwołań są przydzielane na zarządzanym stosie. Gdy aplikacja tworzy pierwszy typ referencyjny, jest dla niego rezerwowana pamięć pod podstawowym adresem zarządzanego stosu. Podczas tworzenia następnego obiektu moduł odśmiecania pamięci przydziela mu pamięć w przestrzeni adresowej następującej bezpośrednio po pierwszym obiekcie. Tak długo, jak jest dostępna przestrzeń adresowa, moduł odśmiecania pamięci przydziela w ten sposób miejsce nowym obiektom.

Przydzielanie pamięci z zarządzanego stosu jest szybsze niż niezarządzane przydzielanie pamięci. Ponieważ środowisko uruchomieniowe przydziela pamięć dla obiektu przez dodanie wartości do wskaźnika, prawie tak szybko, jak alokacja pamięci ze stosu. Ponadto, ponieważ nowe obiekty, które są przydzielane po kolei, są przechowywane w sposób ciągły w zarządzanym stosie, aplikacja może szybko uzyskiwać dostęp do obiektów.

### <a name="memory-release"></a>Wersja pamięci

Aparat optymalizacji w module odśmiecania pamięci ustala najlepszy moment na wykonanie procesu wyrzucania w oparciu o dokonywane przydziały. Gdy moduł odśmiecania wykonuje ten proces, zwalnia pamięć zajmowaną przez obiekty, które nie są już używane przez aplikację. Określa, które obiekty nie są już używane przez badanie *katalogów głównych*aplikacji. Elementy główne aplikacji obejmują pola statyczne, zmienne lokalne i parametry stosu wątku oraz rejestry procesora. Każdy obiekt główny odwołuje się do obiektu w zarządzanym stosie albo przyjmuje wartość null. Moduł wyrzucania elementów bezużytecznych ma dostęp do listy aktywnych katalogów głównych, które utrzymuje kompilator just-in-Time (JIT) i środowisko uruchomieniowe. Korzystając z tej listy, Moduł wyrzucania elementów bezużytecznych tworzy wykres, który zawiera wszystkie obiekty, które są dostępne z elementów głównych.

Obiekty nieobecne na liście są nieosiągalne z obiektów głównych aplikacji. Moduł wyrzucania elementów bezużytecznych traktuje obiekty nieosiągalne i zwalnia przydzieloną im pamięć. Podczas wyrzucania elementów moduł odśmiecania pamięci analizuje zarządzany stos w poszukiwaniu bloków przestrzeni adresowej zajmowanych przez nieosiągalne obiekty. Po wykryciu niedostępnego obiektu moduł odśmiecania za pomocą funkcji kopiowania pamięci kompaktuje dostępne obiekty wewnątrz pamięci i jednoczenie zwalnia bloki przestrzeni adresowej przydzielone dotychczas nieosiągalnym obiektom. Po skompaktowaniu pamięci osiągalnych obiektów moduł odśmiecania pamięci dokonuje niezbędnych korekt wskaźników, tak aby obiekty główne aplikacji wskazywały obiekty w ich nowych lokalizacjach. Ponadto ustawia wskaźnik zarządzanego stosu za ostatnim dostępnym obiektem.

Pamięć jest kompaktowana tylko wtedy, gdy kolekcja odnajdzie znaczną liczbę nieosiągalnych obiektów. Jeśli żaden obiekt w zarządzanym stosie nie wymaga wyrzucenia, nie ma też potrzeby kompaktowania pamięci.

W celu poprawy wydajności działania środowisko uruchomieniowe przydziela pamięć dużym obiektom w oddzielnym stosie. Moduł odśmiecania pamięci automatycznie zwalnia pamięć dla dużych obiektów. Jednak aby uniknąć przesuwania dużych obiektów w pamięci, ta pamięć zwykle nie jest kompaktowana.

## <a name="conditions-for-a-garbage-collection"></a>Warunki dla wyrzucania elementów bezużytecznych

Odzyskiwanie pamięci występuje, gdy spełniony jest jeden z następujących warunków:

- System ma małą ilość pamięci fizycznej. Jest on wykrywany przez powiadomienie o niskim poziomie z systemu operacyjnego lub z niską ilością pamięci, jak wskazano na hoście.

- Pamięć używana przez przydzielone obiekty na zarządzanej stercie przekracza akceptowalny próg. Ten próg jest ciągle dostosowywany podczas uruchamiania procesu.

- <xref:System.GC.Collect%2A?displayProperty=nameWithType>Metoda jest wywoływana. W prawie wszystkich przypadkach nie trzeba wywoływać tej metody, ponieważ moduł wyrzucania elementów bezużytecznych działa w sposób ciągły. Ta metoda jest używana głównie do unikatowych sytuacji i testowania.

## <a name="the-managed-heap"></a>Zarządzane sterty

Po zainicjowaniu modułu wyrzucania elementów bezużytecznych przez środowisko CLR przydziela on segment pamięci do przechowywania obiektów i zarządzania nimi. Ta pamięć jest nazywana stertą zarządzaną, w przeciwieństwie do sterty natywnej w systemie operacyjnym.

Istnieje sterta zarządzana dla każdego procesu zarządzanego. Wszystkie wątki w procesie przydzielają pamięć dla obiektów na tym samym stosie.

W celu zarezerwowania pamięci moduł zbierający elementy bezużyteczne wywołuje funkcję [Funkcja VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) systemu Windows i rezerwuje jeden segment pamięci w czasie dla aplikacji zarządzanych. Moduł wyrzucania elementów bezużytecznych rezerwuje również segmenty, a następnie zwalnia segmenty z powrotem do systemu operacyjnego (po wyczyszczeniu ich z dowolnego obiektu), wywołując funkcję [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) systemu Windows.

> [!IMPORTANT]
> Rozmiar segmentów przydzielone przez moduł wyrzucania elementów bezużytecznych jest specyficzny dla implementacji i może ulec zmianie w dowolnym momencie, łącznie z okresowymi aktualizacjami. Aplikacja nigdy nie powinna mieć założeń lub zależeć od określonego rozmiaru segmentu ani nie powinna próbować skonfigurować ilości pamięci dostępnej dla alokacji segmentu.

Im mniejsza liczba obiektów przypadających na stosie, tym mniejsza ilość pracy do wykonania przez moduł zbierający elementy bezużyteczne. W przypadku przydzielania obiektów nie należy używać wartości zaokrąglonych, które przekraczają Twoje potrzeby, na przykład przydzielając tablicę 32 bajtów, gdy potrzebne są tylko 15 bajtów.

Po wyzwoleniu wyrzucania elementów bezużytecznych moduł zbierający elementy bezużyteczne odzyskuje pamięć, która jest zajęta przez obiekty martwe. Proces odzyskiwania kompaktuje obiekty na żywo, dzięki czemu są one przenoszone razem, a wolne miejsce zostaje usunięte, co sprawia, że sterta jest mniejsza. Dzięki temu obiekty, które są przydzielane razem, pozostają razem na zarządzanej stercie w celu zachowania ich lokalizacji.

Nietrwałość (częstotliwość i czas trwania) wyrzucania elementów bezużytecznych to wynik ilości alokacji i ilości pamięci przeprowadzonej w zarządzanym stosie.

Sterta może być traktowana jako akumulacja dwóch stert: [sterty dużych obiektów](large-object-heap.md) i sterty małego obiektu. Sterta dużego obiektu zawiera obiekty, które są 85 000 bajtów i większych, które są zwykle tablicami. Jest rzadki, aby obiekt wystąpienia był bardzo duży.

> [!TIP]
> Można [skonfigurować rozmiar progu](../../core/run-time-config/garbage-collector.md#large-object-heap-threshold) obiektów do przechodzenia do sterty dużego obiektu.

## <a name="generations"></a>Generacje

Algorytm GC jest oparty na kilku kwestiach:

- Jest to szybsze kompaktowanie pamięci dla części zarządzanego sterty niż w przypadku całej sterty zarządzanej.
- Nowsze obiekty mają krótsze okresy istnienia i starsze obiekty mają dłuższe okresy istnienia.
- Nowsze obiekty są ze sobą powiązane i uzyskują do nich dostęp przez aplikację w tym samym czasie.

Wyrzucanie elementów bezużytecznych odbywa się głównie z odzyskiwaniem obiektów o krótkim czasie. Aby zoptymalizować wydajność modułu wyrzucania elementów bezużytecznych, zarządzana sterta jest podzielona na trzy generacje, 0, 1 i 2, dzięki czemu może obsłużyć osobne, długotrwałe i krótkotrwałe obiekty. Moduł wyrzucania elementów bezużytecznych przechowuje nowe obiekty w generacji 0. Obiekty utworzone wcześniej w okresie istnienia aplikacji i nieusunięte przez moduł odśmiecania trafiają na wyższy poziom, do generacji 1 i 2. Ponieważ jest to szybsze kompaktowanie części zarządzanego sterty niż cała sterta, ten schemat umożliwia modułowi wyrzucania elementów bezużytecznych zwalnianie pamięci w określonej generacji zamiast zwalniania pamięci dla całego zarządzanego sterty za każdym razem, gdy wykonuje kolekcję.

- **Generacja 0**. Jest to najmłodsze generowanie i zawiera obiekty krótkotrwałe. Przykładem obiektu krótkotrwałego jest zmienna tymczasowa. Wyrzucanie elementów bezużytecznych występuje najczęściej w tej generacji.

  Nowo przydzielono obiekty tworzą nową generację obiektów i są kolekcjami niejawnie generacji 0. Jeśli jednak są to duże obiekty, przechodzą na stertę dużego obiektu (LOH), która jest czasami określana jako *generacja 3*. Generacja 3 to fizyczna generacja, która jest logicznie zbierana w ramach generacji 2.

  Większość obiektów jest odzyskiwana do wyrzucania elementów bezużytecznych w generacji 0 i nie przechodzenia do nowej generacji.
  
  Jeśli aplikacja próbuje utworzyć nowy obiekt, gdy generacja 0 jest pełna, moduł zbierający elementy bezużyteczne wykonuje kolekcję w próbie zwolnienia przestrzeni adresowej dla obiektu. Rozpoczyna od zbadania obiektów w generacji 0, a nie wszystkich obiektów w zarządzanym stosie. Kolekcja 0 sama generacji często ponownie przejmuje wystarczającą ilość pamięci, aby umożliwić aplikacji kontynuowanie tworzenia nowych obiektów.

- **Generacja 1**. Ta generacja zawiera obiekty krótkoterminowe i służy jako bufor między obiektami krótko-i długotrwałymi.

  Gdy moduł zbierający elementy bezużyteczne wykonuje zbiór generacji 0, kompaktuje pamięć dla osiągalnych obiektów i promuje je do generacji 1. Ponieważ obiekty, które pozostały po procesie wyrzucania elementów, zwykle mają dłuższe okresy istnienia, podwyższenie im poziomu o generację jest jak najbardziej uzasadnione. Moduł wyrzucania elementów bezużytecznych nie musi przebadać obiektów w generacjach 1 i 2 za każdym razem, gdy wykonuje kolekcję generacji 0.
  
  Jeśli zbiór generacji 0 nie odzyska wystarczającej ilości pamięci, aby aplikacja mogła utworzyć nowy obiekt, Moduł wyrzucania elementów bezużytecznych może wykonać kolekcję generacji 1, a następnie generację 2. Obiekty w generacji 1, które nie zostały wyrzucone, są przenoszone do generacji 2.

- **Generacja 2**. Ta generacja zawiera obiekty długotrwałe. Przykładem obiektu długotrwałego jest obiekt w aplikacji serwera, który zawiera dane statyczne, które są przechowywane na czas trwania procesu.

  Obiekty w generacji 2, które przeżyły kolekcję, pozostaną w generacji 2, dopóki nie zostaną uznane za nieosiągalne w przyszłych kolekcjach.
  
  Obiekty na stosie dużego obiektu (które są czasami określane jako *generacja 3*) są również zbierane w generacji 2.

Wyrzucanie elementów bezużytecznych odbywa się w określonych generacjach, gdy jest to warunki Zbieranie generacji oznacza gromadzenie obiektów w tej generacji i wszystkich jej młodszych generacjach. Wyrzucanie elementów bezużytecznych generacji 2 jest również znane jako pełne wyrzucanie elementów bezużytecznych, ponieważ odzyskuje obiekty we wszystkich generacjach (czyli wszystkie obiekty w stercie zarządzanym).

### <a name="survival-and-promotions"></a>Przeżycia i promocja

Obiekty, które nie są odzyskiwane w wyrzucaniu elementów bezużytecznych, są znane jako osoby przejmowane i są promowane do nowej generacji:

- Obiekty, które przeżyły wyrzucanie elementów bezużytecznych generacji 0, zostały podwyższone do generacji 1.
- Obiekty, które przeżyły wyrzucanie elementów bezużytecznych generacji 1, są podwyższane do generacji 2.
- Obiekty, które przeżyły wyrzucanie elementów bezużytecznych generacji 2, pozostają w generacji 2.

Gdy moduł wyrzucania elementów bezużytecznych wykryje, że stopień przeżycia jest wysoki w generacji, zwiększa próg alokacji dla tej generacji. Następna kolekcja pobiera znaczny rozmiar odzyskiwanej pamięci. Środowisko CLR ciągle równoważy dwa priorytety: nie pozwala to na zbyt duże działanie zestawu roboczego aplikacji przez opóźnione wyrzucanie elementów bezużytecznych i niezezwalanie na zbyt częste uruchamianie wyrzucania elementów bezużytecznych.

### <a name="ephemeral-generations-and-segments"></a>Pokoleń tymczasowych i segmentów

Ponieważ obiekty w generacji 0 i 1 są krótkoterminowe, te generacje są znane jako *generacja tymczasowych*.

Generacje tymczasowe są przydzieleni do segmentu pamięci, który jest znany jako segment tymczasowych. Każdy nowy segment uzyskany przez moduł wyrzucania elementów bezużytecznych stał się nowym segmentem tymczasowych i zawiera obiekty, które przeżyły wyrzucanie elementów bezużytecznych generacji 0. Stary segment tymczasowych zostanie segmentem nowej generacji 2.

Rozmiar segmentu tymczasowych różni się w zależności od tego, czy system jest 32-bitowy, czy 64-bitowy i na typie modułu wyrzucania elementów bezużytecznych, który jest uruchomiony ([stacja robocza lub serwer GC](workstation-server-gc.md)). W poniższej tabeli przedstawiono domyślne rozmiary segmentu tymczasowych.

|Stacja robocza/serwer GC|32-bitowa|64-bitowa|
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

  Zwykle sterta dużego obiektu (LOH) nie jest kompaktowa, ponieważ kopiowanie dużych obiektów nakłada spadek wydajności. Jednak w programie .NET Core i w .NET Framework 4.5.1 i nowszych można użyć <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> właściwości, aby skompaktować stertę dużego obiektu na żądanie. Ponadto LOH jest automatycznie kompaktowana, gdy ustalono limit, określając jedną z:

  - Limit pamięci dla kontenera.
  - Opcje konfiguracji [GCHeapHardLimit](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitcomplus_gcheaphardlimit) lub [GCHeapHardLimitPercent](../../core/run-time-config/garbage-collector.md#systemgcheaphardlimitpercentcomplus_gcheaphardlimitpercent) Run-Time.

Moduł wyrzucania elementów bezużytecznych używa następujących informacji, aby określić, czy obiekty są aktywne:

- Elementy **Główne stosu**. Zmienne stosu udostępniane przez kompilator just-in-Time (JIT) i Analizator stosu. Optymalizacje JIT mogą wydłużać lub skracać regiony kodu, w których zmienne stosu są zgłaszane do modułu wyrzucania elementów bezużytecznych.

- **Dojść do wyrzucania elementów bezużytecznych**. Obsługuje obiekty zarządzane, które mogą być przydzielone przez kod użytkownika lub przez środowisko uruchomieniowe języka wspólnego.

- **Dane statyczne**. Obiekty statyczne w domenach aplikacji, które mogą odwoływać się do innych obiektów. Każda domena aplikacji śledzi swoje obiekty statyczne.

Przed uruchomieniem odzyskiwania pamięci wszystkie zarządzane wątki są zawieszane z wyjątkiem wątku, który wyzwolił wyrzucanie elementów bezużytecznych.

Na poniższej ilustracji przedstawiono wątek wyzwalający wyrzucanie elementów bezużytecznych i powoduje zawieszenie innych wątków.

![Gdy wątek wyzwala odzyskiwanie pamięci](media/gc-triggered.png)

## <a name="unmanaged-resources"></a>Zasoby niezarządzane

W przypadku większości obiektów tworzonych przez aplikację można polegać na wyrzucaniu elementów bezużytecznych w celu automatycznego wykonywania niezbędnych zadań zarządzania pamięcią. Zasoby niezarządzane wymagają jednak jawnego usuwania z pamięci. Najpopularniejszym typem niezarządzanego zasobu jest obiekt opakowujący zasób systemu operacyjnego, taki jak dojście do pliku, uchwyt okna lub połączenie sieciowe. Mimo że moduł wyrzucania elementów bezużytecznych może śledzić okres istnienia zarządzanego obiektu, który hermetyzuje niezarządzany zasób, nie ma konkretnej wiedzy na temat czyszczenia zasobu.

Podczas tworzenia obiektu, który hermetyzuje zasób niezarządzany, zaleca się podanie kodu niezbędnego do oczyszczenia niezarządzanego zasobu w `Dispose` metodzie publicznej. Dostarczając `Dispose` metodę, można umożliwić użytkownikom obiektu jawne zwalnianie pamięci po zakończeniu pracy z obiektem. W przypadku korzystania z obiektu, który hermetyzuje niezarządzany zasób, należy się upewnić, że jest `Dispose` to konieczne.

Należy również udostępnić sposób, aby niezarządzane zasoby były udostępniane na wypadek, gdyby odbiorca Twojego typu zapomnił wywołać `Dispose` . Możesz użyć bezpiecznego dojścia, aby otoczyć niezarządzany zasób, lub zastąpić <xref:System.Object.Finalize?displayProperty=nameWithType> metodę.

Aby uzyskać więcej informacji na temat oczyszczania zasobów niezarządzanych, zobacz [Oczyszczanie zasobów niezarządzanych](unmanaged.md).

## <a name="see-also"></a>Zobacz też

- [Stacja robocza i odzyskiwanie pamięci serwera](workstation-server-gc.md)
- [Odzyskiwanie pamięci w tle](background-gc.md)
- [Opcje konfiguracji dla usługi GC](../../core/run-time-config/garbage-collector.md)
- [Wyrzucanie elementów bezużytecznych](index.md)
