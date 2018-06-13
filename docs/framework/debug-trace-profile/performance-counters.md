---
title: Liczniki wydajności w oprogramowaniu .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- performance, .NET Framework applications
- performance counters
- performance monitoring, counters
ms.assetid: 06a4ae8c-eeb2-4d5a-817e-b1b95c0653e1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb46b6466ee0ee3d4cdc4b7c934e518fd9f7f082
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394423"
---
# <a name="performance-counters-in-the-net-framework"></a>Liczniki wydajności w oprogramowaniu .NET Framework
Ten temat zawiera listę liczników wydajności można znaleźć w [monitora wydajności](http://technet.microsoft.com/library/cc749249.aspx).  
  
-   [Liczniki wydajności wyjątku](#exception)  
  
-   [Liczniki wydajności międzyoperacyjności](#interop)  
  
-   [Liczniki wydajności JIT](#jit)  
  
-   [Podczas ładowania liczników wydajności](#loading)  
  
-   [Liczniki wydajności blokady i wątku](#lockthread)  
  
-   [Liczniki wydajności pamięci](#memory)  
  
-   [Liczniki wydajności sieci](#networking)  
  
-   [Liczniki wydajności zabezpieczeń](#security)  
  
<a name="exception"></a>   
## <a name="exception-performance-counters"></a>Liczniki wydajności wyjątku  
 Kategoria .NET CLR wyjątki konsoli wydajności zawiera liczniki, które zawierają informacje o wyjątki wyrzucane przez aplikację. W poniższej tabeli opisano liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Liczba wyjątków zgłoszonych**|Wyświetla całkowitą liczbę wyjątków zgłaszanych od czasu uruchomienia aplikacji. Obejmuje to zarówno wyjątki .NET i niezarządzanymi wyjątkami przekonwertowanymi na wyjątki .NET. Na przykład HRESULT zwrócony z kodem niezarządzanym jest konwertowana na wyjątek w kodzie zarządzanym.<br /><br /> Ten licznik obejmuje zarówno obsłużonych i nieobsłużonych wyjątków. Wyjątki, które są zgłoszony są zliczane ponownie.|  
|**Liczba wyjątków / s**|Wyświetla liczbę wyjątków zgłaszanych na sekundę. Obejmuje to zarówno wyjątki .NET i niezarządzanymi wyjątkami przekonwertowanymi na wyjątki .NET. Na przykład HRESULT zwrócony z kodem niezarządzanym jest konwertowana na wyjątek w kodzie zarządzanym.<br /><br /> Ten licznik obejmuje zarówno obsłużonych i nieobsłużonych wyjątków. Nie jest to wartość średnia wraz z upływem czasu; jego wartość to różnica między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania. Ten licznik jest wskaźnik potencjalnych problemów z wydajnością, jeśli jest to duży (> 100s) liczbę wyjątki są zgłaszane.|  
|**liczba filtrów / s**|Wskazuje liczbę wykonywanych w ciągu sekundy filtrów wyjątków .NET. Filtr wyjątków określa niezależnie od tego, czy wyjątek jest obsługiwany.<br /><br /> Ten licznik nie jest to wartość średnia wraz z upływem czasu; jego wartość to różnica między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Liczba Finallys / s**|Wyświetla liczbę bloki finally wykonywanych na sekundę. A na koniec bloku gwarancji wykonywane niezależnie od tego, jak został zakończony bloku try.  Tylko finally są zliczane bloki wykonywane dla wyjątku; na koniec bloków w ścieżkach normalne kodu nie są uwzględniane przez ten licznik.<br /><br /> Ten licznik nie jest to wartość średnia wraz z upływem czasu; jego wartość to różnica między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Zgłoszenia do obsługi głębokości / s**|Wyświetla liczbę ramek stosu, przechodzić z ramki, która zgłosiła wyjątek do ramki obsługi wyjątków, na sekundę. Ten licznik resetuje od zera po wprowadzeniu obsługi wyjątków, wyjątki zagnieżdżonych Pokaż Głębokość stosu obsługi do obsługi.<br /><br /> Ten licznik nie jest to wartość średnia wraz z upływem czasu; jego wartość to różnica między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
  
<a name="interop"></a>   
## <a name="interop-performance-counters"></a>Liczniki wydajności międzyoperacyjności  
 Kategoria .NET CLR Interop konsoli wydajności zawiera liczniki, które zawierają informacje o aplikacji interakcji z składniki modelu COM, usług COM + i bibliotek typów zewnętrznych. W poniższej tabeli opisano liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**# CCW**|Wyświetla bieżący numer wywoływane otoki COM (CCW). CCW to serwer proxy dla obiektu zarządzanego przywoływane z niezarządzanego klienta COM. Ten licznik wskazuje liczbę zarządzanych obiektów odwołuje się niezarządzany kod modelu COM.|  
|**# marshalingu**|Wyświetla całkowitą liczbę razy argumentów i zwracanych wartości mają zwracanych z kodu zarządzanego do kodu niezarządzanego i na odwrót, od czasu uruchomienia aplikacji. Ten licznik nie jest zwiększany, jeśli wykonywane wycinki kodu są wbudowane. (Wycinków kodu są odpowiedzialne za organizowanie argumentów i wartości zwracane). Wykonywane wycinki kodu są zazwyczaj wbudowane, jeśli przekazywanie obciążenie jest mała.|  
|**Liczba klas zastępczych**|Wyświetla bieżącą liczbę wycinków kodu utworzonych przez środowisko uruchomieniowe języka wspólnego. Wykonywane wycinki kodu są odpowiedzialne za organizowanie argumentów oraz wartości zwracanych z kodu zarządzanego do niezarządzanego i odwrotnie, podczas wywołania międzyoperacyjnego modelu COM lub platformę wywołania wywołania.|  
|**Liczba eksportów TLB / s**|Zarezerwowane do użytku w przyszłości.|  
|**# importów TLB / s**|Zarezerwowane do użytku w przyszłości.|  
  
<a name="jit"></a>   
## <a name="jit-performance-counters"></a>liczniki wydajności JIT  
 Kategoria .NET CLR JIT konsoli wydajności zawiera liczniki, które zawierają informacje dotyczące kodu, która została skompilowana JIT. W poniższej tabeli opisano liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Liczba skompilowanych bajtów IL w trybie JIT**|Wyświetla całkowitą liczbę bajtów język pośredni (MSIL) firmy Microsoft skompilowanych za pomocą kompilatora just-in-time (JIT) od czasu uruchomienia aplikacji. Ten licznik jest odpowiednikiem **całkowita liczba skompilowanych bajtów IL w trybie JIT** licznika.|  
|**Liczba metod skompilowanych w trybie JIT**|Wyświetla całkowitą liczbę metod kompilacji JIT od aplikacji uruchomiona. Ten licznik nie uwzględnia metod skompilowanych pre-JIT.|  
|**% Czasu w trybie Jit**|Przedstawia wartość procentową czasu wykonywania kompilacji JIT liczony od czasu ostatniego fazy kompilacji JIT. Ten licznik jest aktualizowany po zakończeniu każdej fazy kompilacji JIT. Faza kompilacji JIT występuje, gdy metoda i jego zależności są kompilowane.|  
|**Plik języka Pośredniczącego bajtów skompilowanych w trybie JIT / s**|Wskazuje liczbę bajtów MSIL, które są kompilowane JIT na sekundę. Ten licznik nie jest to wartość średnia wraz z upływem czasu; jego wartość to różnica między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Awarie standardowego Jit**|Wyświetla całkowitą liczbę metod, które kompilator JIT nie może skompilować od czasu uruchomienia aplikacji. Ten błąd może wystąpić, jeśli nie można zweryfikować MSIL lub jest błąd wewnętrzny kompilatora JIT.|  
|**Łączna liczba skompilowanych bajtów IL w trybie JIT**|Wyświetla całkowitą liczbę bajtów MSIL kompilacji JIT od aplikacji uruchomiona. Ten licznik jest odpowiednikiem **# IL bajtów skompilowanych w trybie JIT** licznika.|  
  
<a name="loading"></a>   
## <a name="loading-performance-counters"></a>Podczas ładowania liczników wydajności  
 Kategoria .NET CLR ładowania konsoli wydajności zawiera liczniki, które zawierają informacje dotyczące zestawy, klasy i domen aplikacji, które zostały załadowane. W poniższej tabeli opisano liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**% Czasu ładowania**|Zarezerwowane do użytku w przyszłości.|  
|**Długość wyszukiwania zestawu**|Zarezerwowane do użytku w przyszłości.|  
|**Bajtów w stercie modułu ładującego**|Wyświetla bieżący rozmiar w bajtach pamięci zarezerwowanej przez moduł ładujący klasy we wszystkich domenach aplikacji. Pamięć zadeklarowana to fizyczne miejsce zarezerwowane w pliku stronicowania na dysku.|  
|**Bieżący domen aplikacji**|Wyświetla bieżącą liczbę domen aplikacji załadowanych w tej aplikacji.|  
|**Bieżący zestawów**|Wyświetla bieżącą liczbę zestawów załadowanych we wszystkich domenach aplikacji w aktualnie uruchomionej aplikacji. Jeśli zestaw jest ładowany jako neutralne dla domen z wielu domen aplikacji, ten licznik jest zwiększany tylko raz.|  
|**Bieżący klas załadowanych**|Wyświetla bieżącą liczbę klas załadowanych do wszystkich zestawów.|  
|**Liczba domen aplikacji**|Wskazuje liczbę ładowanych w ciągu sekundy domen aplikacji. Ten licznik nie jest to wartość średnia wraz z upływem czasu; jego wartość to różnica między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Szybkość zwalniania domen aplikacji**|Wyświetla liczbę domen aplikacji zwalnianych w ciągu sekundy. Ten licznik nie jest to wartość średnia wraz z upływem czasu; jego wartość to różnica między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Liczba zestawów**|Wyświetla liczbę zestawów załadowanych na drugi we wszystkich domenach aplikacji. Jeśli zestaw jest ładowany jako neutralne dla domen z wielu domen aplikacji, ten licznik jest zwiększany tylko raz.<br /><br /> Ten licznik nie jest to wartość średnia wraz z upływem czasu; jego wartość to różnica między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Szybkość ładowania klas**|Wskazuje liczbę klas ładowanych w ciągu sekundy w wszystkie zestawy. Ten licznik nie jest to wartość średnia wraz z upływem czasu; jego wartość to różnica między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Współczynnik błędów obciążenia**|Wskazuje liczbę klas, których nie można załadować na sekundę. Ten licznik nie jest to wartość średnia wraz z upływem czasu; jego wartość to różnica między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.<br /><br /> Błędy ładowania może spowodowane wieloma przyczynami, np. nieodpowiednie ustawienia zabezpieczeń lub nieprawidłowy format. Aby uzyskać więcej informacji zobacz Pomoc usług profilowania.|  
|**Łączna liczba błędów w czasie ładowania**|Wyświetla całkowitą liczbę klas, które nie zostały załadowane od czasu uruchomienia aplikacji.<br /><br /> Błędy ładowania może spowodowane wieloma przyczynami, np. nieodpowiednie ustawienia zabezpieczeń lub nieprawidłowy format. Aby uzyskać więcej informacji zobacz Pomoc usług profilowania.|  
|**Całkowita liczba domen aplikacji**|Wyświetla całkowitą liczbę domen aplikacji załadowanych od chwili uruchomienia aplikacji.|  
|**Całkowita liczba zwalnianych domen aplikacji**|Wyświetla łączną liczbę domen aplikacji zwolnionych od czasu uruchomienia aplikacji. Jeśli domeny aplikacji jest załadowany i zwolniony wiele razy, ten licznik zwiększany po każdej zmianie domeny aplikacji to zwolniony.|  
|**Całkowita liczba zestawów**|Wyświetla całkowitą liczbę zestawów załadowanych od czasu uruchomienia aplikacji. Jeśli zestaw jest ładowany jako neutralne dla domen z wielu domen aplikacji, ten licznik jest zwiększany tylko raz.|  
|**Całkowita liczba klas załadowanych**|Wyświetla skumulowaną liczbę klas załadowanych do wszystkich zestawów od czasu uruchomienia aplikacji.|  
  
<a name="lockthread"></a>   
## <a name="lock-and-thread-performance-counters"></a>Liczniki wydajności blokady i wątku  
 Kategoria .NET CLR LocksAndThreads konsoli wydajności zawiera liczniki, które zawierają informacje o zarządzanych blokad i wątków używanych przez aplikację. W poniższej tabeli opisano liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**# Aktualna liczba wątków logicznych**|Wyświetla liczbę bieżącego wątku zarządzanych obiektów w aplikacji. Ten licznik licznik jednocześnie działające i zatrzymanie wątków. Ten licznik nie jest to wartość średnia wraz z upływem czasu; Wyświetla ostatnią odczytaną wartość.|  
|**Aktualna liczba fizycznych wątków**|Wyświetla liczbę wątków natywnego systemu operacyjnego utworzonych i zarządzanych przez środowisko uruchomieniowe języka wspólnego do działania jako wątki podstawowe dla obiektów wątków zarządzanych. Wartość tego licznika nie obejmuje wątki używane przez środowisko wykonawcze w czasie wykonywania operacji wewnętrznych; jest to podzbiór wątków w procesie systemu operacyjnego.|  
|**# Aktualna liczba rozpoznanych wątków**|Wyświetla liczbę wątków, które obecnie są rozpoznawane w czasie wykonywania. Wątki te są skojarzone z odpowiedniego obiektu zarządzanego wątku. Środowisko uruchomieniowe nie tworzy tych wątków, ale uruchamianych wewnątrz środowiska uruchomieniowego co najmniej raz.<br /><br /> Śledzone są tylko wątki unikatowe; wątki mających taki sam identyfikator wątku ponownie środowisko uruchomieniowe lub zostaną utworzone ponownie po zamknięciu wątku nie są zliczane podwójnie.|  
|**Liczba całkowita liczba rozpoznanych wątków**|Wyświetla całkowitą liczbę wątków, które zostały rozpoznane przez środowisko uruchomieniowe od czasu uruchomienia aplikacji. Wątki te są skojarzone z odpowiedniego obiektu zarządzanego wątku. Środowisko uruchomieniowe nie tworzy tych wątków, ale uruchamianych wewnątrz środowiska uruchomieniowego co najmniej raz.<br /><br /> Śledzone są tylko wątki unikatowe; wątki mających taki sam identyfikator wątku ponownie środowisko uruchomieniowe lub zostaną utworzone ponownie po zamknięciu wątku nie są zliczane podwójnie.|  
|**Współczynnik rywalizacji / s**|Wyświetla szybkość jaką wątków w czasie wykonywania prób uzyskania niepomyślnie zarządzanej blokady.|  
|**Bieżąca długość kolejki**|Wyświetla całkowitą liczbę wątków, które obecnie oczekują na uzyskanie zarządzanej blokady w aplikacji. Ten licznik nie jest to wartość średnia wraz z upływem czasu; Wyświetla ostatnią odczytaną wartość.|  
|**Długość kolejki / s**|Wyświetla liczbę wątków na sekundę, które czekają na uzyskanie blokady w aplikacji. Ten licznik nie jest to wartość średnia wraz z upływem czasu; jego wartość to różnica między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Szczytowa długość kolejki**|Wyświetla całkowitą liczbę wątków oczekujących jednocześnie na uzyskanie zarządzanej blokady od czasu uruchomienia aplikacji.|  
|**Liczba rozpoznanych wątków / s**|Wyświetla liczbę wątków na sekundę, które zostały rozpoznane przez środowisko uruchomieniowe. Wątki te są skojarzone z odpowiedniego obiektu zarządzanego wątku. Środowisko uruchomieniowe nie tworzy tych wątków, ale uruchamianych wewnątrz środowiska uruchomieniowego co najmniej raz.<br /><br /> Śledzone są tylko wątki unikatowe; wątki mających taki sam identyfikator wątku ponownie środowisko uruchomieniowe lub zostaną utworzone ponownie po zamknięciu wątku nie są zliczane podwójnie.<br /><br /> Ten licznik nie jest to wartość średnia wraz z upływem czasu; jego wartość to różnica między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Łączna liczba rywalizacji**|Wyświetla całkowitą liczbę razy wątków w środowisku uruchomieniowym podjęto próbę uzyskania blokady zarządzane bez powodzenia.|  
  
<a name="memory"></a>   
## <a name="memory-performance-counters"></a>Liczniki wydajności pamięci  
 Kategorii wydajności pamięci platformy .NET CLR konsoli zawiera liczniki, które zawierają informacje o moduł garbage collector. W poniższej tabeli opisano liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Liczba bajtów we wszystkich Stertach**|Wyświetla sumę **Rozmiar sterty pokolenia 1**, **Rozmiar sterty pokolenia 2**, i **duży rozmiar sterty obiektu** liczników. Ten licznik wskazuje bieżącą ilość pamięci przydzielona w bajtach na wyrzucanie elementów bezużytecznych stosów.|  
|**# Uchwyty GC**|Wyświetla bieżąca liczba dojść do kolekcji pamięci w użyciu. Wyrzucanie elementów kolekcji uchwyty są dojść do zasobów zewnętrznych do środowiska CLR i środowiska zarządzanego.|  
|**# Kolekcje pokolenia 0**|Wyświetla liczbę wystąpień obiektów pokolenia 0 (to znaczy najmłodsze, ostatnio przydzielone obiekty) są bezużytecznych od czasu uruchomienia aplikacji.<br /><br /> Bezużytecznych generacji 0 występuje, gdy dostępna pamięć generacji 0 nie wystarcza do spełnienia żądań alokacji. Ten licznik jest zwiększany po zakończeniu generowania 0 wyrzucania elementów bezużytecznych. Okno wyrzucania wyższej generacji uwzględniają wszystkie niższych generacji. Ten licznik jest jawnie zwiększany, gdy występuje wyrzucania wyższej generacji (generacja 1 lub 2).<br /><br /> Ten licznik wskazuje ostatnią odczytaną wartość. **_Global\_**  wartość licznika jest niedokładna i należy ją ignorować.|  
|**# Kolekcje gen 1**|Wyświetla liczbę wystąpień obiektów generacji 1 są bezużytecznych od czasu uruchomienia aplikacji.<br /><br /> Licznik jest zwiększany po zakończeniu generacji 1 wyrzucania elementów bezużytecznych. Okno wyrzucania wyższej generacji uwzględniają wszystkie niższych generacji. Ten licznik jest jawnie zwiększany, gdy występuje wyrzucania wyższej generacji (generacja 2).<br /><br /> Ten licznik wskazuje ostatnią odczytaną wartość. **_Global\_**  wartość licznika jest niedokładna i należy ją ignorować.|  
|**# Kolekcje gen 2**|Wyświetla liczbę wystąpień obiektów generacji 2 są bezużytecznych od czasu uruchomienia aplikacji. Licznik jest zwiększany po zakończeniu generacji 2 wyrzucania elementów bezużytecznych (nazywanej także pełną wyrzucania elementów bezużytecznych).<br /><br /> Ten licznik wskazuje ostatnią odczytaną wartość. **_Global\_**  wartość licznika jest niedokładna i należy ją ignorować.|  
|**# Wywołanych GC**|Wyświetla całkowitą liczbę razy wyrzucanie elementów bezużytecznych wykonanych w wyniku jawnego wywołania <xref:System.GC.Collect%2A?displayProperty=nameWithType>. Jest dobrym rozwiązaniem, aby umożliwić moduł garbage collector częstotliwość jego kolekcji.|  
|**# unieruchomionych obiektów**|Wskazuje liczbę unieruchomionych obiektów napotkanych w ostatnim wyrzucanie elementów bezużytecznych. Unieruchomiony obiekt to obiekt, który moduł garbage collector nie można przenieść w pamięci. Ten licznik śledzi unieruchomionych obiektów znajdujących się tylko w stosach, które są bezużytecznych. Na przykład wyrzucania elementów bezużytecznych generacji 0 spowoduje wyliczenie unieruchomionych obiektów znajdujących się tylko w stosie pokolenia 0.|  
|**Liczba bloków synchronizacji w użyciu**|Wyświetla bieżącą liczbę bloków synchronizacji w użyciu. Bloki synchronizacji to dla obiektów struktury danych przydzielone do przechowywania informacji o synchronizacji. Posiadają odwołania słabe do zarządzanych obiektów i muszą być skanowane przez moduł garbage collector. Bloki synchronizacji nie są ograniczone do przechowywania informacji o synchronizacji; można również przechowywać COM interop metadanych. Ten licznik wskazuje problemy z wydajnością z intensywnym użyciem pierwotnych synchronizacji.|  
|**# Całkowita liczba Zadeklarowane bajty**|Wyświetlana jest ilość pamięci wirtualnej w bajtach zarezerwowanej aktualnie przez moduł garbage collector. Pamięć zadeklarowana to pamięć fizyczna, dla której zarezerwowano miejsce w pliku stronicowania na dysku.|  
|**# Całkowita liczba zastrzeżone bajtów**|Wyświetlana jest ilość pamięci wirtualnej w bajtach zastrzeżonej przez moduł garbage collector. Pamięć zastrzeżona to obszar pamięci wirtualnej zarezerwowana dla aplikacji, w przypadku nie dysku lub stron pamięci głównej.|  
|**% Czasu odzyskiwania pamięci**|Wyświetla procent minionego czasu, jaki był poświęcony na operację wyrzucania od ostatniego cyklu wyrzucania elementów w kolekcji. Ten licznik wskazuje zwykle pracy wykonanej przez moduł garbage collector zbieranie i compact pamięci w imieniu aplikacji. Ten licznik jest aktualizowany tylko po zakończeniu każdej operacji wyrzucania elementów bezużytecznych. Ten licznik nie jest to wartość średnia; jego wartość reprezentuje ostatnią odczytaną wartość.|  
|**Przydzielonych bajtów na sekundę**|Wskazuje liczbę bajtów przydzielanych na stercie kolekcji pamięci na sekundę. Ten licznik jest aktualizowany po zakończeniu każdej operacji wyrzucania elementów bezużytecznych w każdej alokacji. Ten licznik nie jest to wartość średnia wraz z upływem czasu; jego wartość to różnica między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Przy życiu finalizacji**|Wyświetla liczbę zbieranych pamięci obiektów, które pozostają aktualne po kolekcji, ponieważ się sfinalizowana. Jeśli tych obiektów zawiera odwołania do innych obiektów, tych obiektów także przetrwać, ale nie są uwzględniane przez ten licznik. **Awansowane finalizacji pamięci z pokolenia 0** reprezentuje pamięć, który udało się z powodu finalizacji przetrwać.<br /><br /> Ten licznik nie jest zbiorcza; na końcu każdej operacji wyrzucania elementów bezużytecznych liczba przy życiu jest aktualizowany podczas tylko tej określonej kolekcji. Ten licznik wskazuje dodatkowego obciążenia, która aplikacja może pociągnąć za sobą z powodu finalizacji.|  
|**Rozmiar sterty pokolenia 0**|Wyświetla maksymalną liczbę bajtów, które mogą być przydzielone podczas generowania 0; Bieżąca liczba bajtów przydzielonych w generacji 0 nie oznacza.<br /><br /> Wyrzucanie elementów bezużytecznych generacji 0 występuje, gdy alokacje od ostatniego zebrania o większym rozmiarze. Rozmiar generacji 0 jest dostosowana przez moduł garbage collector i zmieniać podczas wykonywania aplikacji. Na końcu kolekcji generacji 0 rozmiaru pokolenia 0 sterta to 0 bajtów. Ten licznik wskazuje rozmiar w bajtach alokacji, który wywołuje dalej bezużytecznych generacji 0.<br /><br /> Ten licznik jest aktualizowany po zakończeniu operacji wyrzucania elementów bezużytecznych w każdej alokacji.|  
|**Awansowane z pokolenia 0 bajtów na sekundę**|Wskazuje liczbę bajtów na sekundę, które zostały awansowane z pokolenia 0 na pokolenie 1. Pamięć jest podnoszony, gdy jej przeżyje wyrzucania elementów bezużytecznych. Ten licznik jest wskaźnikiem stosunkowo długotrwałe obiektów tworzonych w ciągu sekundy.<br /><br /> Ten licznik wyświetla różnicę między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Rozmiar sterty pokolenia 1**|Wskazuje bieżącą liczbę bajtów pokolenia 1; Ten licznik wyświetla maksymalny rozmiar generacji 1. Obiekty nie są bezpośrednio przydzielony w tym pokoleniu; są awansowane w wyniku poprzedniej generacji 0 wyrzucanie elementów bezużytecznych. Ten licznik jest aktualizowany po zakończeniu operacji wyrzucania elementów bezużytecznych w każdej alokacji.|  
|**Awansowane z pokolenia 1 bajtów na sekundę**|Wskazuje liczbę bajtów na sekundę, które zostały awansowane z pokolenia 1 na pokolenie 2. Ten licznik nie uwzględnia obiektów, które zostały awansowane wyłącznie z powodu się sfinalizowana.<br /><br /> Pamięć jest podnoszony, gdy jej przeżyje wyrzucania elementów bezużytecznych. Nic nie jest awansowana z generacji 2, ponieważ to najstarsze generacji. Ten licznik jest wskaźnikiem bardzo długotrwałe obiektów tworzonych w ciągu sekundy.<br /><br /> Ten licznik wyświetla różnicę między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Rozmiar sterty pokolenia 2**|Wskazuje bieżącą liczbę bajtów pokolenia 2. Obiekty nie są bezpośrednio przydzielony w tym pokoleniu; są awansowane z pokolenia 1 podczas poprzedniej generacji 1 wyrzucanie elementów bezużytecznych. Ten licznik jest aktualizowany po zakończeniu operacji wyrzucania elementów bezużytecznych w każdej alokacji.|  
|**Rozmiar sterty obiektów wielkich**|Wyświetla bieżący rozmiar w bajtach sterty dużych obiektów. Obiekty, które są większe niż około 85,000 bajtów są traktowane jako duże obiekty przez moduł garbage collector i przydzielania bezpośrednio w stercie specjalne; nie są awansowane za pośrednictwem generacji. Ten licznik jest aktualizowany po zakończeniu operacji wyrzucania elementów bezużytecznych w każdej alokacji.|  
|**Identyfikator procesu**|Wyświetla identyfikator procesu wystąpienia procesu CLR, która jest monitorowana.|  
|**Pamięć przetwarzania końcowego awansowana z pokolenia 0**|Wskazuje liczbę bajtów pamięci, które zostały awansowane z pokolenia 0 na pokolenie 1 wyłącznie z powodu się sfinalizowana. Ten licznik nie jest zbiorcza; wyświetlana jest wartość odczytaną po zakończeniu ostatniej operacji wyrzucania elementów bezużytecznych.|  
|**Pamięć awansowana z pokolenia 0**|Wskazuje liczbę bajtów pamięci, które pozostają aktualne po wyrzucanie elementów bezużytecznych i awansowane z pokolenia 0 na pokolenie 1. Ten licznik nie uwzględnia obiektów, które zostały awansowane wyłącznie z powodu się sfinalizowana. Ten licznik nie jest zbiorcza; wyświetlana jest wartość odczytaną po zakończeniu ostatniej operacji wyrzucania elementów bezużytecznych.|  
|**Pamięć awansowana z pokolenia 1**|Wskazuje liczbę bajtów pamięci, które pozostają aktualne po wyrzucanie elementów bezużytecznych i awansowane z pokolenia 1 na pokolenie 2. Ten licznik nie uwzględnia obiektów, które zostały awansowane wyłącznie z powodu się sfinalizowana. Ten licznik nie jest zbiorcza; wyświetlana jest wartość odczytaną po zakończeniu ostatniej operacji wyrzucania elementów bezużytecznych. Ten licznik jest resetowany do 0, jeśli kolekcja generacji 0 tylko ostatniego wyrzucanie elementów bezużytecznych.|  
  
<a name="networking"></a>   
## <a name="networking-performance-counters"></a>Liczniki wydajności sieci  
 Kategoria .NET CLR sieci konsoli wydajności zawiera liczniki, które zawierają informacje o danych, która aplikacja wysyła i odbiera za pośrednictwem sieci. W poniższej tabeli opisano liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Odebrane bajty**|Łączna liczba całkowita liczba bajtów odebranych przez wszystkie <xref:System.Net.Sockets.Socket> obiektów w ramach <xref:System.AppDomain> od rozpoczęcia procesu. Liczba ta obejmuje dane i informacje protokołu nie jest zdefiniowana przez protokół TCP/IP.|  
|**Wysłane bajty**|Łączna liczba bajtów wysłanych przez wszystkie <xref:System.Net.Sockets.Socket> obiektów w ramach <xref:System.AppDomain> od rozpoczęcia procesu. Liczba ta obejmuje dane i informacje protokołu nie jest zdefiniowana przez protokół TCP/IP.|  
|**Połączeń**|Skumulowana łączna liczba <xref:System.Net.Sockets.Socket> obiektów dla gniazda strumieni, które kiedykolwiek zostały połączone w <xref:System.AppDomain> od rozpoczęcia procesu.|  
|**Odebrane datagramy**|Zbiorcza liczba odebrane przez wszystkie pakiety datagram <xref:System.Net.Sockets.Socket> obiektów w ramach <xref:System.AppDomain> od rozpoczęcia procesu.|  
|**Wysłane datagramy**|Zbiorcza całkowita liczba wysłanych przez wszystkich pakietów datagram <xref:System.Net.Sockets.Socket> obiektów w ramach <xref:System.AppDomain> od rozpoczęcia procesu.|  
|**HttpWebRequest średni okres istnienia**|Średni czas ukończenia dla wszystkich <xref:System.Net.HttpWebRequest> obiektów, które zostało zakończone w ostatniego interwału w ramach <xref:System.AppDomain> od rozpoczęcia procesu.|  
|**HttpWebRequest Średni czas oczekiwania**|Średni czas na kolejki dla wszystkich <xref:System.Net.HttpWebRequest> obiektów, które w ostatnim interwale w kolejce <xref:System.AppDomain> od rozpoczęcia procesu.|  
|**HttpWebRequests utworzone na sekundę**|Liczba <xref:System.Net.HttpWebRequest> obiektów tworzonych w ciągu sekundy w <xref:System.AppDomain>.|  
|**HttpWebRequests/s**|Liczba <xref:System.Net.HttpWebRequest> obiektów, które zostały dodane do kolejki na sekundę w <xref:System.AppDomain>.|  
|**HttpWebRequests zostało przerwane na sekundę**|Liczba <xref:System.Net.HttpWebRequest> obiektów, których aplikacja o nazwie <xref:System.Net.HttpWebRequest.Abort%2A> metody na sekundę w <xref:System.AppDomain>.|  
|**HttpWebRequests/s**|Liczba <xref:System.Net.HttpWebRequest> obiektów, które otrzymały kod stanu nie powiodło się z serwera na sekundę w <xref:System.AppDomain>.|  
  
 Istnieje kilka rodzajów sieci obsługiwanych liczników wydajności:  
  
-   Liczniki zdarzeń, które mierzenia liczby powtórzeń niektórych zdarzenie wystąpiło.  
  
-   Liczniki danych mierzących ilość danych wysłanego lub odebranego.  
  
-   Czas trwania liczniki, które miar jak długo różne procesy potrwać. Czasy są mierzone w obiektach każdego interwału (zazwyczaj w sekundach) po pochodzą z innych stanów.  
  
-   Liczniki dla interwału, które mierzenia liczby obiektów, które wykonują określonego przejścia na interwał (zwykle na sekundę).  
  
 Następujące sieci liczniki wydajności dla zdarzeń:  
  
-   **Połączeń**  
  
-   **Odebrane datagramy**  
  
-   **Wysłane datagramy**  
  
 Te liczniki wydajności zawierają liczby od rozpoczęcia procesu. Liczby <xref:System.Net.Sockets.Socket> połączeń ustanowionych zawiera jawne <xref:System.Net.Sockets.Socket> metoda wywołuje przez aplikację dla połączenia gniazda strumienia, który został ustanowiony również jako wewnętrzne wywołań innych klas (<xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.WebClient>, i <xref:System.Net.Sockets.TcpClient>, na przykład) do <xref:System.Net.Sockets.Socket> — klasa  
  
 Liczniki dla **Odebrane datagramy** i **wysyłane datagramy** obejmuje datagram pakiety wysyłane lub odbierane przy użyciu jawnych <xref:System.Net.Sockets.Socket> metoda wywołuje przez aplikację jako również wewnętrzny wywołań w innych klasy (<xref:System.Net.Sockets.UdpClient>, na przykład) do <xref:System.Net.Sockets.Socket>. Klasa. Liczniki **Odebrane datagramy** i **wysyłane datagramy** może również służyć do zapewnienia bardzo surowych miary liczbę bajtów były wysyłane lub odbierane przy użyciu datagramy przejmując średni rozmiar datagramu.  
  
 Liczniki wydajności sieci dla danych są następujące:  
  
-   **Odebrane bajty**  
  
-   **Wysłane bajty**  
  
 Liczniki powyżej Podaj liczbę bajtów od rozpoczęcia procesu.  
  
 Istnieją dwa liczniki czas trwania mierzących czas trwania <xref:System.Net.HttpWebRequest> obiekty do przekazywania albo ich życia cały cykl lub po prostu część z nich:  
  
-   **HttpWebRequest średni okres istnienia**  
  
-   **HttpWebRequest Średni czas oczekiwania**  
  
 Dla **średni okres istnienia HttpWebRequest** licznika, okres istnienia większość <xref:System.Net.HttpWebRequest> obiektów zawsze rozpoczyna się od czasu utworzenia obiektu do czasu odpowiedzi strumień jest zamknięty przez aplikację. Istnieją dwa, rzadko przypadkach:  
  
-   Jeśli aplikacja nigdy nie wywołuje <xref:System.Net.HttpWebRequest.GetResponse%2A> lub <xref:System.Net.HttpWebRequest.BeginGetResponse%2A> metod, a następnie okres istnienia <xref:System.Net.HttpWebRequest> obiektu jest ignorowana.  
  
-   Jeśli <xref:System.Net.HttpWebRequest> obiekt zgłasza <xref:System.Net.WebException> podczas wywoływania metody <xref:System.Net.HttpWebRequest.GetResponse%2A> lub <xref:System.Net.HttpWebRequest.EndGetResponse%2A> metod, okres istnienia kończy się po wyjątku. Z technicznego punktu widzenia podstawowego strumienia odpowiedzi jest także zamknięty w tym momencie (w strumieniu odpowiedzi zwracany do użytkownika to naprawdę strumienia pamięci zawierający kopię w strumieniu odpowiedzi).  
  
 Istnieją cztery liczniki, które śledzą niektórych <xref:System.Net.HttpWebRequest> obiekt problemów na interwał. Te liczniki wydajności pozwalają deweloperom aplikacji, Administratorzy, i pracownikami działu pomocy technicznej lepiej zrozumieć, jakie <xref:System.Net.HttpWebRequest> robią obiektów. Następujące liczniki:  
  
-   **HttpWebRequests utworzone na sekundę**  
  
-   **HttpWebRequests/s**  
  
-   **HttpWebRequests zostało przerwane na sekundę**  
  
-   **HttpWebRequests/s**  
  
 Dla **przerwania HttpWebRequests na sekundę** licznik, wewnętrzny wywołań <xref:System.Net.HttpWebRequest.Abort%2A> zliczane są także. Te wewnętrzne wywołania są zazwyczaj spowodowane aplikacji może być konieczne pomiar czasu.  
  
 **HttpWebRequests/s** licznika zawiera liczbę <xref:System.Net.HttpWebRequest> obiektów, które otrzymały stan niepowodzenia kodu z serwera na sekundę. Oznacza to, że kod stanu otrzymany z serwera Http na końcu żądania nie jest w zakresie od 200 do 299. Kody stanu, które są obsługiwane i powoduje nowe żądanie (wiele kodów stanu 401 nieautoryzowane, na przykład) będą się nie powieść lub nie na podstawie wyniku próby. Jeśli aplikacja będzie wyświetlony błąd, na podstawie przy ponownej próbie, ten licznik jest zwiększany.  
  
 Liczniki wydajności sieci są dostępne i zarządzane za pomocą <xref:System.Diagnostics.PerformanceCounter> i powiązanych klas w <xref:System.Diagnostics> przestrzeni nazw. Liczniki wydajności sieci można również wyświetlać w konsoli Monitor wydajności systemu Windows.  
  
 Liczniki wydajności sieci muszą być włączone w pliku konfiguracji do użycia. Wszystkie sieci liczniki wydajności są włączone lub wyłączone przy użyciu jednego ustawienia w pliku konfiguracji. Poszczególne sieci liczniki wydajności nie może być włączona lub wyłączona. Aby uzyskać więcej informacji, zobacz [ \<performanceCounter > elementu (ustawienia sieciowe)](../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md).  
  
 Jeśli są włączone liczniki sieci, spowoduje to utworzenie i zaktualizować zarówno domeny AppDomain, jak i liczniki wydajności globalnego. Wyłączenie aplikacji nie zapewnia żadnych sieci danych licznika wydajności.  
  
 Liczniki wydajności są podzielone na kategorie. Aplikację można wyświetlić listę wszystkich kategorii z Poniższy przykładowy kod:  
  
```  
PerformanceCounterCategory[] Array = PerformanceCounterCategory.GetCategories();  
for (int i = 0; i < Array.Length; i++)  
{  
    Console.Out.WriteLine("{0}. Name={1} Help={2}", i, Array[i].CategoryName, Array[i].CategoryHelp);  
}  
```  
  
 Sieci liczniki wydajności są wyświetlane w dwóch kategorii:  
  
-   "Środowisko .NET CLR w sieci" - oryginalnego liczniki wydajności wprowadzone w programie .NET Framework w wersji 2 i obsługiwana na .NET Framework w wersji 2 lub nowszej.  
  
-   ".NET CLR sieci 4.0.0.0" - wszystkie powyższe gniazda liczników oraz nowe liczniki wydajności, które są obsługiwane w programie .NET Framework w wersji 4 lub nowszy. Te nowe liczniki Podaj informacje o wydajności na <xref:System.Net.HttpWebRequest> obiektów.  
  
 Aby uzyskać więcej informacji na dostęp i zarządzanie liczników wydajności w aplikacji, zobacz [liczniki wydajności](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
<a name="security"></a>   
## <a name="security-performance-counters"></a>Liczniki wydajności zabezpieczeń  
 Kategorii wydajności konsoli .NET CLR zabezpieczeń zawiera liczniki, które dostarczają informacji na temat zabezpieczeń sprawdzanych przez środowisko uruchomieniowe języka wspólnego dla aplikacji. W poniższej tabeli opisano liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**# Sprawdzanie w trakcie wykonywania łącza**|Wyświetla całkowitą liczbę zabezpieczenia dostępu kodu w czasie konsolidacji sprawdza, czy od czasu uruchomienia aplikacji. Kontrole zabezpieczeń dostępu kodu w czasie konsolidacji są wykonywane, gdy obiekt wywołujący żąda określonego uprawnienia w czasie kompilacji just in time (JIT). Sprawdź czas łącza jest wykonywana raz dla obiekt wywołujący. Ten licznik nie jest świadczy poważnych problemów z wydajnością; jest jedynie świadczy o działania systemu zabezpieczeń.|  
|**% Czasu potrzebnego na sprawdzenie RT**|Przedstawia wartość procentową czasu wykonywania środowiska uruchomieniowego kodu dostępu do kontroli zabezpieczeń od ostatniej próbki. Ten licznik jest aktualizowany po zakończeniu sprawdzania zabezpieczeń .NET Framework. Nie jest to wartość średnia; reprezentuje ostatnią odczytaną wartość.|  
|**% Czasu Sig uwierzytelniania**|Zarezerwowane do użytku w przyszłości.|  
|**Głębokość przeszukiwania stosu**|Przedstawia Głębokość stosu podczas ostatniego sprawdzanie zabezpieczeń dostępu kodu środowiska uruchomieniowego. Kontrole zabezpieczeń dostępu kodu środowiska uruchomieniowego są wykonywane przez przejście na stosie. Ten licznik nie jest to wartość średnia; Wyświetla ostatnią odczytaną wartość.|  
|**Sprawdzanie łącznego czasu wykonywania**|Wyświetla całkowitą liczbę kod środowiska uruchomieniowego dostępu kontroli zabezpieczeń wykonywane od czasu uruchomienia aplikacji. Kod środowiska uruchomieniowego dostęp zabezpieczeń, które testy są wykonywane, gdy obiekt wywołujący żąda określonego uprawnienia. Sprawdzanie środowiska uruchomieniowego zostało utworzone przy każdym wywołaniu przez wywołującego i sprawdza bieżącego stosu wątków obiektu wywołującego. W przypadku użycia z **zaprezentuje Głębokość stosu** licznika, ten licznik wskazuje występuje dla kontroli zabezpieczenia pogorszenia wydajności.|  
  
## <a name="see-also"></a>Zobacz też  
 [Liczniki wydajności](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 [Profilowanie środowiska uruchomieniowego](../../../docs/framework/debug-trace-profile/runtime-profiling.md)
