---
title: Podstawy dotyczące odzyskiwania pamięci
ms.date: 03/30/2017
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
ms.openlocfilehash: d4dd3e16edae6e30d93083694a2d2d18c0815933
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="fundamentals-of-garbage-collection"></a>Podstawy dotyczące odzyskiwania pamięci
<a name="top"></a> W środowisko uruchomieniowe języka wspólnego (CLR) moduł zbierający elementy bezużyteczne służy jako Menedżer pamięci automatycznego. Zapewnia następujące korzyści:  
  
-   Umożliwia projektowanie aplikacji bez konieczności zwolnić pamięć.  
  
-   Przydziela wydajnie obiektów na stercie zarządzanej.  
  
-   Zwraca obiekty, które są już używane, czyści ich pamięci i będzie dostępna dla przyszłych alokacji pamięci. Zarządzanych obiektów automatycznie pobieranie zawartości czystego, więc ich konstruktory nie można zainicjować wszystkich pól danych.  
  
-   Zapewnia bezpieczeństwo pamięci, upewniając się, że obiekt nie może korzystać z zawartości innego obiektu.  
  
 W tym temacie opisano podstawowe koncepcje operacji wyrzucania elementów bezużytecznych. Ten temat zawiera następujące sekcje:  
  
-   [Podstawy dotyczące odzyskiwania pamięci](#fundamentals_of_memory)  
  
-   [Warunki dotyczące wyrzucania elementów bezużytecznych](#conditions_for_a_garbage_collection)  
  
-   [Sterta zarządzana](#the_managed_heap)  
  
-   [Generacje](#generations)  
  
-   [Co się dzieje podczas wyrzucania elementów bezużytecznych](#what_happens_during_a_garbage_collection)  
  
-   [Manipulowanie zasoby niezarządzane](#manipulating_unmanaged_resources)  
  
-   [Wyrzucanie elementów bezużytecznych stacji roboczej i serwera](#workstation_and_server_garbage_collection)  
  
-   [Współbieżne odzyskiwanie pamięci](#concurrent_garbage_collection)  
  
-   [Odzyskiwanie pamięci w tle stacji roboczej](#background_garbage_collection)  
  
-   [Odzyskiwanie pamięci w tle serwera](#background_server_garbage_collection)  
  
<a name="fundamentals_of_memory"></a>   
## <a name="fundamentals-of-memory"></a>Podstawy dotyczące odzyskiwania pamięci  
 Poniższa lista zawiera podsumowanie ważnych pojęć pamięci środowiska CLR.  
  
-   Każdy proces ma własną, oddzielne wirtualnej przestrzeni adresowej. Wszystkie procesy na tym samym komputerze udostępnianie tego samego pamięci fizycznej i udostępnić plik stronicowania, jeśli istnieje.  
  
-   Domyślnie na komputerach z 32-bitowy każdy proces ma trybu użytkownika 2 GB wirtualnej przestrzeni adresowej.  
  
-   Jako Deweloper aplikacji działa tylko z wirtualnej przestrzeni adresowej i nigdy nie manipulowania bezpośrednio pamięci fizycznej. Moduł zbierający elementy bezużyteczne przydziela i zwalnia pamięć wirtualna dla Ciebie na stercie zarządzanej.  
  
     Podczas pisania kodu natywnego używasz funkcji Win32 do pracy z wirtualnej przestrzeni adresowej. Te funkcje przydzielić oraz o wolnym pamięci wirtualnej dla Ciebie na native sterty.  
  
-   Ilość pamięci wirtualnej mogą mieć trzy stany:  
  
    -   Wolne. Blok pamięci nie ma odwołań do niego i jest dostępne do alokacji.  
  
    -   Zastrzeżone. Blok pamięci jest dostępna do użycia i nie można używać dla innych żądań alokacji. Jednak nie można zapisać danych do tego bloku pamięci, dopóki nie zostanie zatwierdzone.  
  
    -   Zatwierdzone. Blok pamięci jest przypisany do magazynu fizycznego.  
  
-   Można pobrać fragmentacji wirtualnej przestrzeni adresowej. Oznacza to, że istnieją wolnego blokuje, znanej także jako luk w przestrzeni adresowej. Po zażądaniu alokacji pamięci wirtualnej Menedżer pamięci wirtualnej musi znaleźć bloku wolnego pojedynczego jest wystarczająco duży, aby spełnić to żądanie alokacji. Nawet jeśli 2 GB wolnego miejsca, alokacji, który wymaga 2 GB zakończy się niepowodzeniem, chyba że wszystkie wolnego miejsca w bloku jeden adres.  
  
-   Za mało pamięci można uruchomić po uruchomieniu poza wirtualnej przestrzeni adresowej do zarezerwowania lub fizycznego miejsca do zatwierdzenia.  
  
 Plik strony jest używany, nawet jeśli wykorzystania pamięci fizycznej (to znaczy zapotrzebowanie na pamięć fizyczna) jest niska. Przy pierwszym uruchomieniu programu wykorzystania pamięci fizycznej jest wysoka, system operacyjny musi zwolnienia miejsca w pamięci fizycznej do przechowywania danych, a kopię zapasową niektórych danych, który znajduje się w pamięci fizycznej do pliku stronicowania. Czy dane nie jest stronicowana aż nie jest konieczne, więc można napotkać stronicowania w sytuacjach, gdy jest bardzo niskie wykorzystanie pamięci fizycznej. 
 
 [Powrót do początku](#top)  
  
<a name="conditions_for_a_garbage_collection"></a>   
## <a name="conditions-for-a-garbage-collection"></a>Warunki dotyczące wyrzucania elementów bezużytecznych  
 Wyrzucanie elementów bezużytecznych występuje, gdy spełniony jest jeden z następujących warunków:  
  
-   System jest mało dostępnej pamięci fizycznej. Wykryto powiadomienia małej ilości pamięci z systemu operacyjnego lub braku pamięci wskazanych przez hosta.
  
-   Pamięci, która jest używana przez obiekty przydzielone na stercie zarządzanej przekracza dopuszczalną wartość progową. Wartość progu stale tak, jak proces działa.  
  
-   <xref:System.GC.Collect%2A?displayProperty=nameWithType> Metoda jest wywoływana. W większości przypadków nie trzeba wywołać tę metodę, ponieważ moduł garbage collector działa w sposób ciągły. Ta metoda jest używana głównie do sytuacji unikatowy i testowania.  
  
 [Powrót do początku](#top)  
  
<a name="the_managed_heap"></a>   
## <a name="the-managed-heap"></a>Sterta zarządzana  
 Po zainicjowaniu moduł garbage collector przez środowisko CLR przydziela segment pamięci do przechowywania obiektów i zarządzanie nimi. Ta pamięć jest nazywany sterty zarządzanej, w przeciwieństwie do natywnej sterty w systemie operacyjnym.  
  
 Brak sterty zarządzanej dla każdego procesu zarządzanego. Wszystkie wątki w procesie przydzielić pamięci dla obiektów w tym samym stosie.  
  
 Aby zarezerwować pamięci, moduł zbierający elementy bezużyteczne wywołuje Win32 [VirtualAlloc](https://msdn.microsoft.com/library/aa366887.aspx) funkcji i jeden segment rezerwy pamięci w czasie zarządzanych aplikacji. Moduł zbierający elementy bezużyteczne również rezerwuje segmentów zgodnie z potrzebami i zwalnia segmentów do systemu operacyjnego (po wyczyszczenie je wszystkie obiekty) przez wywołanie Win32 [VirtualFree](https://msdn.microsoft.com/library/aa366892.aspx) funkcji.  
  
> [!IMPORTANT]
>  Rozmiar segmentów przydzielone przez moduł garbage collector jest konkretnej implementacji i może ulec zmianie w dowolnym momencie, w tym w okresowych aktualizacji. Aplikacji nigdy nie może dokonać założeń dotyczących lub zależą od rozmiaru określonego segmentu nie powinny podejmować próby skonfiguruj ilość pamięci dostępnej dla segmentu alokacji.  
  
 Mniej obiektów przydzielony na stosie mniej pracy przez moduł garbage collector zrobić. Podczas alokowania obiektów, nie należy używać wartości zaokrągloną w górę, które przekraczają potrzeb, takich jak przydzielanie tablicę bajtów 32, gdy będziesz potrzebować tylko 15 bajtów.  
  
 Po wyzwoleniu wyrzucania elementów bezużytecznych moduł garbage collector zwraca pamięci, która jest zajęta przez obiekty martwy. Proces reclaiming kompaktuje obiekty na żywo, aby zostały przeniesione ze sobą i martwy miejsca zostanie usunięty, dzięki czemu mniejsze sterty. Zapewnia to, że obiekty, które są ze sobą przydzielone razem pozostają na stercie zarządzanej w celu zachowania ich lokalizacji.  
  
 Intrusiveness (częstotliwości i czasu używania) wyrzucania jest wynik woluminu alokacji i ilość pamięci udało przetrwać na stercie zarządzanej.  
  
 Sterty można uznać za sumą dwóch stosów: sterty dużego obiektu i sterty małego obiektu.  
  
 Sterty dużego obiektu zawiera bardzo dużych obiektów, które są 85,000 bajtów i większych. Obiekty, dla sterty dużego obiektu są zazwyczaj tablic. Jest rzadko wystąpienia obiektu być bardzo duże.  
  
 [Powrót do początku](#top)  
  
<a name="generations"></a>   
## <a name="generations"></a>Generacje  
 Stos jest podzielony na generacje, więc może obsługiwać obiektów długotrwałe i krótkim okresie. Wyrzucanie elementów bezużytecznych dotyczy głównie odzyskiwanie danych w krótkim okresie obiektów, które zwykle zajmują tylko niewielką częścią sterty. Dostępne są trzy generacje obiektów na stercie:  
  
-   **Generacji 0**. To jest najmłodszego generowania i zawiera obiekty krótkim okresie. Przykład krótkim okresie obiektu to zmiennej tymczasowej. Wyrzucanie elementów bezużytecznych występuje najczęściej w tym pokoleniu.  
  
     Nowo przydzielone obiekty tworzą nowej generacji obiektów i są niejawnie kolekcje pokolenia 0, chyba że są one dużych obiektów, w którym to przypadku przejdź na sterty dużego obiektu w kolekcji generacji 2.  
  
     Większość obiektów odzyskane do pamięci w pokoleniu 0, a po następnej generacji.  
  
-   **Generacja 1**. Tej generacji zawiera obiekty krótkim okresie i pełni rolę bufora między obiektami krótkim okresie i długotrwałe.  
  
-   **Generacja 2**. Tej generacji zawiera obiekty długotrwałe. Przykład długotrwałe obiekt jest obiektem w aplikacji serwera, który zawiera dane statyczne, która działa w czasie trwania procesu.  
  
 Wyrzucanie elementów bezużytecznych występować w określonej generacji gwarantuje warunków. Zbieranie generacji oznacza zbierania obiektów w tej generacji i wszystkie jego młodszych generacji. Wyrzucania elementów bezużytecznych generacji 2 jest nazywana pełnego wyrzucania elementów bezużytecznych, ponieważ jego zwraca wszystkie obiekty w wszystkich generacji (to znaczy, że wszystkie obiekty w stercie zarządzanej).  
  
### <a name="survival-and-promotions"></a>Surwiwalowy i promocjach  
 Obiekty, które nie zostały odzyskane w wyrzucania elementów bezużytecznych są określane jako przy życiu i awansowane na nowej generacji. Obiekty, które pozostają aktualne po generacji 0 wyrzucania elementów bezużytecznych awansowane na pokolenie 1; obiekty, które pozostają aktualne po generacji 1 wyrzucania elementów bezużytecznych awansowane na pokolenie 2; i obiekty, które pozostają aktualne po wyrzucania elementów bezużytecznych generacji 2 pozostają w generacji 2.  
  
 Gdy moduł garbage collector wykryje, że szybkość przetrwania jest wysoka w generacji, zwiększa próg alokacji dla tej generacji, dlatego dalej kolekcji pobiera znacznej rozmiar pamięci regeneracji. CLR stale równoważy dwóch priorytety: nie pozwolić aplikacji roboczy get zestaw zbyt duże i nie umożliwienie wyrzucanie elementów bezużytecznych zbyt dużo czasu.  
  
### <a name="ephemeral-generations-and-segments"></a>Generacje tymczasowych i segmentów  
 Ponieważ obiektów generacji 0 i 1 są krótkim okresie, generacje te są nazywane generacje tymczasowych.  
  
 Generacje tymczasowych musi zostać alokowany w segmencie pamięci, znany jako tymczasowych segmentu. Każdy nowy segment uzyskaną przez moduł garbage collector staje się nowy segment tymczasowych i zawiera obiekty, które udało przetrwać generacji 0 wyrzucania elementów bezużytecznych. Stary segmentu tymczasowych staje się segment nowej generacji 2.  
  
 Rozmiar segmentu tymczasowych różni się w zależności od, czy system jest 32 - lub 64-bitowych i w typie modułu zbierającego elementy bezużyteczne, który jest uruchomiony. W poniższej tabeli przedstawiono wartości domyślne.  
  
||32-bitowa|64-bitowy|  
|-|-------------|-------------|  
|Stacja robocza GC|16 MB|256 MB|  
|Serwer wykazu Globalnego|64 MB|4 GB|  
|Serwer wykazu Globalnego o > 4 procesorów logicznych|32 MB|2 GB|  
|Serwer wykazu Globalnego o > 8 procesorów logicznych|16 MB|1 GB|  
  
 Segment tymczasowych może zawierać obiekty generacji 2. Obiekty generacji 2 można użyć wielu segmentach (dowolną liczbę wymaga proces i umożliwia pamięci).  
  
 Ilość pamięci zwolnionych od tymczasowych wyrzucanie elementów bezużytecznych jest ograniczona do rozmiar segmentu tymczasowych. Ilość pamięci, która zostanie zwolniona jest proporcjonalny do obszaru był zajęty przez obiekty martwy.  
  
 [Powrót do początku](#top)  
  
<a name="what_happens_during_a_garbage_collection"></a>   
## <a name="what-happens-during-a-garbage-collection"></a>Co się dzieje podczas wyrzucania elementów bezużytecznych  
 Wyrzucanie elementów bezużytecznych zawiera następujące etapy:  
  
-   Faza oznaczanie, które wyszukuje i tworzy listę wszystkich obiektów na żywo.  
  
-   Faza przemieszczenie aktualizacji odwołania do obiektów, które będą skompaktować.  
  
-   Faza kompaktowanie, która zwraca miejsce zajmowane przez martwy obiektów i kompaktowanie sprawny obiektów. Fazy kompaktowania przenosi obiekty, które mają udało przetrwać wyrzucania elementów bezużytecznych do starszych końca segmentu.  
  
     Ponieważ kolekcje generacji 2 mogą zajmować wiele segmentów, obiekty, które zostały awansowane w generacji 2 można przenieść do starszych segmentu. Zarówno generacji 1 i generacji 2 przy życiu można przenieść do innego segmentu, ponieważ są awansowane na pokolenie 2.  
  
     Zwykle sterty dużego obiektu jest nie kompaktowanie, ponieważ kopiowanie dużych obiektów obniża wydajność. Jednak począwszy [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], można użyć <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> właściwości kompaktowania sterty dużych obiektów na żądanie.  
  
 Moduł zbierający elementy bezużyteczne używa następujących informacji, aby określić, czy obiekty są na żywo:  
  
-   **Stos katalogów głównych**. Zmienne stosu just in time (JIT) kompilatora i walkera stosu.  
  
-   **Uchwyty kolekcji Garbage**. Obsługuje, że punkt do obiektów zarządzanych oraz czy można przypisać przez kod użytkownika lub przez środowisko uruchomieniowe języka wspólnego.  
  
-   **Dane statyczne**. Statycznych obiektów w domenach aplikacji, które można odwoływać się do innych obiektów. Każda domena aplikacji przechowuje informacje o jego statycznych obiektów.  
  
 Przed rozpoczęciem wyrzucania elementów bezużytecznych, wszystkie wątki zarządzane są wstrzymywane, z wyjątkiem wątku, który wywołał wyrzucanie elementów bezużytecznych.  
  
 Na poniższej ilustracji przedstawiono wątku, który wyzwala wyrzucania elementów bezużytecznych i powoduje, że inne wątki zostanie zawieszona.  
  
 ![Gdy wątek wyzwala wyrzucania elementów bezużytecznych](../../../docs/standard/garbage-collection/media/gc-triggered.png "GC_Triggered")  
Wątek, który wyzwala wyrzucania elementów bezużytecznych  
  
 [Powrót do początku](#top)  
  
<a name="manipulating_unmanaged_resources"></a>   
## <a name="manipulating-unmanaged-resources"></a>Manipulowanie zasoby niezarządzane  
 Jeśli zarządzanych obiektów odwołują się niezarządzane obiekty przy użyciu ich dojścia do plików natywnych, musisz jawnie Zwolnij niezarządzane obiekty, ponieważ moduł garbage collector śledzi pamięci tylko na stercie zarządzanej.  
  
 Użytkownicy obiektu zarządzanego nie może usunąć natywne zasoby używane przez obiekt. Aby wykonać oczyszczanie, możesz wprowadzić zarządzanego obiektu finalizable. Finalizacji składa się z akcji oczyszczania, które można wykonywać, gdy obiekt jest już używana. Po zaniku obiekt zarządzany, wykonuje akcji oczyszczania, które są określone metody finalizatora.  
  
 Finalizable obiekt zostanie odnaleziony za martwy, jego finalizatora jest umieszczany w kolejce, dzięki czemu jego akcje czyszczenia są wykonywane, ale sam obiekt jest podwyższany do nowej generacji. W związku z tym należy poczekać, aż do następnego wyrzucanie elementów bezużytecznych, która występuje na tej generacji (który nie musi być dalej wyrzucanie elementów bezużytecznych) do określenia, czy obiekt została odzyskana.  
  
 [Powrót do początku](#top)  
  
<a name="workstation_and_server_garbage_collection"></a>   
## <a name="workstation-and-server-garbage-collection"></a>Wyrzucanie elementów bezużytecznych stacji roboczej i serwera  
 Moduł zbierający elementy bezużyteczne to dostrajana i może działać w wielu różnych scenariuszach. Ustawienie pliku konfiguracji umożliwia Ustaw typ operacji wyrzucania elementów bezużytecznych oparte na cechy obciążenia. Środowisko CLR zapewnia następujące typy operacji wyrzucania elementów bezużytecznych:  
  
-   Odzyskiwanie pamięci na stacji roboczej, dla wszystkich klienckich stacjach roboczych i komputerach autonomicznych. Jest to domyślne ustawienie dla [ \<gcserver — > elementu](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) w schemacie konfiguracji środowiska wykonawczego.  
  
     Odzyskiwanie pamięci na stacji roboczej może być równoczesnych lub niewspółbieżnego. Współbieżne odzyskiwanie pamięci umożliwia zarządzanych wątków, aby kontynuować operacje podczas wyrzucania elementów bezużytecznych.  
  
     Począwszy od [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], odzyskiwanie pamięci w tle zastępuje współbieżne odzyskiwanie pamięci.  
  
-   Odzyskiwanie pamięci na serwerze, który jest przeznaczony dla aplikacji serwerowych, które wymagają wysokiej wydajności i skalowalności. Odzyskiwanie pamięci na serwerze można niewspółbieżnego lub w tle.  
  
 Na poniższej ilustracji przedstawiono dedykowanych wątków, które wykonać odzyskiwanie pamięci na serwerze.  
  
 ![Wątki kolekcji pamięci serwera](../../../docs/standard/garbage-collection/media/gc-server.png "GC_Server")  
Odzyskiwanie pamięci na serwerze  
  
### <a name="configuring-garbage-collection"></a>Konfigurowanie wyrzucanie elementów bezużytecznych  
 Można użyć [ \<gcserver — > element](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) schematu konfiguracji środowiska wykonawczego, aby określić typ operacji wyrzucania elementów bezużytecznych ma CLR do wykonania. Gdy ten element `enabled` atrybut ma ustawioną `false` (ustawienie domyślne), CLR wykonuje stacji roboczej wyrzucanie elementów bezużytecznych. Podczas ustawiania `enabled` atrybutu `true`, CLR wykonuje odzyskiwanie pamięci na serwerze.  
  
 Współbieżne odzyskiwanie pamięci jest określany za pomocą [ \<gcconcurrent — > element](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) środowiska uruchomieniowego schematu konfiguracji. Ustawieniem domyślnym jest `enabled`. To ustawienie określa zarówno równoczesnych i wyrzucanie elementów bezużytecznych w tle.  
  
 Można również określić odzyskiwanie pamięci na serwerze z niezarządzane interfejsy hostingu. Należy pamiętać, że program ASP.NET i SQL Server włączenie odzyskiwanie pamięci na serwerze automatycznie aplikacji znajduje się wewnątrz jednej z tych środowisk.  
  
### <a name="comparing-workstation-and-server-garbage-collection"></a>Porównanie stacji roboczej i serwerze wyrzucanie elementów bezużytecznych  
 Poniżej przedstawiono zagadnienia wątkowość i wydajności dla kolekcji elementy bezużyteczne stacji roboczej:  
  
-   Kolekcja występuje w wątku użytkownika, która wyzwoliła wyrzucanie elementów bezużytecznych i pozostaje w tym samym priorytecie. Ponieważ wątki użytkownika są zazwyczaj uruchamiane przy normalnym priorytecie, moduł garbage collector (który jest uruchamiany w wątku normalnym priorytecie) musi konkurować z innych wątków czas procesora CPU.  
  
     Wątki uruchomione natywnego kodu nie są wstrzymane.  
  
-   Odzyskiwanie pamięci na stacji roboczej jest zawsze używana na komputerze, który zawiera tylko jeden procesor, niezależnie od tego [ \<gcserver — >](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) ustawienie. Jeśli określisz odzyskiwanie pamięci na serwerze, CLR używa stacji roboczej wyrzucanie elementów bezużytecznych z współbieżności wyłączone.  
  
 Poniżej przedstawiono zagadnienia dotyczące serwera wyrzucanie elementów bezużytecznych wątków i wydajności:  
  
-   Kolekcja występuje w wielu wątkach dedykowanych, które działają w `THREAD_PRIORITY_HIGHEST` poziom priorytetu.  
  
-   Stos i dedykowanym wątku do wykonania wyrzucanie elementów bezużytecznych są udostępniane dla każdego Procesora, a stosach są zbierane w tym samym czasie. Każdy sterty zawiera sterty małego obiektu i sterty dużego obiektu i wszystkich stertach jest dostępny przez kod użytkownika. Obiektów na różnych stosów można odwoływać się do siebie.  
  
-   Ponieważ wiele wątków kolekcji garbage współpracują ze sobą, odzyskiwanie pamięci na serwerze jest szybsza niż stacji roboczej wyrzucanie elementów bezużytecznych na stercie sam rozmiar.  
  
-   Odzyskiwanie pamięci na serwerze często ma większy rozmiar segmentów. Należy jednak pamiętać, że jest to tylko generalizacji: rozmiar segmentu jest konkretnej implementacji i może ulec zmianie. Należy wykonać żadnych założeń o rozmiarze segmentów przydzielane przez moduł garbage collector podczas Dostrajanie aplikacji.  
  
-   Odzyskiwanie pamięci na serwerze może być pracochłonne. Na przykład jeśli masz 12 procesów uruchomionych na komputerze, na którym zainstalowano 4 procesory, będzie 48 wątków kolekcji dedykowanej pamięci wszystkich na odzyskiwanie pamięci na serwerze. W przypadku obciążenia pamięci wysokiej Jeśli wszystkie procesy Rozpocznij wyrzucanie elementów bezużytecznych moduł garbage collector będzie mieć 48 wątków do zaplanowania.  
  
 Jeśli używasz setki wystąpienia aplikacji, należy rozważyć użycie pamięci na stacji roboczej z współbieżne odzyskiwanie pamięci wyłączone. To spowoduje mniej przełączania kontekstu, które może poprawić wydajność.  
  
 [Powrót do początku](#top)  
  
<a name="concurrent_garbage_collection"></a>   
## <a name="concurrent-garbage-collection"></a>Współbieżne odzyskiwanie pamięci  
 W kolekcji elementy bezużyteczne stacji roboczej lub serwera można włączyć współbieżne odzyskiwanie pamięci, dzięki czemu wątków, aby uruchomić równocześnie z dedykowanym wątku, który wykonuje większość czasu trwania kolekcji wyrzucanie elementów bezużytecznych. Ta opcja dotyczy tylko wyrzucania w generacji 2; generacji 0 i 1 są zawsze niewspółbieżnego, ponieważ kończyły się bardzo szybko.  
  
 Współbieżne odzyskiwanie pamięci pozwala aplikacji na bardziej elastyczny, minimalizując pauzy dla kolekcji. Wątki zarządzane mogą nadal uruchomić w większości przypadków, gdy wątek kolekcji współbieżne odzyskiwanie jest uruchomiony. W efekcie krótszą wstrzymuje działanie podczas występuje wyrzucania elementów bezużytecznych.  
  
 Aby zwiększyć wydajność, gdy działa wiele procesów, wyłącz współbieżne odzyskiwanie pamięci. Można to zrobić przez dodanie [ \<gcconcurrent — > element](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) do pliku konfiguracji aplikacji i ustawienia wartości jego `enabled` atrybutu `"false"`.  
  
 Współbieżne odzyskiwanie pamięci jest wykonywana na dedykowanym wątku. Domyślnie środowisko CLR uruchamia stacji roboczej wyrzucanie elementów bezużytecznych z współbieżne odzyskiwanie pamięci włączone. Dotyczy to komputerów z jednym procesorem i wielu procesorów.  
  
 Możliwość przydzielić małych obiektów na stercie podczas współbieżne odzyskiwanie pamięci jest ograniczona przez obiekty pozostanie w segmencie tymczasowych podczas uruchamiania współbieżne odzyskiwanie pamięci. Jak uzyskać dostęp do końca segmentu, konieczne będzie czekać współbieżne odzyskiwanie pamięci zakończyć, gdy są wstrzymane zarządzanych wątków, które należy alokacji małego obiektu.  
  
 Współbieżne odzyskiwanie pamięci ma nieco większy zestaw roboczy (w porównaniu z niewspółbieżnego pamięci), ponieważ obiekty można przydzielić podczas kolekcji współbieżnych. Jednak może to wpłynąć na wydajność, ponieważ obiekty, które zostało przydzielone staną się częścią zestawu roboczego. Zasadniczo współbieżne odzyskiwanie pamięci zamienia niektórych Procesora i pamięci na krótszą pauzy.  
  
 Na poniższej ilustracji przedstawiono współbieżne odzyskiwanie pamięci w oddzielnym wątku dedykowanych.  
  
 ![Współbieżne odzyskiwanie kolekcji wątków](../../../docs/standard/garbage-collection/media/gc-concurrent.png "GC_Concurrent")  
Współbieżne odzyskiwanie pamięci  
  
 [Powrót do początku](#top)  
  
<a name="background_garbage_collection"></a>   
## <a name="background-workstation-garbage-collection"></a>Odzyskiwanie pamięci w tle stacji roboczej  
 W tle wyrzucanie elementów bezużytecznych tymczasowych generacje (0 i 1) są zbierane zgodnie z potrzebami, gdy Trwa zbieranie generacji 2. Brak Brak ustawienia dla tła wyrzucanie elementów bezużytecznych; jest włączany automatycznie za współbieżne odzyskiwanie pamięci. Odzyskiwanie pamięci w tle nie zastępuje współbieżne odzyskiwanie pamięci. Jako współbieżne odzyskiwanie pamięci, odzyskiwanie pamięci w tle jest wykonywana na dedykowanym wątku i ma zastosowanie tylko do kolekcji generacji 2.  
  
> [!NOTE]
>  Odzyskiwanie pamięci w tle jest dostępna tylko w [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] i nowszych wersjach. W [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], jest obsługiwana tylko w przypadku stacji roboczej wyrzucanie elementów bezużytecznych. Odzyskiwanie pamięci w tle w programie .NET Framework 4.5, jest dostępna dla zarówno stacji roboczej i serwerze wyrzucanie elementów bezużytecznych.  
  
 Zbiór na tymczasowych generacje podczas odzyskiwanie pamięci w tle jest określany jako pierwszego wyrzucania elementów bezużytecznych. Gdy występują wyrzucania pierwszego planu, wszystkie wątki zarządzane są wstrzymane.  
  
 Gdy trwa odzyskiwanie pamięci w tle i przydzielono za mało obiektów podczas generowania 0, CLR wykonuje generacji 0 lub generacji 1 pierwszego wyrzucania elementów bezużytecznych. Wątek kolekcji pamięci w tle dedykowanych sprawdza na częste punkty bezpieczeństwa, aby ustalić, czy istnieje żądanie dla pierwszego wyrzucania elementów bezużytecznych. Jeśli istnieje, pamięci w tle zawiesza się tak, aby może wystąpić pierwszego wyrzucania elementów bezużytecznych. Po ukończeniu pierwszego planu wyrzucanie elementów bezużytecznych wznowić wątku kolekcji garbage dedykowanych tła i wątki użytkownika.  
  
 Odzyskiwanie pamięci w tle usuwa alokacji ograniczeń narzuconych przez współbieżne odzyskiwanie pamięci, ponieważ tymczasowych wyrzucania mogą wystąpić podczas odzyskiwanie pamięci w tle. Oznacza to, czy odzyskiwanie pamięci w tle można usunąć obiektów martwy w generacje tymczasowych i można również rozwinąć na stercie, w razie potrzeby podczas generowania 1 wyrzucania elementów bezużytecznych.  
  
 Na poniższej ilustracji przedstawiono w oddzielnym wątku dedykowanych na stacji roboczej odzyskiwanie pamięci w tle.  
  
 ![Stacja robocza wyrzucanie elementów bezużytecznych w tle](../../../docs/standard/garbage-collection/media/backgroundworkstn.png "BackgroundWorkstn")  
Odzyskiwanie pamięci w tle stacji roboczej  
  
 [Powrót do początku](#top)  
  
<a name="background_server_garbage_collection"></a>   
## <a name="background-server-garbage-collection"></a>Odzyskiwanie pamięci w tle serwera  
 Począwszy od programu .NET Framework 4.5, odzyskiwanie pamięci w tle serwera jest to domyślny tryb dla odzyskiwanie pamięci na serwerze. Aby wybrać ten tryb, ustaw `enabled` atrybutu [ \<gcserver — > element](../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md) do `true` w schemacie konfiguracji środowiska wykonawczego. Ta działa tryb podobnie do stacji roboczej odzyskiwanie pamięci w tle, opisane w poprzedniej sekcji, ale ma kilka różnic. Odzyskiwanie pamięci w tle stacji roboczej używa jednego dedykowanej pamięci kolekcji wątku w tle, odzyskiwanie pamięci w tle serwera używa wielu wątków zwykle dedykowanych wątków dla każdego procesora logicznego. W przeciwieństwie do stacji roboczej odzyskiwanie kolekcji wątek w tle wątki te nie podlega limitowi czasu.  
  
 Na poniższej ilustracji przedstawiono tła wyrzucanie elementów bezużytecznych w oddzielnym wątku dedykowanych na serwerze.  
  
 ![Odzyskiwanie pamięci na serwerze w tle](../../../docs/standard/garbage-collection/media/backgroundserver.png "BackgroundServer")  
Odzyskiwanie pamięci w tle serwera  
  
## <a name="see-also"></a>Zobacz też  
 [Odzyskiwanie pamięci](../../../docs/standard/garbage-collection/index.md)
