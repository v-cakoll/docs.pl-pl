---
title: Podstawy dotyczące odzyskiwania pamięci
description: Dowiedz się, jak działa moduł odśmiecania pamięci i jak ona skonfigurowana w celu uzyskania optymalnej wydajności.
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
ms.openlocfilehash: 9bb09571ea8c9fb3a6d16a9f16c5269326d7f7da
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712477"
---
# <a name="fundamentals-of-garbage-collection"></a>Podstawy dotyczące odzyskiwania pamięci
<a name="top"></a> W środowisko uruchomieniowe języka wspólnego (CLR) wyrzucanie elementów bezużytecznych działa jako automatycznych Menadżer pamięci. Zapewnia następujące korzyści:  
  
-   Umożliwia projektowanie aplikacji bez konieczności zwalniania pamięci.  
  
-   Efektywnie przydziela obiekty na zarządzanej stercie.  
  
-   Ponownie wzywa obiekty, które są już używane, czyści ich pamięci i utrzymuje dostępne dla przyszłej alokacji pamięci. Zarządzane obiekty automatycznie uzyskują czystą zawartość, więc ich konstruktory nie muszą inicjować wszystkich pól danych.  
  
-   Zapewnia bezpieczeństwo pamięci, upewniając się, że obiekt nie może korzystać zawartość innego obiektu.  
  
 W tym temacie opisano podstawowe pojęcia dotyczące wyrzucania elementów bezużytecznych. 
 
<a name="fundamentals_of_memory"></a>   
## <a name="fundamentals-of-memory"></a>Podstawy pamięci  
 Na poniższej liście podsumowano ważne pojęcia dotyczące pamięci CLR.  
  
-   Każdy proces ma własną, oddzielną wirtualną przestrzeń adresową. Wszystkie procesy na tym samym komputerze udostępnianie tej samej pamięci fizycznej, a następnie Udostępnij plik stronicowania, jeśli taka istnieje.  
  
-   Domyślnie na komputerach 32-bitowych każdy proces ma tryb użytkownika 2 GB wirtualnej przestrzeni adresowej.  
  
-   Jako Deweloper aplikacji pracujesz tylko z wirtualną przestrzenią adresową i nigdy nie manipulujesz pamięci fizycznej bezpośrednio. Moduł odśmiecania pamięci przydziela i zwalnia pamięć wirtualną dla Ciebie na stosie zarządzanym.  
  
     Jeśli piszesz kod natywny używasz funkcji Win32 do pracy z wirtualnej przestrzeni adresowej. Te funkcje alokują i zwalniają pamięć wirtualną dla Ciebie natywnych sterty.  
  
-   Pamięć wirtualna może być w trzech stanach:  
  
    -   Bezpłatnie. Blok pamięci nie ma odwołań do niej i jest dostępny do alokacji.  
  
    -   Zastrzeżone. Blok pamięci jest dostępny do użycia i nie można używać dla innych żądań alokacji. Nie można jednak przechowywać dane w tym bloku pamięci, dopóki nie zostanie zatwierdzony.  
  
    -   Zatwierdzone. Blok pamięci jest przypisany do pamięci fizycznej.  
  
-   Można uzyskać fragmentację wirtualnej przestrzeni adresowej. Oznacza to, że istnieją wolne bloki, znane również jako dziury w przestrzeni adresowej. Gdy wymagana jest alokacja pamięci wirtualnej, Menedżer pamięci wirtualnej musi znaleźć pojedynczy wolny blok, który jest wystarczająco duży, aby spełnić to żądanie alokacji. Nawet jeśli użytkownik ma 2 GB wolnego miejsca, Alokacja wymagająca 2 GB zakończą się niepowodzeniem, chyba że wszystkie tego wolnego miejsca na dysku znajduje się w pojedynczym bloku adresu.  
  
-   Jeśli zabraknie wirtualnej przestrzeni adresowej do zarezerwowania albo przestrzeni fizycznej, aby zatwierdzić, można uruchomić za mało pamięci.  
  
 Pliku stronicowania jest używany, nawet jeśli wykorzystanie pamięci fizycznej (to znaczy, że popyt na pamięć fizyczną) jest niska. Gdy wykorzystanie pamięci fizycznej jest wysokie, po raz pierwszy system operacyjny musi zwolnić miejsce w pamięci fizycznej w celu przechowywania danych i tworzy kopię zapasową niektórych danych, który znajduje się w pamięci fizycznej do pliku stronicowania. Czy dane nie są stronicowane, dopóki nie jest to potrzebne, więc istnieje możliwość napotkania stronicowania w sytuacji, gdy wykorzystanie pamięci fizycznej jest bardzo niskie. 
 
 [Powrót do początku](#top)  
  
<a name="conditions_for_a_garbage_collection"></a>   
## <a name="conditions-for-a-garbage-collection"></a>Warunki dla wyrzucania elementów bezużytecznych  
 Wyrzucanie elementów bezużytecznych występuje, gdy jest spełniony jeden z następujących warunków:  
  
-   System ma mało pamięci fizycznej. Wykryto powiadomienia małej ilości pamięci z systemu operacyjnego lub brakiem pamięci wskazywany przez hosta.
  
-   Pamięć, która jest używana przez alokowane obiekty na stosie zarządzanym przewyższa dopuszczalny próg. Wartość progowa jest stale dopasowywany w trakcie działania procesu.  
  
-   <xref:System.GC.Collect%2A?displayProperty=nameWithType> Metoda jest wywoływana. Prawie we wszystkich przypadkach nie trzeba wywołać tej metody, ponieważ moduł odśmiecania pamięci działa w sposób ciągły. Ta metoda jest używana głównie w unikalnych sytuacjach i testowania.  
  
 [Powrót do początku](#top)  
  
<a name="the_managed_heap"></a>   
## <a name="the-managed-heap"></a>Sterty zarządzanej  
 Po moduł odśmiecania pamięci jest inicjowany przez środowisko CLR, przydzieli on segment pamięci do przechowywania obiektów i zarządzanie nimi. Pamięć ta nosi nazwę zarządzanego stosu, w przeciwieństwie do stosu macierzystego w systemie operacyjnym.  
  
 Brak sterty zarządzanej dla każdego procesu zarządzanego. Wszystkie wątki w procesie przydzielają pamięć dla obiektów, które w tej samej sterty.  
  
 Aby zarezerwować pamięć, moduł zbierający elementy bezużyteczne wywołuje funkcję Win32 [VirtualAlloc](/windows/desktop/api/memoryapi/nf-memoryapi-virtualalloc) funkcji i rezerwuje jeden segment pamięci na raz dla zarządzanych aplikacji. Moduł zbierający elementy bezużyteczne również rezerwuje segmentów zgodnie z potrzebami i zwalnia je do systemu operacyjnego (po wyczyszczeniu ich z wszystkich obiektów) poprzez wywołanie Win32 [VirtualFree](/windows/desktop/api/memoryapi/nf-memoryapi-virtualfree) funkcji.  
  
> [!IMPORTANT]
>  Rozmiar segmentów przydzielonej przez moduł odśmiecania pamięci jest specyficzne dla implementacji i może ulec zmianie w dowolnym momencie, w tym w okresowe aktualizacje. Twoja aplikacja nigdy nie należy wprowadzić założeń dotyczących lub zależeć od rozmiaru określonego segmentu nie ma podejmować skonfigurować ilość pamięci dostępnej dla alokacji segmentu.  
  
 Im mniej obiektów przydzielony na stosie, tym mniej pracy, którego moduł zbierający elementy bezużyteczne musi wykonać. Podczas alokowania obiektów nie należy używać wartości zaokrąglanych w górę, które przekraczają Twoich potrzeb, np. alokować tablicy 32-bitowej, gdy będziesz potrzebować tylko 15 bajtów.  
  
 Po wyzwoleniu wyrzucania elementów bezużytecznych moduł zbierający elementy bezużyteczne odzyskuje pamięć, która jest zajęta przez obiekty martwe. Proces odzyskiwania kompaktuje żywe obiekty tak, że są one przenoszone razem, a martwa przestrzeń jest usuwana, a tym samym czemu stos staje się mniejszy. Dzięki temu, że obiekty, które są alokowane razem, pozostają razem na stosie zarządzanym, aby zachować swoją lokalizację.  
  
 Wszechobecność (częstotliwość i czas trwania) wyrzucania elementów bezużytecznych jest wynikiem ilości alokacji i ilość pamięci przetrwałych na stosie zarządzanym.  
  
 Stos może być traktowany jako akumulacja dwóch stosów: [stertę dużego obiektu](large-object-heap.md) i stosu małych obiektów.  
  
 [Stertę dużego obiektu](large-object-heap.md) zawiera bardzo duże obiekty o rozmiarze 85 000 bajtów i większe. Obiekty na stosie dużego obiektu są zazwyczaj tablicami. To jest rzadkie dla obiektu wystąpienia, żeby był bardzo duży.  
  
 [Powrót do początku](#top)  
  
<a name="generations"></a>   
## <a name="generations"></a>Generacje  
 Stos jest podzielony na generacje, więc może obsługiwać obiekty długo- i krótkotrwałe. Wyrzucanie elementów bezużytecznych występuje przede wszystkim z odzyskiwaniem krótkotrwałych obiektów, które zazwyczaj zajmują tylko niewielką część stosu. Dostępne są trzy generacje obiektów na stosie:  
  
-   **Generacji 0**. To jest najmłodsza generacja i zawiera obiekty krótkotrwałe. Przykładem obiektu krótkotrwałego jest zmienna tymczasowa. Wyrzucanie elementów bezużytecznych występuje najczęściej w tej generacji.  
  
     Nowo przydzielone obiekty tworzą nową generacji obiektów i są niejawną kolekcją kolekcji generacji 0, chyba że są to duże obiekty, w którym to przypadku przejdź na stertę dużego obiektu w kolekcji generacji 2.  
  
     Większość obiektów jest skierowanych do wyrzucania elementów bezużytecznych generacji 0 i nie przeżywa do następnej generacji.  
  
-   **Generacja 1**. Ta generacja zawiera obiekty krótkotrwałe i służy jako bufor między obiektami krótkotrwałe i długotrwałe.  
  
-   **2. generacji**. Ta generacja zawiera długotrwałe obiekty. Przykładem obiektu długotrwałego jest obiekt w aplikacji serwera, który zawiera dane statyczne, żywe czas trwania procesu.  
  
 Wyrzucanie elementów bezużytecznych odbywa się w konkretnych generacjach, jak pozwalają warunki. Zbieranie generacji oznacza zbieranie obiektów w tej generacji oraz młodszych generacjach. Wyrzucanie elementów bezużytecznych generacji 2 jest znany także jako pełne odśmiecanie, ponieważ odzyskuje wszystkie obiekty ze wszystkich pokoleń (to znaczy, wszystkie obiekty w zarządzanym stosie).  
  
### <a name="survival-and-promotions"></a>Pozostawanie w mocy i promocje  
 Obiekty, które nie są odzyskane w wyrzucaniu elementów bezużytecznych są znane jako osoby pozostałe przy życiu i były promowane do następnej generacji. Obiekty, które przeżyły generację 0 wyrzucania elementów bezużytecznych są promowane do generacji 1; obiekty, które przeżyły generację 1 wyrzucania elementów bezużytecznych są promowane do generacji 2; i obiekty, które przeżyły wyrzucania elementów bezużytecznych generacji 2 pozostają w generacji 2.  
  
 W przypadku moduł zbierający elementy bezużyteczne wykryje, że przeżywalność jest wysoka w generacji, zwiększa próg alokacji dla danej generacji, więc kolejnego zbierania pobiera rzeczywisty rozmiar odzyskanej pamięci. Środowisko CLR stale szuka kompromisu między dwoma priorytetami: nie pozwolić aplikacji roboczy get zestaw zbyt duży i nie pozwolić wyrzucania elementów bezużytecznych zajęło zbyt dużo czasu.  
  
### <a name="ephemeral-generations-and-segments"></a>Generacje i segmenty efemeryczne  
 Ponieważ obiekty w generacji 0 i 1 są krótkotrwałe, generacje te są znane jako tymczasowe.  
  
 Generacje efemeryczne muszą być przydzielone w segmencie pamięci określanym jako segment efemeryczny. Każdy nowy segment pozyskany przez moduł odśmiecania pamięci staje się nowym segmentem efemerycznym i zawiera obiekty, które przetrwały generację 0 wyrzucania elementów bezużytecznych. Stary segment efemeryczny staje się nowym segmentem generacji 2.  
  
 Rozmiaru segmentu efemerycznego różni się zależnie od tego, czy system jest 32 - lub 64-bitowy oraz typu modułu zbierającego elementy bezużyteczne, w którym jest uruchomiona. W poniższej tabeli przedstawiono wartości domyślne.  
  
||32-bitowa|64-bitowy|  
|-|-------------|-------------|  
|Stacja robocza GC|16 MB|256 MB|  
|Serwer GC|64 MB|4 GB|  
|Serwer odzyskiwania pamięci z > 4 logiczne procesory CPU|32 MB|2 GB|  
|Serwer GC > 8 procesorów logicznych|16 MB|1 GB|  
  
 Segment efemeryczny może zawierać obiekty generacji 2. Obiekty generacji 2 mogą używać wielu segmentów (tak dużo, ilu dany proces wymaga i umożliwia pamięć).  
  
 Ilość zwolnionej pamięci z efemerycznego wyrzucania elementów bezużytecznych jest ograniczona do rozmiaru segmentu efemerycznego. Ilość zwolnionej pamięci jest proporcjonalna do miejsca zajmowanego przez obiekty martwe.  
  
 [Powrót do początku](#top)  
  
<a name="what_happens_during_a_garbage_collection"></a>   
## <a name="what-happens-during-a-garbage-collection"></a>Co się dzieje podczas wyrzucania elementów bezużytecznych  
 Wyrzucanie elementów bezużytecznych ma następujące etapy:  
  
-   Faza znakowania wyszukuje i tworzy listę wszystkich obiektów żywych.  
  
-   Faza przemieszczania aktualizująca odwołania do obiektów, które zostaną skompaktowane.  
  
-   Faza kompaktowania przejmująca miejsce zajmowane przez obiekty martwe i kompaktująca obiekty zachowywane. Faza kompaktowania przenosi obiekty, które przetrwały wyrzucanie elementów bezużytecznych w kierunku starszego końca segmentu.  
  
     Ponieważ kolekcje geenracji 2 mogą zajmować wiele segmentów, do starszego segmentu można przenosić obiekty, które są promowane do generacji 2. Zarówno generacji 1 i pozostałości generacji 2 można przenieść do innego segmentu, ponieważ są one promowane do generacji 2.  
  
     Zazwyczaj duży obiekt sterty nie skompaktowany, ponieważ kopiowanie dużych obiektów obniża wydajność. Jednakże poczynając od wersji [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], możesz użyć <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> właściwości do kompaktowania sterty dużych obiektów na żądanie.  
  
 Wyrzucanie elementów bezużytecznych używa następujących informacji w celu ustalenia, czy obiekty są żywe:  
  
-   **Zmienne główne stosu**. Zmienne stosu dostarczane przez kompilator programu just-in-time (JIT) oraz walker stosu. Należy pamiętać, że optymalizacje JIT mogą wydłużać lub Skróć regiony kodu w ramach której stosu zmienne są zgłaszane do modułu odśmiecania pamięci.
  
-   **Uchwyty wyrzucania elementów bezużytecznych**. Obsługuje, że wskazują obiekty zarządzane i które można przypisać przez kod użytkownika lub przez środowisko uruchomieniowe języka wspólnego.  
  
-   **Dane statyczne**. Obiekty statyczne w domenach aplikacji, które mogłyby odwoływać się do innych obiektów. Każda domena aplikacji śledzi informacje o swoich obiektach statycznych.  
  
 Zanim rozpocznie się wyrzucanie elementów bezużytecznych, wszystkie zarządzane wątki są zawieszane, z wyjątkiem wątku, który wyzwolił wyrzucanie elementów bezużytecznych.  
  
 Poniższa ilustracja przedstawia wątek, który wyzwala wyrzucanie elementów bezużytecznych i powoduje, że inne wątki zostają wstrzymane.  
  
 ![Kiedy wątek wyzwala wyrzucanie elementów bezużytecznych](../../../docs/standard/garbage-collection/media/gc-triggered.png "GC_Triggered")  
Wątek, który wyzwala wyrzucanie elementów bezużytecznych  
  
 [Powrót do początku](#top)  
  
<a name="manipulating_unmanaged_resources"></a>   
## <a name="manipulating-unmanaged-resources"></a>Manipulowanie niezarządzanymi zasobami  
 Jeśli zarządzane obiekty odwołują się do niezarządzanych obiektów za pomocą ich macierzystych uchwytów plików, trzeba jawnie zwolnić niezarządzane obiekty, ponieważ wyrzucanie elementów bezużytecznych śledzi pamięć tylko w zarządzanym stosie.  
  
 Użytkownicy zarządzanego obiektu nie mogą dysponować macierzystymi zasobami używanymi przez obiekt. Aby wykonać oczyszczanie, można wprowadzić zarządzany obiekt sfinalizowania. Finalizacja składa się z akcji oczyszczania, które należy wykonać, gdy obiekt nie jest już używana. Gdy zarządzany obiekt jest niszczony, wykonuje akcje czyszczenia, które są określone w jego metodzie finalizacji.  
  
 Obiekt sfinalizowania zostanie odnalezione to martwy, jego finalizator jest umieszczany w kolejce, dzięki czemu jego akcje oczyszczania są wykonywane, ale sam obiekt zostanie podwyższony do następnej generacji. W związku z tym, należy poczekać, aż do następnego wyrzucania elementów bezużytecznych występuje w tej generacji (które niekoniecznie jest następnego wyrzucania elementów bezużytecznych) do określenia, czy obiekt został odzyskany.  
  
 [Powrót do początku](#top)  
  
<a name="workstation_and_server_garbage_collection"></a>   
## <a name="workstation-and-server-garbage-collection"></a>Wyrzucanie elementów bezużytecznych stacji roboczych i serwera  
 Wyrzucanie elementów bezużytecznych samodzielnie się Dostraja i może pracować w wielu różnych scenariuszach. Można użyć ustawienia pliku konfiguracyjnego, aby ustawić typ wyrzucania elementów bezużytecznych bazujący na charakterystyce obciążenia. Środowisko CLR oferuje następujące typy operacji wyrzucania elementów bezużytecznych:  
  
-   Wyrzucanie elementów bezużytecznych dla stacji roboczych, dla wszystkich klienckich stacji roboczych i komputerów stacjonarnych. Jest to domyślne ustawienie dla [ \<gcserver — > element](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) w schemacie konfiguracji środowiska uruchomieniowego.  
  
     Wyrzucanie elementów bezużytecznych może być współbieżnych lub niewspółbieżnie. Współbieżne wyrzucanie elementów bezużytecznych umożliwia zarządzanym wątkom kontynuowanie operacji podczas wyrzucania elementów bezużytecznych.  
  
     Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], wyrzucanie elementów bezużytecznych w tle zastępuje współbieżne wyrzucanie elementów bezużytecznych.  
  
-   Wyrzucanie elementów bezużytecznych serwera, który jest przeznaczony dla aplikacji serwera wymagających wysokiej przepływności i skalowalności. Wyrzucanie elementów bezużytecznych serwera może być niewspółbieżne lub w tle.  
  
 Poniższa ilustracja przedstawia dedykowane wątki, które wykonują wyrzucania elementów bezużytecznych na serwerze.  
  
 ![Wątków serwer wyrzucania elementów bezużytecznych](../../../docs/standard/garbage-collection/media/gc-server.png "GC_Server")  
Wyrzucanie elementów bezużytecznych serwera  
  
### <a name="configuring-garbage-collection"></a>Konfigurowanie wyrzucania elementów bezużytecznych  
 Możesz użyć [ \<gcserver — > element](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) schematu konfiguracji środowiska uruchomieniowego, aby określić typ wyrzucania elementów bezużytecznych ma CLR do wykonania. Gdy ten element `enabled` ma ustawioną wartość atrybutu `false` (ustawienie domyślne), CLR wykonuje wyrzucanie elementów bezużytecznych. Po ustawieniu `enabled` atrybutu `true`, CLR wykonuje wyrzucanie elementów bezużytecznych serwera.  
  
 Współbieżne wyrzucanie elementów bezużytecznych jest określony za pomocą [ \<gcconcurrent — > element](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) schematu konfiguracji środowiska uruchomieniowego. Ustawieniem domyślnym jest `enabled`. To ustawienie kontroluje zarówno równolegle i wyrzucania elementów bezużytecznych w tle.  
  
 Można również określić serwer wyrzucania elementów bezużytecznych z niezarządzanymi interfejsami hostowania. Należy pamiętać, że program ASP.NET i programu SQL Server umożliwiają wyrzucanie elementów bezużytecznych serwera automatycznie, jeśli aplikacja jest hostowana w jednym z tych środowisk.  
  
### <a name="comparing-workstation-and-server-garbage-collection"></a>Porównywanie wyrzucania elementów bezużytecznych stacji roboczych i serwera  
 Poniżej przedstawiono zagadnienia wielowątkowości i wydajności dotyczące wyrzucania elementów bezużytecznych dla stacji roboczych:  
  
-   Zbieranie odbywa się w wątku użytkownika, który wyzwolił wyrzucanie elementów bezużytecznych i pozostaje na tym samym priorytecie. Ponieważ wątki użytkownika zwykle działają przy normalnym priorytecie, moduł odśmiecania pamięci (który jest uruchamiany na wątku o normalnym priorytecie) musi rywalizować z innymi wątkami o czas Procesora.  
  
     Wątki uruchamiające kod macierzysty nie zostają zawieszone.  
  
-   Wyrzucanie elementów bezużytecznych jest zawsze używana na komputerze, który ma tylko jeden procesor, bez względu na to [ \<gcserver — >](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) ustawienie. Jeśli określisz wyrzucania elementów bezużytecznych dla serwera, środowisko CLR używa wyrzucania elementów bezużytecznych dla stacji roboczych ze współbieżnością wyłączoną.  
  
 Zagadnienia wielowątkowości i wydajności dotyczące wyrzucania elementów bezużytecznych dla serwera są następujące:  
  
-   Zbieranie odbywa się w wielu dedykowanych wątkach, które są uruchomione w `THREAD_PRIORITY_HIGHEST` poziom priorytetu.  
  
-   Dedykowany wątek służący do wyrzucania elementów bezużytecznych oraz sterta są zapewniane dla każdego Procesora, a sterty są zbierane w tym samym czasie. Każdy stos zawiera stos małych obiektów i stos dużych obiektów i wszystkich stosów jest możliwy przez kod użytkownika. Obiekty na różnych stertach mogą odwoływać się do siebie nawzajem.  
  
-   Ponieważ wiele wątków wyrzucania elementów bezużytecznych współpracuje ze sobą, wyrzucanie elementów bezużytecznych serwera jest szybsze niż wyrzucanie elementów bezużytecznych na tej samej wielkości sterty.  
  
-   Wyrzucanie elementów bezużytecznych serwera często ma segmenty o większych rozmiarach. Należy jednak pamiętać, że jest to tylko generalizacji: rozmiar segmentu jest specyficzne dla implementacji i może ulec zmianie. Powinien zawierać żadnych założeń o rozmiarze segmentów przydzielone przez moduł odśmiecania pamięci podczas dostosowywania aplikacji.  
  
-   Wyrzucanie elementów bezużytecznych serwera może znacznie obciążać zasoby. Na przykład jeśli masz 12 procesów uruchomionych na komputerze, który ma 4 procesory, nastąpi 48 wątków kolekcji dedykowanej pamięci Jeśli wszystkie używają wyrzucanie elementów bezużytecznych serwera. W sytuacji wysokiego obciążenia pamięci Jeśli wszystkie procesy zaczną wyrzucać wyrzucanie elementów bezużytecznych, wyrzucanie elementów bezużytecznych będzie miał 48 wątków do zaplanowania.  
  
 Jeśli korzystasz z setek wystąpień aplikacji, należy wziąć pod uwagę przy użyciu stacji roboczej wyrzucania elementów bezużytecznych z współbieżne wyrzucanie elementów bezużytecznych wyłączone. To spowoduje mniej przełączania kontekstu, co może zwiększyć wydajność.  
  
 [Powrót do początku](#top)  
  
<a name="concurrent_garbage_collection"></a>   
## <a name="concurrent-garbage-collection"></a>Współbieżne wyrzucanie elementów bezużytecznych  
 W stacji roboczej lub serwerze wyrzucanie elementów bezużytecznych można włączyć równoczesne odśmiecanie, która pozwala wątkom z dedykowanego wątku, który wykonuje wyrzucania elementów bezużytecznych przez większość czasu trwania kolekcji działać. Ta opcja dotyczy tylko wyrzucania elementów bezużytecznych w generacji 2; generacje 0 i 1 są zawsze niewspółbieżne, ponieważ kończą się bardzo szybko.  
  
 Współbieżne wyrzucanie elementów bezużytecznych umożliwia większą responsywność poprzez zminimalizowanie przerw dla kolekcji aplikacji interaktywnych. Zarządzanych wątkami można kontynuować do uruchamiania w większości przypadków przy uruchomionym wątku kolekcji wyrzucania. Skutkuje to krótszymi przerwami podczas wyrzucania elementów bezużytecznych.  
  
 Aby zwiększyć wydajność, po uruchomieniu kilka procesów, należy wyłączyć współbieżne wyrzucanie elementów bezużytecznych. Można to zrobić, dodając [ \<gcconcurrent — > element](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) do pliku konfiguracji aplikacji i ustawiając wartość jej `enabled` atrybutu `"false"`.  
  
 Współbieżne wyrzucanie elementów bezużytecznych jest wykonywane na dedykowanym wątku. Domyślnie środowisko CLR uruchamia wyrzucanie elementów bezużytecznych współbieżne wyrzucanie elementów bezużytecznych włączone. Ta zasada obowiązuje dla komputerów z jednym procesorem i wieloprocesorowych.  
  
 Możliwość przydzielania małych obiektów na stercie podczas równoczesnego wyrzucania elementów bezużytecznych jest ograniczona przez obiekty pozostawione w segmencie efemerycznym podczas uruchamiania równoczesnego wyrzucania elementów bezużytecznych. Zaraz po osiągnięciu końca odcinka, trzeba będzie poczekać współbieżne wyrzucanie elementów bezużytecznych zakończyć, gdy są wstrzymywane zarządzanych wątkach, które trzeba wprowadzać alokacje małych obiektów.  
  
 Współbieżne wyrzucanie elementów bezużytecznych ma nieco większy zestaw roboczy (w porównaniu z niewspółbieżnym wyrzucaniem elementów bezużytecznych), ponieważ zapewnia możliwość alokowania obiektów podczas wyrzucania współbieżnego. Jednak może to wpłynąć na wydajność, ponieważ obiekty, które są przydzielane stają się częścią zestawu roboczego. Zasadniczo równoczesne wyrzucanie elementów bezużytecznych zamienia niektóre procesora CPU i pamięci na krótsze przerwy.  
  
 Poniższa ilustracja przedstawia współbieżne wyrzucanie elementów bezużytecznych wykonywane w osobnym dedykowanym wątku.  
  
 ![Wątków równoczesne wyrzucania elementów bezużytecznych](../../../docs/standard/garbage-collection/media/gc-concurrent.png "GC_Concurrent")  
Współbieżne wyrzucanie elementów bezużytecznych  
  
 [Powrót do początku](#top)  
  
<a name="background_garbage_collection"></a>   
## <a name="background-workstation-garbage-collection"></a>Tło wyrzucanie elementów bezużytecznych  
 W tle wyrzucanie elementów bezużytecznych generacje efemeryczne (0 i 1) są zbierane zgodnie z potrzebami w trakcie wyrzucania generacji 2. Nie ma żadnego ustawienia dotyczącego wyrzucania elementów bezużytecznych w tle; jest włączany automatycznie za pomocą współbieżne wyrzucanie elementów bezużytecznych. Wyrzucanie elementów bezużytecznych w tle jest zamiennikiem współbieżne wyrzucanie elementów bezużytecznych. Za pomocą współbieżne wyrzucanie elementów bezużytecznych, wyrzucania elementów bezużytecznych w tle odbywa się na dedykowanym wątku i ma zastosowanie tylko do kolekcji generacji 2.  
  
> [!NOTE]
>  Wyrzucanie elementów bezużytecznych w tle jest dostępne tylko w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] i nowszych wersjach. W [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], jest ona obsługiwana tylko w przypadku wyrzucanie elementów bezużytecznych. Począwszy od programu .NET Framework 4.5, wyrzucanie elementów bezużytecznych w tle jest dostępna dla wyrzucania elementów bezużytecznych stacji roboczej i serwerze.  
  
 Kolekcja pokoleń efemerycznych powstająca podczas wyrzucania elementów bezużytecznych w tle jest określany jako pierwszego wyrzucania elementów bezużytecznych. Po wystąpieniu wyrzucania pierwszego planu, wszystkie zarządzane wątki są wstrzymywane.  
  
 Gdy wyrzucanie elementów bezużytecznych w tle jest w toku i wystarczająca liczba obiektów została przydzielona w generacji 0, CLR wykonuje generacji 0 lub 1 wyrzucenia elementów bezużytecznych generacji. Wątku dedykowanego wyrzucania elementów bezużytecznych sprawdza częste punkty bezpieczeństwa w celu ustalenia, czy ma żądania wyrzucenia elementów bezużytecznych. Jeśli, zbieranie w tle zawiesza się tak, aby pierwszego wyrzucania elementów bezużytecznych może wystąpić. Po zakończeniu pierwszego wyrzucania elementów bezużytecznych wznowienie wątku dedykowanego wyrzucania elementów bezużytecznych i wątki użytkownika.  
  
 Wyrzucanie elementów bezużytecznych w tle usuwa ograniczenia alokacji nałożone przez współbieżne wyrzucanie elementów bezużytecznych, ponieważ tymczasowe wyrzucanie elementów bezużytecznych może wystąpić podczas wyrzucanie elementów bezużytecznych w tle. Oznacza to, że wyrzucania elementów bezużytecznych w tle może usunąć obiekty martwe w generacje efemeryczne i może także zwiększyć na stosie, w razie potrzeby podczas generację 1 wyrzucania elementów bezużytecznych.  
  
 Na poniższej ilustracji przedstawiono bezużytecznych w tle wykonywane w osobnym dedykowanym wątku na stacji roboczej.  
  
 ![Wyrzucanie elementów bezużytecznych w tle](../../../docs/standard/garbage-collection/media/backgroundworkstn.png "BackgroundWorkstn")  
Tło wyrzucanie elementów bezużytecznych  
  
 [Powrót do początku](#top)  
  
<a name="background_server_garbage_collection"></a>   
## <a name="background-server-garbage-collection"></a>Tło serwer wyrzucania elementów bezużytecznych  
 Począwszy od programu .NET Framework 4.5, wyrzucanie elementów bezużytecznych serwera tła jest to domyślny tryb wyrzucanie elementów bezużytecznych serwera. Aby wybrać ten tryb, ustaw `enabled` atrybutu [ \<gcserver — > element](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) do `true` w schemacie konfiguracji środowiska uruchomieniowego. Ten tryb działa podobnie do tła wyrzucanie elementów bezużytecznych, opisanego w poprzedniej sekcji, ale istnieje kilka różnic. Tle wyrzucanie elementów bezużytecznych używa jednego dedykowanego wątku wyrzucania elementów bezużytecznych, natomiast w tle wyrzucanie elementów bezużytecznych dla serwera korzysta z wielu wątków, zazwyczaj z dedykowanego wątku dla każdego procesora logicznego. W przeciwieństwie do stacji roboczej tła wątku wyrzucania elementów bezużytecznych te wątki nie mają limitu czasu.  
  
 Na poniższej ilustracji przedstawiono bezużytecznych w tle wykonywane w osobnym dedykowanym wątku na serwerze.  
  
 ![Serwer wyrzucania elementów bezużytecznych w tle](../../../docs/standard/garbage-collection/media/backgroundserver.png "BackgroundServer")  
Tło serwer wyrzucania elementów bezużytecznych  
  
## <a name="see-also"></a>Zobacz także

- [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
