---
title: Liczniki wydajności w oprogramowaniu .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- performance, .NET Framework applications
- performance counters
- performance monitoring, counters
ms.assetid: 06a4ae8c-eeb2-4d5a-817e-b1b95c0653e1
ms.openlocfilehash: a592cbb49c1b9ec8f36b90f2ec1097f6c84efbe9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281808"
---
# <a name="performance-counters-in-the-net-framework"></a>Liczniki wydajności w .NET Framework

Ten temat zawiera listę liczników wydajności, które można znaleźć w [monitorze wydajności systemu Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc749249%28v=ws.11%29).  

## <a name="exception-performance-counters"></a>Liczniki wydajności wyjątków  
 Kategoria wyjątków środowiska CLR programu .NET Console zawiera liczniki, które zawierają informacje o wyjątkach zgłaszanych przez aplikację. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**liczba zgłoszonych wyjątków**|Przedstawia łączną liczbę wyjątków zgłoszonych od momentu uruchomienia aplikacji. Dotyczy to zarówno wyjątków .NET, jak i niezarządzanych wyjątków, które są konwertowane na wyjątki platformy .NET. Na przykład wynik HRESULT zwrócony z kodu niezarządzanego jest konwertowany na wyjątek w kodzie zarządzanym.<br /><br /> Ten licznik obejmuje zarówno obsłużone, jak i Nieobsłużone wyjątki. Ponownie zliczane wyjątki.|  
|**liczba zgłoszonych wyjątków/s**|Wyświetla liczbę zgłoszonych wyjątków na sekundę. Dotyczy to zarówno wyjątków .NET, jak i niezarządzanych wyjątków, które są konwertowane na wyjątki platformy .NET. Na przykład wynik HRESULT zwrócony z kodu niezarządzanego jest konwertowany na wyjątek w kodzie zarządzanym.<br /><br /> Ten licznik obejmuje zarówno obsłużone, jak i Nieobsłużone wyjątki. Nie jest to średnia w czasie; Wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzieloną przez czas trwania interwału próbkowania. Ten licznik jest wskaźnikiem potencjalnych problemów z wydajnością w przypadku zgłoszenia dużej liczby wyjątków (> 100s).|  
|**liczba filtrów/s**|Wyświetla liczbę filtrów wyjątków programu .NET wykonywanych w ciągu sekundy. Filtr wyjątku jest obliczany niezależnie od tego, czy wyjątek jest obsługiwany.<br /><br /> Ten licznik nie jest średnią w czasie; Wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzieloną przez czas trwania interwału próbkowania.|  
|**Liczba finally/s**|Wyświetla liczbę bloków finally wykonywanych w ciągu sekundy. Blok finally jest gwarantowany do wykonania niezależnie od tego, jak został zakończony blok try.  Zliczane są tylko bloki finally wykonane dla wyjątku; bloki finally w normalnych ścieżkach kodu nie są zliczane przez ten licznik.<br /><br /> Ten licznik nie jest średnią w czasie; Wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzieloną przez czas trwania interwału próbkowania.|  
|**Rzutowanie na głębokość catch/s**|Wyświetla liczbę ramek stosu przepływających od klatki, która zgłosiła wyjątek do ramki, która obsługiwała wyjątek, na sekundę. Ten licznik resetuje do zera, gdy zostanie wprowadzona procedura obsługi wyjątków, więc zagnieżdżone wyjątki pokazują głębokość stosu obsługi do obsługi.<br /><br /> Ten licznik nie jest średnią w czasie; Wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzieloną przez czas trwania interwału próbkowania.|  
     
## <a name="interop-performance-counters"></a>Liczniki wydajności międzyoperacyjności  
 Kategoria programu .NET Interop dla środowiska URUCHOMIENIOWego w konsoli wydajności zawiera liczniki, które zawierają informacje o interakcjach aplikacji ze składnikami modelu COM, usługami COM+ i zewnętrznymi bibliotekami typów. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Liczba CCWs**|Wyświetla bieżącą liczbę wywoływanych otok COM (CCWs). CCW jest serwerem proxy dla obiektu zarządzanego, do którego odwołuje się niezarządzany klient COM. Ten licznik wskazuje liczbę zarządzanych obiektów, do których odwołuje się kod niezarządzany COM.|  
|**Liczba elementów kierujących**|Wyświetla łączną liczbę przypadków, w których argumenty i wartości zwracane zostały przekazane z kodu zarządzanego do niezarządzanego i na odwrót, od momentu uruchomienia aplikacji. Ten licznik nie jest zwiększany, jeśli podklasy są wbudowane. (Wycinki są odpowiedzialne za kierowanie argumentów i zwracanych wartości). Wycinki są zwykle wbudowane, jeśli narzutowanie jest małe.|  
|**Liczba wycinków**|Przedstawia bieżącą liczbę wycinków utworzonych przez środowisko uruchomieniowe języka wspólnego. Wycinki są odpowiedzialne za kierowanie argumentów i zwracanie wartości z zarządzanego do niezarządzanego kodu, a na odwrót — w trakcie wywołania międzyoperacyjnego modelu COM lub wywołania platformy.|  
|**Liczba operacji eksportu TLB/s**|Zarezerwowane do użytku w przyszłości.|  
|**Liczba importowanych buforów TLB/s**|Zarezerwowane do użytku w przyszłości.|  
    
## <a name="jit-performance-counters"></a>liczniki wydajności JIT  
 Kategoria kompilatora wydajności JIT środowiska .NET CLR zawiera liczniki, które zawierają informacje o kodzie, który został skompilowany przez JIT. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Liczba bajtów trybie JIT IL**|Wyświetla całkowitą liczbę bajtów języka pośredniego firmy Microsoft (MSIL) kompilowanych przez kompilator just-in-Time (JIT) od momentu uruchomienia aplikacji. Ten licznik jest odpowiednikiem **łącznej liczby trybie JIT licznika Il bajtów** .|  
|**Liczba metod trybie JIT**|Przedstawia łączną liczbę metod, które zostały skompilowane JIT od momentu uruchomienia aplikacji. Ten licznik nie obejmuje metod skompilowanych przed JIT.|  
|**Czas (%) w JIT**|Przedstawia wartość procentową czasu spędzonego w kompilacji JIT od ostatniej fazy kompilacji JIT. Ten licznik jest aktualizowany na końcu każdej fazy kompilacji JIT. Faza kompilacji JIT występuje, gdy metoda i jej zależności są kompilowane.|  
|**Bajty IL trybie JIT/s**|Wyświetla liczbę bajtów MSIL, które są kompilowane w trybie JIT na sekundę. Ten licznik nie jest średnią w czasie; Wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzieloną przez czas trwania interwału próbkowania.|  
|**Standardowe błędy JIT**|Wyświetla szczytową liczbę metod, które kompilator JIT nie mógł skompilować od momentu uruchomienia aplikacji. Ten błąd może wystąpić, jeśli nie można zweryfikować MSIL lub wystąpił błąd wewnętrzny kompilatora JIT.|  
|**Łączna liczba bajtów trybie JIT IL**|Przedstawia łączną liczbę bajtów MSIL skompilowanych JIT od momentu uruchomienia aplikacji. Ten licznik jest równoważny licznikowi **trybie JIT bajtów Il** .|  
     
## <a name="loading-performance-counters"></a>Ładowanie liczników wydajności  
 Kategoria ładowania CLR programu .NET Console zawiera liczniki, które zawierają informacje o zestawach, klasach i domenach aplikacji, które są ładowane. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Czas ładowania (%)**|Zarezerwowane do użytku w przyszłości.|  
|**Długość wyszukiwania zestawu**|Zarezerwowane do użytku w przyszłości.|  
|**Bajty w stercie modułu ładującego**|Wyświetla bieżący rozmiar (w bajtach) pamięci zatwierdzonej przez program ładujący klasy we wszystkich domenach aplikacji. Pamięć zadeklarowana to miejsce fizyczne zarezerwowane w pliku stronicowania dysku.|  
|**Bieżące domeny aplikacji**|Przedstawia bieżącą liczbę domen aplikacji załadowanych w tej aplikacji.|  
|**Bieżące zestawy**|Wyświetla bieżącą liczbę zestawów załadowanych we wszystkich domenach aplikacji w aktualnie uruchomionej aplikacji. Jeśli zestaw jest ładowany jako neutralny dla domeny z wielu domen aplikacji, ten licznik jest zwiększany tylko raz.|  
|**Załadowane bieżące klasy**|Wyświetla bieżącą liczbę klas załadowanych we wszystkich zestawach.|  
|**Szybkość domen aplikacji**|Przedstawia liczbę ładowanych domen aplikacji na sekundę. Ten licznik nie jest średnią w czasie; Wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzieloną przez czas trwania interwału próbkowania.|  
|**Szybkość niezaładowanych elementów AppDomain**|Przedstawia liczbę zwolnionych domen aplikacji na sekundę. Ten licznik nie jest średnią w czasie; Wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzieloną przez czas trwania interwału próbkowania.|  
|**Współczynnik zestawów**|Przedstawia liczbę zestawów załadowanych na sekundę we wszystkich domenach aplikacji. Jeśli zestaw jest ładowany jako neutralny dla domeny z wielu domen aplikacji, ten licznik jest zwiększany tylko raz.<br /><br /> Ten licznik nie jest średnią w czasie; Wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzieloną przez czas trwania interwału próbkowania.|  
|**Liczba załadowanych klas**|Wyświetla liczbę klas załadowanych na sekundę we wszystkich zestawach. Ten licznik nie jest średnią w czasie; Wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzieloną przez czas trwania interwału próbkowania.|  
|**Szybkość niepowodzeń ładowania**|Wyświetla liczbę klas, które nie zostały załadowane na sekundę. Ten licznik nie jest średnią w czasie; Wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzieloną przez czas trwania interwału próbkowania.<br /><br /> Błędy ładowania mogą wystąpić z wielu powodów, takich jak niedostateczne zabezpieczenia lub nieprawidłowy format. Aby uzyskać szczegółowe informacje, zobacz profilowanie pomocy usług.|  
|**Łączna liczba błędów ładowania**|Wyświetla szczytową liczbę klas, których załadowanie nie powiodło się od momentu uruchomienia aplikacji.<br /><br /> Błędy ładowania mogą wystąpić z wielu powodów, takich jak niedostateczne zabezpieczenia lub nieprawidłowy format. Aby uzyskać szczegółowe informacje, zobacz profilowanie pomocy usług.|  
|**Łączna liczba domen aplikacji**|Wyświetla szczytową liczbę domen aplikacji załadowanych od momentu uruchomienia aplikacji.|  
|**Łączna liczba domen aplikacji zwolnionych**|Przedstawia łączną liczbę zwolnionych domen aplikacji od momentu uruchomienia aplikacji. Jeśli domena aplikacji zostanie załadowana i zwolniona wielokrotnie, ten licznik rośnie za każdym razem, gdy domena aplikacji zostanie zwolniona.|  
|**Łączna liczba zestawów**|Wyświetla łączną liczbę zestawów załadowanych od momentu uruchomienia aplikacji. Jeśli zestaw jest ładowany jako neutralny dla domeny z wielu domen aplikacji, ten licznik jest zwiększany tylko raz.|  
|**Łączna liczba załadowanych klas**|Przedstawia skumulowaną liczbę klas załadowanych we wszystkich zestawach od momentu uruchomienia aplikacji.|  
   
## <a name="lock-and-thread-performance-counters"></a>Liczniki wydajności blokady i wątku  
 Kategoria programu .NET CLR LocksAndThreads z konsolą wydajności zawiera liczniki, które zawierają informacje o zarządzanych blokadach i wątkach używanych przez aplikację. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**liczba bieżących wątków logicznych**|Przedstawia liczbę aktualnie zarządzanych obiektów wątków w aplikacji. Ten licznik przechowuje liczbę uruchomionych i zatrzymanych wątków. Ten licznik nie jest średnią w czasie; zostanie wyświetlona tylko Ostatnia obserwowana wartość.|  
|**liczba bieżących wątków fizycznych**|Przedstawia liczbę natywnych wątków systemu operacyjnego utworzonych i należących do środowiska uruchomieniowego języka wspólnego, aby działały jako wątki bazowe dla obiektów wątku zarządzanego. Wartość tego licznika nie obejmuje wątków używanych przez środowisko uruchomieniowe w ramach operacji wewnętrznych; jest to podzestaw wątków w procesie systemu operacyjnego.|  
|**Liczba aktualnie rozpoznawanych wątków**|Wyświetla liczbę wątków, które są aktualnie rozpoznawane przez środowisko uruchomieniowe. Te wątki są skojarzone z odpowiednim obiektem zarządzanego wątku. Środowisko uruchomieniowe nie tworzy tych wątków, ale zostały uruchomione w środowisku uruchomieniowym co najmniej raz.<br /><br /> Śledzone są tylko unikatowe wątki; wątki z tym samym IDENTYFIKATORem wątku, który ponownie wprowadzają środowisko uruchomieniowe lub są ponownie tworzone po zakończeniu wątku, nie są zliczane dwa razy.|  
|**Łączna liczba rozpoznanych wątków**|Przedstawia łączną liczbę wątków, które zostały rozpoznane przez środowisko uruchomieniowe od momentu uruchomienia aplikacji. Te wątki są skojarzone z odpowiednim obiektem zarządzanego wątku. Środowisko uruchomieniowe nie tworzy tych wątków, ale zostały uruchomione w środowisku uruchomieniowym co najmniej raz.<br /><br /> Śledzone są tylko unikatowe wątki; wątki z tym samym IDENTYFIKATORem wątku, który ponownie wprowadzają środowisko uruchomieniowe lub są ponownie tworzone po zakończeniu wątku, nie są zliczane dwa razy.|  
|**Współczynnik rywalizacji/s**|Przedstawia szybkość, z jaką wątki w czasie wykonywania próbują uzyskać zarządzaną blokadę, która nie powiodła się.|  
|**Bieżąca długość kolejki**|Przedstawia łączną liczbę wątków, które aktualnie oczekują na uzyskanie zarządzanej blokady w aplikacji. Ten licznik nie jest średnią w czasie; zostanie wyświetlona Ostatnia obserwowana wartość.|  
|**Długość kolejki/s**|Przedstawia liczbę wątków na sekundę, które oczekują na uzyskanie blokady w aplikacji. Ten licznik nie jest średnią w czasie; Wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzieloną przez czas trwania interwału próbkowania.|  
|**Szczytowa długość kolejki**|Przedstawia łączną liczbę wątków, które oczekują na uzyskanie blokady zarządzanej od momentu uruchomienia aplikacji.|  
|**częstotliwość rozpoznanych wątków/s**|Przedstawia liczbę wątków na sekundę, które zostały rozpoznane przez środowisko uruchomieniowe. Te wątki są skojarzone z odpowiednim obiektem zarządzanego wątku. Środowisko uruchomieniowe nie tworzy tych wątków, ale zostały uruchomione w środowisku uruchomieniowym co najmniej raz.<br /><br /> Śledzone są tylko unikatowe wątki; wątki z tym samym IDENTYFIKATORem wątku, który ponownie wprowadzają środowisko uruchomieniowe lub są ponownie tworzone po zakończeniu wątku, nie są zliczane dwa razy.<br /><br /> Ten licznik nie jest średnią w czasie; Wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzieloną przez czas trwania interwału próbkowania.|  
|**Łączna liczba rywalizacji**|Przedstawia łączną liczbę przypadków, w których wątki w czasie wykonywania próbowały uzyskać zarządzaną blokadę, która nie powiodła się.|  
    
## <a name="memory-performance-counters"></a>Liczniki wydajności pamięci  
 Kategoria pamięci CLR programu .NET Console zawiera liczniki, które dostarczają informacji na temat modułu wyrzucania elementów bezużytecznych. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Liczba bajtów we wszystkich stertach**|Wyświetla sumę **rozmiaru sterty generacji 1**, **rozmiaru sterty generacji 2**i liczników **rozmiaru sterty dla dużego obiektu** . Ten licznik wskazuje bieżącą pamięć przydzieloną w bajtach na sterty wyrzucania elementów bezużytecznych.|  
|**Liczba dojść do # GC**|Wyświetla bieżącą liczbę dojść do wyrzucania elementów bezużytecznych w użyciu. Dojścia do wyrzucania elementów bezużytecznych są dojściami do zasobów zewnętrznych względem środowiska uruchomieniowego języka wspólnego i środowiska zarządzanego.|  
|**Liczba kolekcji generacji 0**|Przedstawia liczbę obiektów generacji 0 (czyli najwygodniejszych, ostatnio przyznanych obiektów), które są zbierane jako elementy bezużyteczne od momentu uruchomienia aplikacji.<br /><br /> Wyrzucanie elementów bezużytecznych generacji 0 występuje, gdy dostępna pamięć w generacji 0 nie wystarcza do spełnienia żądania alokacji. Licznik jest zwiększany na końcu wyrzucania elementów bezużytecznych generacji 0. Wyrzucanie elementów bezużytecznych z większą generacji obejmuje wszystkie kolekcje o mniejszych generacjach. Ten licznik jest jawnie zwiększany w przypadku wystąpienia większej generacji (generacji 1 lub 2) wyrzucania elementów bezużytecznych.<br /><br /> Ten licznik wyświetla ostatnią obserwowana wartość. Wartość licznika **\__global** nie jest dokładna i powinna być ignorowana.|  
|**Liczba kolekcji generacji 1**|Przedstawia liczbę obiektów generacji 1, które są zbierane jako elementy bezużyteczne od momentu uruchomienia aplikacji.<br /><br /> Licznik jest zwiększany po zakończeniu wyrzucania elementów bezużytecznych generacji 1. Wyrzucanie elementów bezużytecznych z większą generacji obejmuje wszystkie kolekcje o mniejszych generacjach. Ten licznik jest jawnie zwiększany, gdy następuje wyrzucanie elementów bezużytecznych generacji (generacja 2).<br /><br /> Ten licznik wyświetla ostatnią obserwowana wartość. Wartość licznika **\__global** nie jest dokładna i powinna być ignorowana.|  
|**Liczba kolekcji generacji 2**|Przedstawia, ile razy obiekty generacji 2 są zbierane jako elementy bezużyteczne od momentu uruchomienia aplikacji. Licznik jest zwiększany na końcu wyrzucania elementów bezużytecznych generacji 2 (nazywane również pełnym odzyskiwaniem pamięci).<br /><br /> Ten licznik wyświetla ostatnią obserwowana wartość. Wartość licznika **\__global** nie jest dokładna i powinna być ignorowana.|  
|**# Wywołano GC**|Wyświetla szczytową liczbę przypadków wykonania wyrzucania elementów bezużytecznych z powodu jawnego wywołania <xref:System.GC.Collect%2A?displayProperty=nameWithType>. Dobrym sposobem jest umożliwienie modułowi zbierającemu elementy bezużyteczne dostrajania częstotliwości jego kolekcji.|  
|**Liczba przypiętych obiektów**|Wyświetla liczbę przypiętych obiektów napotkanych w ostatnim wyrzucaniu elementów bezużytecznych. Przypięty obiekt jest obiektem, który nie może zostać przeniesiony w pamięci. Ten licznik śledzi obiekty przypięte tylko w stertach, które są zbierane jako elementy bezużyteczne. Na przykład wyrzucanie elementów bezużytecznych generacji 0 powoduje Wyliczenie przypiętych obiektów tylko w stercie generacji 0.|  
|**Liczba bloków ujścia w użyciu**|Wyświetla bieżącą liczbę bloków synchronizacji w użyciu. Bloki synchronizacji są strukturami danych dla obiektów przydzielonymi do przechowywania informacji o synchronizacji. Przechowują one słabe odwołania do obiektów zarządzanych i muszą być skanowane przez moduł wyrzucania elementów bezużytecznych. Bloki synchronizacji nie są ograniczone do przechowywania informacji o synchronizacji; mogą także przechowywać metadane międzyoperacyjności modelu COM. Ten licznik wskazuje problemy z wydajnością przy dużym użyciu podstawowych elementów synchronizacji.|  
|**Liczba zadeklarowanych bajtów**|Wyświetla ilość pamięci wirtualnej (w bajtach) aktualnie zatwierdzonej przez moduł wyrzucania elementów bezużytecznych. Pamięć zadeklarowana to pamięć fizyczna, dla której zarezerwowano miejsce w pliku stronicowania dysku.|  
|**Liczba zarezerwowanych bajtów**|Wyświetla ilość pamięci wirtualnej (w bajtach) aktualnie zarezerwowaną przez moduł wyrzucania elementów bezużytecznych. Zarezerwowana pamięć to przestrzeń pamięci wirtualnej zarezerwowana dla aplikacji, gdy nie zostały użyte żadne strony dysku lub pamięci głównej.|  
|**Czas (%) w GC**|Przedstawia procent czasu, który upłynął podczas wykonywania wyrzucania elementów bezużytecznych od momentu ostatniego cyklu wyrzucania elementów bezużytecznych. Ten licznik zazwyczaj wskazuje prace wykonywane przez moduł wyrzucania elementów bezużytecznych w celu zbierania i kompaktowania pamięci w imieniu aplikacji. Ten licznik jest aktualizowany tylko na końcu wszystkich wyrzucania elementów bezużytecznych. Ten licznik nie jest średnią; jego wartość odzwierciedla ostatnią zaobserwowanej wartości.|  
|**Przydzielono bajtów/sekundę**|Wyświetla liczbę bajtów na sekundę przydzieloną na stercie wyrzucania elementów bezużytecznych. Ten licznik jest aktualizowany na końcu każdej operacji wyrzucania elementów bezużytecznych, a nie przy każdej alokacji. Ten licznik nie jest średnią w czasie; Wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzieloną przez czas trwania interwału próbkowania.|  
|**Osoby przeżyjąjące zakończenie**|Przedstawia liczbę obiektów zebranych w pamięci podręcznej, które przeżyły do kolekcji, ponieważ oczekują na sfinalizowanie. Jeśli te obiekty przechowują odwołania do innych obiektów, te obiekty również przeżyły, ale nie są zliczane przez ten licznik. **Podwyższona wartość finalizowania pamięci z licznika generacji 0** reprezentuje całą pamięć, która została przeżyły z powodu finalizacji.<br /><br /> Ten licznik nie jest skumulowany; jest ona aktualizowana na końcu każdego wyrzucania elementów bezużytecznych z liczbą osób, które są używane tylko w danej kolekcji. Ten licznik wskazuje dodatkowe obciążenie, które aplikacja może ponieść ze względu na finalizację.|  
|**Rozmiar sterty generacji 0**|Wyświetla maksymalną liczbę bajtów, które mogą być przydzieloną w generacji 0; nie wskazuje na bieżącą liczbę bajtów przydzieloną w generacji 0.<br /><br /> Wyrzucanie elementów bezużytecznych generacji 0 występuje, gdy przydziały od momentu ostatniej kolekcji przekroczą ten rozmiar. Rozmiar generacji 0 jest dostrojony przez moduł wyrzucania elementów bezużytecznych i może ulec zmianie podczas wykonywania aplikacji. Na końcu kolekcji generacji 0 rozmiar sterty generacji 0 wynosi 0 bajtów. Ten licznik wyświetla rozmiar (w bajtach) przydziałów, które wywołuje wyrzucanie elementów bezużytecznych następnej generacji 0.<br /><br /> Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, a nie przy każdej alokacji.|  
|**Liczba bajtów awansowanych generacji 0/s**|Wyświetla liczbę bajtów na sekundę, które są podwyższane z generacji 0 do generacji 1. Pamięć jest podwyższana, gdy przeżyje odzyskiwanie pamięci. Ten licznik jest wskaźnikiem obiektów o stosunkowo długim czasie, które są tworzone na sekundę.<br /><br /> Ten licznik wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzieloną przez czas trwania interwału próbkowania.|  
|**Rozmiar sterty generacji 1**|Wyświetla bieżącą liczbę bajtów w generacji 1; Ten licznik nie wyświetla maksymalnego rozmiaru generacji 1. Obiekty nie są bezpośrednio przydzielne w tej generacji; są one promowane z wyrzucania elementów bezużytecznych poprzedniej generacji 0. Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, a nie przy każdej alokacji.|  
|**Wyróżnione bajty generacji 1/s**|Wyświetla liczbę bajtów na sekundę, które są podwyższane z generacji 1 do generacji 2. Obiekty, które są promowane tylko dlatego, że oczekują na sfinalizowanie, nie są uwzględnione w tym liczniku.<br /><br /> Pamięć jest podwyższana, gdy przeżyje odzyskiwanie pamięci. Brak promocji z generacji 2, ponieważ jest to najstarsza generacja. Ten licznik jest wskaźnikiem bardzo długotrwałych obiektów tworzonych w ciągu sekundy.<br /><br /> Ten licznik wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzieloną przez czas trwania interwału próbkowania.|  
|**Rozmiar sterty generacji 2**|Wyświetla bieżącą liczbę bajtów w generacji 2. Obiekty nie są bezpośrednio przydzielne w tej generacji; są one promowane od generacji 1 w trakcie odzyskiwania pamięci poprzedniej generacji 1. Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, a nie przy każdej alokacji.|  
|**Rozmiar sterty dla dużego obiektu**|Wyświetla bieżący rozmiar sterty dużego obiektu w bajtach. Obiekty, które są większe niż około 85 000 bajtów są traktowane jako duże obiekty przez moduł wyrzucania elementów bezużytecznych i są bezpośrednio przydzielane w specjalnej stercie. Nie są one promowane w ramach generacji. Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, a nie przy każdej alokacji.|  
|**Identyfikator procesu**|Wyświetla identyfikator procesu monitorowanego wystąpienia procesu CLR.|  
|**Awansowana finalizowanie pamięci z generacji 0**|Wyświetla bajty pamięci, które są podwyższane z generacji 0 do generacji 1 tylko ponieważ oczekują na sfinalizowanie. Ten licznik nie jest skumulowany; Wyświetla wartość zaobserwowana na końcu ostatniego wyrzucania elementów bezużytecznych.|  
|**Podwyższona ilość pamięci z generacji 0**|Wyświetla bajty pamięci, które przeżyły do wyrzucania elementów bezużytecznych i są podwyższane z generacji 0 do generacji 1. Obiekty, które są promowane tylko dlatego, że oczekują na sfinalizowanie, nie są uwzględnione w tym liczniku. Ten licznik nie jest skumulowany; Wyświetla wartość zaobserwowana na końcu ostatniego wyrzucania elementów bezużytecznych.|  
|**Podwyższona ilość pamięci z generacji 1**|Wyświetla bajty pamięci, które przeżyły do wyrzucania elementów bezużytecznych i zostały podwyższone z generacji 1 do generacji 2. Obiekty, które są promowane tylko dlatego, że oczekują na sfinalizowanie, nie są uwzględnione w tym liczniku. Ten licznik nie jest skumulowany; Wyświetla wartość zaobserwowana na końcu ostatniego wyrzucania elementów bezużytecznych. Ten licznik jest resetowany do wartości 0, jeśli ostatnie wyrzucanie elementów bezużytecznych było tylko kolekcjami generacji 0.|  
     
## <a name="networking-performance-counters"></a>Liczniki wydajności sieci  

Kategoria sieci środowiska CLR programu .NET Console zawiera liczniki, które zawierają informacje o danych wysyłanych i odbieranych przez sieć. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Bajty odebrane**|Skumulowana łączna liczba bajtów odebranych przez wszystkie <xref:System.Net.Sockets.Socket> obiektów w ramach <xref:System.AppDomain> od momentu uruchomienia procesu. Ta liczba obejmuje dane i wszelkie informacje o protokole, które nie są zdefiniowane przez TCP/IP.|  
|**Bajty wysłane**|Skumulowana liczba bajtów wysłanych przez wszystkie <xref:System.Net.Sockets.Socket> obiektów w ramach <xref:System.AppDomain> od momentu uruchomienia procesu. Ta liczba obejmuje dane i wszelkie informacje o protokole, które nie są zdefiniowane przez TCP/IP.|  
|**Nawiązano połączenia**|Skumulowana łączna liczba obiektów <xref:System.Net.Sockets.Socket> dla gniazd strumienia, które były kiedykolwiek połączone w <xref:System.AppDomain> od momentu uruchomienia procesu.|  
|**Odebrane datagramy**|Skumulowana łączna liczba pakietów datagramów odebranych przez wszystkie <xref:System.Net.Sockets.Socket> obiektów w ramach <xref:System.AppDomain> od momentu uruchomienia procesu.|  
|**Wysłane datagramy**|Skumulowana łączna liczba pakietów datagramów wysłanych przez wszystkie <xref:System.Net.Sockets.Socket> obiektów w ramach <xref:System.AppDomain> od momentu uruchomienia procesu.|  
|**Średni czas istnienia HttpWebRequest**|Średni czas ukończenia dla wszystkich obiektów <xref:System.Net.HttpWebRequest>, które zakończyły się w ostatnim interwale w <xref:System.AppDomain> od momentu rozpoczęcia procesu.|  
|**Średni czas kolejki HttpWebRequest**|Średni czas w kolejce dla wszystkich obiektów <xref:System.Net.HttpWebRequest>, które opuściły kolejkę w ostatnim interwale w <xref:System.AppDomain> od momentu uruchomienia procesu.|  
|**HttpWebRequests utworzone/s**|Liczba obiektów <xref:System.Net.HttpWebRequest> utworzonych na sekundę w <xref:System.AppDomain>.|  
|**HttpWebRequests w kolejce/s**|Liczba obiektów <xref:System.Net.HttpWebRequest>, które zostały dodane do kolejki na sekundę w <xref:System.AppDomain>.|  
|**HttpWebRequests przerwane/s**|Liczba obiektów <xref:System.Net.HttpWebRequest>, w których aplikacja wywołała metodę <xref:System.Net.HttpWebRequest.Abort%2A> na sekundę w <xref:System.AppDomain>.|  
|**Niepowodzenie HttpWebRequests/s**|Liczba obiektów <xref:System.Net.HttpWebRequest>, które otrzymały kod stanu błędu z serwera na sekundę w <xref:System.AppDomain>.|  
  
 Obsługiwane są kilka klas liczników wydajności sieci:  
  
- Liczniki zdarzeń mierzące liczbę wystąpień pewnego zdarzenia.  
  
- Liczniki danych mierzące ilość wysłanych lub odebranych danych.  
  
- Liczniki czasu trwania mierzące, jak długo trwają różne procesy. Czasy są mierzone na obiektach każdego interwału (zwykle w sekundach) po wyjściu z różnych stanów.  
  
- Liczniki dla interwałów, które mierzą liczbę obiektów tworzących określone przejście na interwał (zwykle na sekundę).  
  
Dostępne są następujące liczniki wydajności sieci dla zdarzeń:  
  
- **Nawiązano połączenia**  
  
- **Odebrane datagramy**  
  
- **Wysłane datagramy**  
  
 Te liczniki wydajności udostępniają liczby od momentu rozpoczęcia procesu. Liczba ustanowionych połączeń <xref:System.Net.Sockets.Socket> obejmuje jawne wywołania metody <xref:System.Net.Sockets.Socket> przez aplikację dla połączenia gniazda usługi Stream, które zostało nawiązane, a także wywołania wewnętrzne wykonane przez inne klasy (na przykład<xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.WebClient>i <xref:System.Net.Sockets.TcpClient>) do klasy <xref:System.Net.Sockets.Socket>  
  
 Liczby odbieranych i **wysyłanych** **datagramów obejmują pakiety datag** wysłane lub odebrane przy użyciu jawnej metody <xref:System.Net.Sockets.Socket> wywołań przez aplikację, a także wywołania wewnętrzne wykonane przez inne klasy (na przykład<xref:System.Net.Sockets.UdpClient>) do <xref:System.Net.Sockets.Socket>. określonej. Liczba **odebranych datagramów** i **wysłanych** datagramy mogą być również używane w celu zapewnienia bardzo surowej miary liczby bajtów wysłanych lub odebranych za pomocą datagramy przy założeniu, że średni rozmiar datagramu.  
  
 Dostępne są następujące liczniki wydajności sieci dla danych:  
  
- **Bajty odebrane**  
  
- **Bajty wysłane**  
  
 Powyższe liczniki zapewniają liczbę bajtów od momentu rozpoczęcia procesu.  
  
 Istnieją dwa liczniki czasu trwania, które mierzą, jak długo zajęło <xref:System.Net.HttpWebRequest> obiektów do przekazywania przez cały cykl życia lub po prostu jego część:  
  
- **Średni czas istnienia HttpWebRequest**  
  
- **Średni czas kolejki HttpWebRequest**  
  
 W przypadku licznika **okresu istnienia HttpWebRequest średni** czas istnienia większości obiektów <xref:System.Net.HttpWebRequest> zawsze zaczyna się od momentu utworzenia obiektu aż do momentu zamknięcia strumienia odpowiedzi przez aplikację. Istnieją dwa nietypowe przypadki:  
  
- Jeśli aplikacja nigdy nie wywołuje metod <xref:System.Net.HttpWebRequest.GetResponse%2A> lub <xref:System.Net.HttpWebRequest.BeginGetResponse%2A>, okres istnienia obiektu <xref:System.Net.HttpWebRequest> jest ignorowany.  
  
- Jeśli obiekt <xref:System.Net.HttpWebRequest> zgłasza <xref:System.Net.WebException> podczas wywoływania <xref:System.Net.HttpWebRequest.GetResponse%2A> lub <xref:System.Net.HttpWebRequest.EndGetResponse%2A> metod, okres istnienia zostanie zakończony, gdy zostanie zgłoszony wyjątek. Technicznie, źródłowy strumień odpowiedzi jest również zamykany w tym momencie (strumień odpowiedzi zwrócony do użytkownika to naprawdę strumień pamięci zawierający kopię strumienia odpowiedzi).  
  
 Istnieją cztery liczniki, które śledzą niektóre <xref:System.Net.HttpWebRequest> problemy dotyczące obiektów na interwał. Te liczniki wydajności mogą pomóc deweloperom aplikacji, administratorom i pracownikom pomocy technicznej lepiej zrozumieć działanie obiektów <xref:System.Net.HttpWebRequest>. Dostępne są następujące liczniki:  
  
- **HttpWebRequests utworzone/s**  
  
- **HttpWebRequests w kolejce/s**  
  
- **HttpWebRequests przerwane/s**  
  
- **Niepowodzenie HttpWebRequests/s**  
  
 W przypadku licznika **przerwanych HttpWebRequests/s** zliczane są również wywołania wewnętrzne <xref:System.Net.HttpWebRequest.Abort%2A>. Te wywołania wewnętrzne są zwykle spowodowane przekroczeniem limitu czasu, które aplikacja może chcieć zmierzyć.  
  
 Licznik **HttpWebRequests zakończonych niepowodzeniem/s** zawiera liczbę obiektów <xref:System.Net.HttpWebRequest>, które otrzymały kod stanu niepowodzenia z serwera na sekundę. Oznacza to, że kod stanu otrzymany z serwera http na końcu żądania nie był w zakresie od 200 do 299. Kody stanu, które są obsługiwane i powodują, że nowe żądanie (wiele nieautoryzowanych kodów stanu 401, na przykład) zakończy się niepowodzeniem lub nie powiedzie się na podstawie wyniku ponowienia próby. Jeśli aplikacja zobaczy błąd w oparciu o ponowienie próby, licznik zostanie zwiększony.  
  
 Liczniki wydajności sieci są dostępne i zarządzane przy użyciu <xref:System.Diagnostics.PerformanceCounter> i powiązanych klas w przestrzeni nazw <xref:System.Diagnostics>. Liczniki wydajności sieci można także wyświetlić za pomocą konsoli monitora wydajności systemu Windows.  
  
 Liczniki wydajności sieci muszą być włączone w pliku konfiguracji, który ma być używany. Wszystkie liczniki wydajności sieci są włączone lub wyłączone przy użyciu jednego ustawienia w pliku konfiguracji. Nie można włączyć lub wyłączyć poszczególnych liczników wydajności sieci. Aby uzyskać więcej informacji, zobacz [\<performanceCounter > elementu (Ustawienia sieci)](../configure-apps/file-schema/network/performancecounter-element-network-settings.md).  
  
 W przypadku włączenia liczników sieci spowoduje to utworzenie i zaktualizowanie zarówno liczników wydajności dla domeny aplikacji, jak i globalnych. Jeśli ta funkcja jest wyłączona, aplikacja nie będzie dostarczać żadnych danych licznika wydajności sieci.  
  
 Liczniki wydajności są pogrupowane w kategorie. Aplikacja może wyświetlić listę wszystkich kategorii z następującym przykładowym kodem:  
  
```csharp
PerformanceCounterCategory[] Array = PerformanceCounterCategory.GetCategories();  
for (int i = 0; i < Array.Length; i++)  
{  
    Console.Out.WriteLine("{0}. Name={1} Help={2}", i, Array[i].CategoryName, Array[i].CategoryHelp);  
}  
```  
  
 Liczniki wydajności sieci są wymienione w dwóch kategoriach:  
  
- "Sieć CLR platformy .NET" — oryginalne liczniki wydajności wprowadzone w .NET Framework wersji 2 i obsługiwane w .NET Framework wersji 2 i nowszych.  
  
- ".NET CLR Networking 4.0.0.0" — wszystkie powyższe liczniki gniazda oraz nowe liczniki wydajności obsługiwane w .NET Framework wersji 4 i nowszych. Te nowe liczniki zawierają informacje o wydajności dotyczące <xref:System.Net.HttpWebRequest> obiektów.  
  
 Aby uzyskać więcej informacji na temat uzyskiwania dostępu do liczników wydajności i zarządzania nimi w aplikacji, zobacz [liczniki wydajności](performance-counters.md).  
    
## <a name="security-performance-counters"></a>Liczniki wydajności zabezpieczeń  
 Kategoria zabezpieczeń programu .NET CLR konsoli wydajności zawiera liczniki, które dostarczają informacji o sprawdzaniu zabezpieczeń wykonywanych przez środowisko uruchomieniowe języka wspólnego dla aplikacji. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Liczba sprawdzeń w czasie konsolidacji**|Przedstawia łączną liczbę sprawdzeń zabezpieczeń dostępu kodu w ramach połączenia od momentu uruchomienia aplikacji. Sprawdzanie zabezpieczeń dostępu kodu w czasie konsolidacji jest wykonywane, gdy obiekt wywołujący wymaga określonego uprawnienia w czasie kompilacji just-in-Time (JIT). Sprawdzanie czasu konsolidacji jest wykonywane raz dla każdego obiektu wywołującego. Ta liczba nie jest przejawem poważnych problemów z wydajnością; jest to jedynie wskaźnik aktywności systemu zabezpieczeń.|  
|**Czas trwania sprawdzania RT**|Przedstawia wartość procentową czasu trwania sprawdzania zabezpieczeń dostępu kodu w czasie wykonywania od ostatniego przykładu. Ten licznik jest aktualizowany na końcu .NET Framework sprawdzanie zabezpieczeń. Nie jest to średnia; reprezentuje ostatnią obserwowana wartość.|  
|**% Czasu uwierzytelniania SIG**|Zarezerwowane do użytku w przyszłości.|  
|**Głębokość przechodzenia stosu**|Wyświetla głębokość stosu podczas ostatniego sprawdzenia zabezpieczeń dostępu kodu w czasie wykonywania. Sprawdzanie zabezpieczeń dostępu kodu w czasie wykonywania odbywa się przez przechodzenie stosu. Ten licznik nie jest średnią; zostanie wyświetlona tylko Ostatnia obserwowana wartość.|  
|**Łączna liczba sprawdzeń środowiska uruchomieniowego**|Przedstawia łączną liczbę testów zabezpieczeń dostępu kodu w czasie wykonywania wykonanych od chwili uruchomienia aplikacji. Sprawdzanie zabezpieczeń dostępu kodu środowiska uruchomieniowego jest wykonywane, gdy wywołujący żąda określonego uprawnienia. Sprawdzanie środowiska uruchomieniowego jest wykonywane dla każdego wywołania przez obiekt wywołujący i sprawdza bieżący stos wątków obiektu wywołującego. Gdy jest używany z licznikiem głębokości przeszukiwania **stosu** , ten licznik wskazuje na spadek wydajności, który występuje w przypadku kontroli zabezpieczeń.|  
  
## <a name="see-also"></a>Zobacz także

- [Liczniki wydajności](performance-counters.md)
- [Profilowanie środowiska uruchomieniowego](runtime-profiling.md)
