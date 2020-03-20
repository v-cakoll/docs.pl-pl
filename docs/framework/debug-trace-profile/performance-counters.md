---
title: Liczniki wydajności w oprogramowaniu .NET Framework
ms.date: 03/30/2017
helpviewer_keywords:
- performance, .NET Framework applications
- performance counters
- performance monitoring, counters
ms.assetid: 06a4ae8c-eeb2-4d5a-817e-b1b95c0653e1
ms.openlocfilehash: 44a5d1cb70d294d720290a4754bb5f5cb47f79a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400023"
---
# <a name="performance-counters-in-the-net-framework"></a>Liczniki wydajności w platformie .NET Framework

W tym temacie znajduje się lista liczników wydajności, które można znaleźć w [Monitorze wydajności systemu Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc749249%28v=ws.11%29).  

## <a name="exception-performance-counters"></a>Liczniki wydajności wyjątków  
 Kategoria Wyjątki clr konsoli wydajności .NET zawiera liczniki, które zawierają informacje o wyjątkach zgłaszanych przez aplikację. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**# Exceps rzucony**|Wyświetla całkowitą liczbę wyjątków zgłoszonych od momentu rozpoczęcia aplikacji. Obejmuje to zarówno wyjątki .NET, jak i niezarządzane wyjątki, które są konwertowane na wyjątki .NET. Na przykład HRESULT zwrócony z kodu niezarządzanego jest konwertowany na wyjątek w kodzie zarządzanym.<br /><br /> Ten licznik zawiera zarówno obsługiwane, jak i nieobsługiwały wyjątki. Wyjątki, które są rethrown są liczone ponownie.|  
|**# Exceps Rzucony / S**|Wyświetla liczbę wyjątków zgłaszanych na sekundę. Obejmuje to zarówno wyjątki .NET, jak i niezarządzane wyjątki, które są konwertowane na wyjątki .NET. Na przykład HRESULT zwrócony z kodu niezarządzanego jest konwertowany na wyjątek w kodzie zarządzanym.<br /><br /> Ten licznik zawiera zarówno obsługiwane, jak i nieobsługiwały wyjątki. Nie jest to średnia w czasie; wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzielonymi przez czas trwania interwału próbkowania. Ten licznik jest wskaźnikiem potencjalnych problemów z wydajnością, jeśli zostanie podrzucona duża (>100s) liczba wyjątków.|  
|**Liczba filtrów / s**|Wyświetla liczbę filtrów wyjątków .NET wykonywanych na sekundę. Filtr wyjątków ocenia niezależnie od tego, czy wyjątek jest obsługiwany.<br /><br /> Ten licznik nie jest średnią w czasie; wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzielonymi przez czas trwania interwału próbkowania.|  
|**Liczba wreszcie / s**|Wyświetla liczbę bloków finally wykonywanych na sekundę. Finally bloku jest gwarantowane do wykonania niezależnie od tego, jak blok try został zakończony.  Tylko finally bloków wykonywanych dla wyjątku są liczone; finally bloki na normalnych ścieżek kodu nie są liczone przez ten licznik.<br /><br /> Ten licznik nie jest średnią w czasie; wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzielonymi przez czas trwania interwału próbkowania.|  
|**Rzucać do catch głębokość / s**|Wyświetla liczbę klatek stosu przemkniętych, z ramki, która rzuciła wyjątek do ramki, która obsługiwała wyjątek, na sekundę. Ten licznik resetuje się do zera po wprowadzeniu obsługi wyjątków, więc zagnieżdżone wyjątki pokazują głębokość stosu programu handler-to-handler.<br /><br /> Ten licznik nie jest średnią w czasie; wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzielonymi przez czas trwania interwału próbkowania.|  

## <a name="interop-performance-counters"></a>Liczniki wydajności interop  
 Kategoria Net CLR Interop konsoli wydajności zawiera liczniki, które zawierają informacje o interakcji aplikacji ze składnikami COM, usługami COM+ i bibliotekami typów zewnętrznych. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Liczba ccws**|Wyświetla bieżącą liczbę opakowań wywoływanych COM (CCWs). CCW jest serwerem proxy dla obiektu zarządzanego, do którego odwołuje się niezarządzany klient COM. Ten licznik wskazuje liczbę obiektów zarządzanych, do których odwołuje się niezarządzany kod COM.|  
|**Liczba marszałków**|Wyświetla całkowitą liczbę argumentów i zwracane wartości zostały zorganizowane z kodu zarządzanego do niezarządzanego i odwrotnie, od momentu rozpoczęcia aplikacji. Ten licznik nie jest zwiększany, jeśli odcinki są inlined. (Wycinki są odpowiedzialne za kierowanie argumentów i zwracanie wartości). Wycinki są zwykle inlined, jeśli kierowanie napowietrznych jest mały.|  
|**Liczba wycinków**|Wyświetla bieżącą liczbę wycinków utworzonych przez środowisko uruchomieniowe języka wspólnego. Wycinki są odpowiedzialne za kierowanie argumentów i zwracanie wartości z kodu zarządzanego do niezarządzanego i odwrotnie, podczas wywołania współdziałania COM lub wywołania wywołania platformy.|  
|**Liczba eksportów TLB /s**|Zarezerwowane do użytku w przyszłości.|  
|**Liczba importów TLB /s**|Zarezerwowane do użytku w przyszłości.|  

## <a name="jit-performance-counters"></a>liczniki wydajności JIT  
 Kategoria konsoli wydajności .NET CLR JIT zawiera liczniki, które zawierają informacje o kodzie, który został skompilowany przez JIT. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Liczba IL Bytes JITted**|Wyświetla całkowitą liczbę bajtów języka pośredniego firmy Microsoft (MSIL) skompilowanych przez kompilator just-in-time (JIT) od momentu rozpoczęcia aplikacji. Ten licznik jest odpowiednikiem **licznika Całkowita liczba IL Bytes Jitted.**|  
|**Liczba metod JITted**|Wyświetla całkowitą liczbę metod Skompilowanych przez JIT od momentu rozpoczęcia aplikacji. Ten licznik nie obejmuje metod wstępnie skompilowanych przez JIT.|  
|**% czasu w Jit**|Wyświetla procent czasu spędzonego w kompilacji JIT od ostatniej fazy kompilacji JIT. Ten licznik jest aktualizowany na końcu każdej fazy kompilacji JIT. Faza kompilacji JIT występuje, gdy metoda i jej zależności są kompilowane.|  
|**IL Bajty Jitted / s**|Wyświetla liczbę bajtów MSIL, które są kompilowane JIT na sekundę. Ten licznik nie jest średnią w czasie; wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzielonymi przez czas trwania interwału próbkowania.|  
|**Standardowe błędy Jit**|Wyświetla maksymalną liczbę metod kompilatora JIT nie można skompilować od momentu rozpoczęcia aplikacji. Ten błąd może wystąpić, jeśli nie można zweryfikować MSIL lub jeśli występuje błąd wewnętrzny w kompilatorze JIT.|  
|**Całkowita liczba IL Bytes Jitted**|Wyświetla całkowitą liczbę bajtów MSIL JIT skompilowany od momentu rozpoczęcia aplikacji. Ten licznik jest odpowiednikiem **# IL Bytes Jitted** licznika.|  

## <a name="loading-performance-counters"></a>Załadunku liczniki wydajności  
 Kategoria ładowania konsoli wydajności .NET CLR zawiera liczniki, które zawierają informacje o zestawach, klasach i domenach aplikacji, które są ładowane. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**% wczytywania czasu**|Zarezerwowane do użytku w przyszłości.|  
|**Długość wyszukiwania zestawu**|Zarezerwowane do użytku w przyszłości.|  
|**Bajty w stercie ładowarki**|Wyświetla bieżący rozmiar (w bajtach) pamięci zatwierdzonej przez moduł ładujący klas we wszystkich domenach aplikacji. Pamięć zatwierdzona to miejsce fizyczne zarezerwowane w pliku stronicowania dysku.|  
|**Aktualne appdomains**|Wyświetla bieżącą liczbę domen aplikacji załadowanych w tej aplikacji.|  
|**Bieżące złożenia**|Wyświetla bieżącą liczbę zestawów załadowanych we wszystkich domenach aplikacji w aktualnie uruchomionej aplikacji. Jeśli zestaw jest ładowany jako adres neutralny dla domeny z wielu domen aplikacji, ten licznik jest zwiększany tylko raz.|  
|**Bieżące załadowane klasy**|Wyświetla bieżącą liczbę klas załadowanych we wszystkich złożeniach.|  
|**Wskaźnik appdomen**|Wyświetla liczbę domen aplikacji załadowanych na sekundę. Ten licznik nie jest średnią w czasie; wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzielonymi przez czas trwania interwału próbkowania.|  
|**Szybkość rozładowywanych appdomen**|Wyświetla liczbę domen aplikacji zwolnionych na sekundę. Ten licznik nie jest średnią w czasie; wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzielonymi przez czas trwania interwału próbkowania.|  
|**Liczba zgromadzeń**|Wyświetla liczbę zestawów załadowanych na sekundę we wszystkich domenach aplikacji. Jeśli zestaw jest ładowany jako adres neutralny dla domeny z wielu domen aplikacji, ten licznik jest zwiększany tylko raz.<br /><br /> Ten licznik nie jest średnią w czasie; wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzielonymi przez czas trwania interwału próbkowania.|  
|**Szybkość załadowanych klas**|Wyświetla liczbę klas załadowanych na sekundę we wszystkich złożeniach. Ten licznik nie jest średnią w czasie; wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzielonymi przez czas trwania interwału próbkowania.|  
|**Częstotliwość awarii obciążenia**|Wyświetla liczbę klas, których załadowano na sekundę. Ten licznik nie jest średnią w czasie; wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzielonymi przez czas trwania interwału próbkowania.<br /><br /> Błędy obciążenia mogą wystąpić z wielu powodów, takich jak nieodpowiednie zabezpieczenia lub nieprawidłowy format. Aby uzyskać szczegółowe informacje, zobacz Pomoc usług profilowania.|  
|**Całkowita liczba błędów obciążenia**|Wyświetla szczytową liczbę klas, których załadowano od momentu rozpoczęcia aplikacji.<br /><br /> Błędy obciążenia mogą wystąpić z wielu powodów, takich jak nieodpowiednie zabezpieczenia lub nieprawidłowy format. Aby uzyskać szczegółowe informacje, zobacz Pomoc usług profilowania.|  
|**Całkowita Appdomains**|Wyświetla szczytową liczbę domen aplikacji załadowanych od momentu rozpoczęcia aplikacji.|  
|**Całkowita liczba rozładowanych appdoains**|Wyświetla całkowitą liczbę domen aplikacji zwolnionych od momentu rozpoczęcia aplikacji. Jeśli domena aplikacji jest ładowana i zwalniana wiele razy, ten licznik zwiększa się za każdym razem, gdy domena aplikacji jest zwalniana.|  
|**Suma zgromadzeń**|Wyświetla całkowitą liczbę zestawów załadowanych od momentu rozpoczęcia aplikacji. Jeśli zestaw jest ładowany jako adres neutralny dla domeny z wielu domen aplikacji, ten licznik jest zwiększany tylko raz.|  
|**Łączna liczba załadowanych klas**|Wyświetla skumulowaną liczbę klas załadowanych we wszystkich zestawach od momentu rozpoczęcia aplikacji.|  

## <a name="lock-and-thread-performance-counters"></a>Liczniki wydajności blokady i gwintów  
 Kategoria Net CLR LocksAndThreads konsoli wydajności zawiera liczniki, które zawierają informacje o zarządzanych blokad i wątków, których używa aplikacja. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Liczba bieżących wątków logicznych**|Wyświetla liczbę bieżących zarządzanych obiektów wątku w aplikacji. Ten licznik utrzymuje liczbę uruchomionych i zatrzymanych wątków. Ten licznik nie jest średnią w czasie; wyświetla tylko ostatnią zaobserwowaną wartość.|  
|**Liczba bieżących wątków fizycznych**|Wyświetla liczbę wątków natywnego systemu operacyjnego utworzonych i należących do środowiska wykonawczego języka wspólnego, aby działać jako podstawowe wątki dla zarządzanych obiektów wątku. Wartość tego licznika nie obejmuje wątków używanych przez środowisko wykonawcze w jego wewnętrznych operacjach; jest to podzbiór wątków w procesie systemu operacyjnego.|  
|**Liczba bieżących rozpoznawanych wątków**|Wyświetla liczbę wątków, które są obecnie rozpoznawane przez środowisko wykonawcze. Te wątki są skojarzone z odpowiednim obiektem wątku zarządzanego. Środowisko wykonawcze nie tworzy tych wątków, ale mają one uruchomić wewnątrz środowiska wykonawczego co najmniej raz.<br /><br /> Śledzone są tylko unikatowe wątki; wątki o tym samym identyfikatorze wątku, które ponownie wejdą do środowiska wykonawczego lub są odtworzone po zamknięciu wątku nie są liczone dwa razy.|  
|**Liczba całkowitej liczby rozpoznanych wątków**|Wyświetla całkowitą liczbę wątków, które zostały rozpoznane przez środowisko wykonawcze od momentu uruchomienia aplikacji. Te wątki są skojarzone z odpowiednim obiektem wątku zarządzanego. Środowisko wykonawcze nie tworzy tych wątków, ale mają one uruchomić wewnątrz środowiska wykonawczego co najmniej raz.<br /><br /> Śledzone są tylko unikatowe wątki; wątki o tym samym identyfikatorze wątku, które ponownie wejdą do środowiska wykonawczego lub są odtworzone po zamknięciu wątku nie są liczone dwa razy.|  
|**Współczynnik rywalizacji / s**|Wyświetla szybkość, z jaką wątki w czasie wykonywania próbują uzyskać blokadę zarządzaną bezskutecznie.|  
|**Bieżąca długość kolejki**|Wyświetla całkowitą liczbę wątków, które obecnie oczekują na uzyskanie blokady zarządzanej w aplikacji. Ten licznik nie jest średnią w czasie; wyświetla ostatnią zaobserwowaną wartość.|  
|**Długość kolejki /s**|Wyświetla liczbę wątków na sekundę, które oczekują na uzyskanie blokady w aplikacji. Ten licznik nie jest średnią w czasie; wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzielonymi przez czas trwania interwału próbkowania.|  
|**Szczyt długości kolejki**|Wyświetla całkowitą liczbę wątków, które czekały na uzyskanie blokady zarządzanej od momentu rozpoczęcia aplikacji.|  
|**szybkość rozpoznawanych wątków /s**|Wyświetla liczbę wątków na sekundę, które zostały rozpoznane przez środowisko wykonawcze. Te wątki są skojarzone z odpowiednim obiektem wątku zarządzanego. Środowisko wykonawcze nie tworzy tych wątków, ale mają one uruchomić wewnątrz środowiska wykonawczego co najmniej raz.<br /><br /> Śledzone są tylko unikatowe wątki; wątki o tym samym identyfikatorze wątku, które ponownie wejdą do środowiska wykonawczego lub są odtworzone po zamknięciu wątku nie są liczone dwa razy.<br /><br /> Ten licznik nie jest średnią w czasie; wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzielonymi przez czas trwania interwału próbkowania.|  
|**Całkowita liczba rywalizacji**|Wyświetla całkowitą liczbę razy, że wątki w czasie wykonywania próbował uzyskać blokadę zarządzaną bezskutecznie.|  

## <a name="memory-performance-counters"></a>Liczniki wydajności pamięci  
 Kategoria pamięci CLR konsoli wydajności zawiera liczniki, które zawierają informacje o modułu zbierającego elementy bezużyteczne. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**# Bajty we wszystkich heaps**|Wyświetla sumę liczników **sterty gen 1,** **gen 2 i**duży **rozmiar sterty obiektu.** Ten licznik wskazuje bieżącą pamięć przydzieloną w bajtach na sterty wyrzucania elementów bezużytecznych.|  
|**# Uchwyty GC**|Wyświetla bieżącą liczbę używanych dojść do wyrzucania elementów bezużytecznych. Dojścia dobierania elementów bezużytecznych są dojścia do zasobów zewnętrznych do środowiska uruchomieniowego języka wspólnego i środowiska zarządzanego.|  
|**# Gen 0 Kolekcje**|Wyświetla liczbę razy generacji 0 obiektów (czyli najmłodsze, ostatnio przydzielone obiekty) są śmieci zebrane od momentu rozpoczęcia aplikacji.<br /><br /> Wyrzucanie elementów bezużytecznych generacji 0 występuje, gdy dostępna pamięć w generacji 0 nie jest wystarczająca do spełnienia żądania alokacji. Ten licznik jest zwiększany na końcu generacji 0 wyrzucania elementów bezużytecznych. Kolekcje modułów wyższej generacji obejmują wszystkie kolekcje niższej generacji. Ten licznik jest jawnie zwiększany, gdy występuje zbieranie elementów bezużytecznych wyższej generacji (generacja 1 lub 2).<br /><br /> Ten licznik wyświetla ostatnią zaobserwowaną wartość. Wartość licznika **_Global\_ ** nie jest dokładna i powinna zostać zignorowana.|  
|**# Gen 1 Kolekcje**|Wyświetla liczbę razy generacji 1 obiekty są śmieci zebrane od momentu rozpoczęcia aplikacji.<br /><br /> Licznik jest zwiększany na końcu generacji 1 wyrzucania elementów bezużytecznych. Kolekcje modułów wyższej generacji obejmują wszystkie kolekcje niższej generacji. Ten licznik jest jawnie zwiększany, gdy występuje zbieranie elementów bezużytecznych wyższej generacji (generacji 2).<br /><br /> Ten licznik wyświetla ostatnią zaobserwowaną wartość. Wartość licznika **_Global\_ ** nie jest dokładna i powinna zostać zignorowana.|  
|**# Gen 2 Kolekcje**|Wyświetla liczbę razy generacji 2 obiekty są śmieci zebrane od momentu rozpoczęcia aplikacji. Licznik jest zwiększany na końcu generacji 2 wyrzucania elementów bezużytecznych (nazywany również pełne wyrzucanie elementów bezużytecznych).<br /><br /> Ten licznik wyświetla ostatnią zaobserwowaną wartość. Wartość licznika **_Global\_ ** nie jest dokładna i powinna zostać zignorowana.|  
|**# Wywołane GC**|Wyświetla szczytową liczbę wykonań wyrzucania elementów <xref:System.GC.Collect%2A?displayProperty=nameWithType>bezużytecznych z powodu jawnego wywołania . Jest dobrą praktyką, aby umożliwić moduł zbierający elementy bezużyteczne dostroić częstotliwość jego kolekcji.|  
|**Liczba przypiętych obiektów**|Wyświetla liczbę przypiętych obiektów napotkanych w ostatnim wyrzucaniu elementów bezużytecznych. Przypięty obiekt jest obiektem, który moduł zbierający elementy bezużyteczne nie może przenieść w pamięci. Ten licznik śledzi przypięte obiekty tylko w sterty, które są zbierane śmieci. Na przykład wyrzucania elementów bezużytecznych generacji 0 powoduje wyliczenie przypiętych obiektów tylko w stercie generacji 0.|  
|**Liczba używanych bloków zlewozmywakowych**|Wyświetla bieżącą liczbę używanych bloków synchronizacji. Bloki synchronizacji są strukturami danych dla obiektu przydzielonymi do przechowywania informacji o synchronizacji. Posiadają one słabe odwołania do obiektów zarządzanych i muszą być skanowane przez moduł zbierający elementy bezużyteczne. Bloki synchronizacji nie są ograniczone do przechowywania informacji o synchronizacji; mogą również przechowywać metadane międzyoperacyjne COM. Ten licznik wskazuje problemy z wydajnością z intensywnym użyciem ćwitrów synchronizacji.|  
|**# Całkowita liczba zatwierdzonych bajtów**|Wyświetla ilość pamięci wirtualnej w bajtach, obecnie zatwierdzona przez moduł zbierający elementy bezużyteczne. Pamięć zatwierdzona jest pamięcią fizyczną, dla której miejsce zostało zarezerwowane w pliku stronicowania dysku.|  
|**# Całkowita zarezerwowana bajty**|Wyświetla ilość pamięci wirtualnej w bajtach, obecnie zarezerwowane przez moduł zbierający elementy bezużyteczne. Pamięć zarezerwowana to miejsce pamięci wirtualnej zarezerwowane dla aplikacji, gdy nie użyto żadnych stron dysku lub pamięci głównej.|  
|**% czasu w GC**|Wyświetla procent czasu, który upłynął na wykonywanie wyrzucania elementów bezużytecznych od ostatniego cyklu wyrzucania elementów bezużytecznych. Ten licznik zwykle wskazuje pracę wykonaną przez moduł zbierający elementy bezużyteczne do zbierania i kompaktowy pamięci w imieniu aplikacji. Ten licznik jest aktualizowany tylko na końcu każdego wyrzucania elementów bezużytecznych. Ten licznik nie jest średnią; jego wartość odzwierciedla ostatnią zaobserwowaną wartość.|  
|**Przydzielone bajty na sekundę**|Wyświetla liczbę bajtów na sekundę przydzielonych na stercie wyrzucania elementów bezużytecznych. Ten licznik jest aktualizowany na końcu każdego wyrzucania elementów bezużytecznych, a nie w każdej alokacji. Ten licznik nie jest średnią w czasie; wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzielonymi przez czas trwania interwału próbkowania.|  
|**Finalizacja Ocalałych**|Wyświetla liczbę elementów zebranych elementów bezużytecznych, które przetrwać kolekcji, ponieważ oczekują na sfinalizowanie. Jeśli te obiekty posiadają odwołania do innych obiektów, te obiekty również przetrwać, ale nie są liczone przez ten licznik. **Promowane finalizacji pamięci z gen 0** licznik reprezentuje całą pamięć, która przetrwała z powodu finalizacji.<br /><br /> Ten licznik nie kumuluje się; jest aktualizowany na końcu każdego wyrzucania elementów bezużytecznych z liczbą ocalałych podczas tej konkretnej kolekcji tylko. Ten licznik wskazuje dodatkowe obciążenie, które aplikacja może ponieść z powodu finalizacji.|  
|**Rozmiar sterty Gen 0**|Wyświetla maksymalną liczbę bajtów, które można przydzielić w generacji 0; nie wskazuje bieżącej liczby bajtów przydzielonych w generacji 0.<br /><br /> Generacji 0 wyrzucania elementów bezużytecznych występuje, gdy alokacje od ostatniej kolekcji przekracza ten rozmiar. Rozmiar generacji 0 jest dostrojony przez moduł zbierający elementy bezużyteczne i może ulec zmianie podczas wykonywania aplikacji. Na końcu kolekcji generacji 0 rozmiar sterty generacji 0 wynosi 0 bajtów. Ten licznik wyświetla rozmiar w bajtach alokacji, która wywołuje następnej generacji 0 wyrzucania elementów bezużytecznych.<br /><br /> Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, a nie w każdej alokacji.|  
|**Gen 0 Promowane bajty/s**|Wyświetla bajty na sekundę, które są promowane z generacji 0 do generacji 1. Pamięć jest promowana, gdy przetrwa wyrzucania elementów bezużytecznych. Ten licznik jest wskaźnikiem stosunkowo długowiecznych obiektów tworzonych na sekundę.<br /><br /> Ten licznik wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzielonymi przez czas trwania interwału próbkowania.|  
|**Rozmiar sterty Gen 1**|Wyświetla bieżącą liczbę bajtów w generacji 1; licznik ten nie wyświetla maksymalnego rozmiaru generacji 1. Obiekty nie są bezpośrednio przydzielane w tej generacji; są one promowane z poprzedniej generacji 0 wyrzucania elementów bezużytecznych. Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, a nie w każdej alokacji.|  
|**Gen 1 promowane bajty/s**|Wyświetla bajty na sekundę, które są promowane z generacji 1 do generacji 2. Obiekty, które są promowane tylko dlatego, że oczekują na sfinalizowanie nie są uwzględnione w tym liczniku.<br /><br /> Pamięć jest promowana, gdy przetrwa wyrzucania elementów bezużytecznych. Nic nie jest promowane od generacji 2, ponieważ jest to najstarsze pokolenie. Ten licznik jest wskaźnikiem bardzo długowiecznych obiektów tworzonych na sekundę.<br /><br /> Ten licznik wyświetla różnicę między wartościami obserwowanymi w ostatnich dwóch próbkach podzielonymi przez czas trwania interwału próbkowania.|  
|**Rozmiar sterty Gen 2**|Wyświetla bieżącą liczbę bajtów w generacji 2. Obiekty nie są bezpośrednio przydzielane w tej generacji; są one promowane z generacji 1 podczas poprzedniej generacji 1 wyrzucania elementów bezużytecznych. Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, a nie w każdej alokacji.|  
|**Rozmiar sterty dużego obiektu**|Wyświetla bieżący rozmiar w bajtach sterty dużego obiektu. Obiekty, które są większe niż około 85 000 bajtów są traktowane jako duże obiekty przez moduł zbierający elementy bezużyteczne i są bezpośrednio przydzielane w specjalnej stercie. Nie są one promowane przez pokolenia. Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, a nie w każdej alokacji.|  
|**Identyfikator procesu**|Wyświetla identyfikator procesu monitorowanego wystąpienia procesu CLR.|  
|**Promowana finalizacja pamięci z gen 0**|Wyświetla bajty pamięci, które są promowane z generacji 0 do generacji 1 tylko dlatego, że oczekują na sfinalizowanie. Ten licznik nie kumuluje się; wyświetla wartość obserwowaną na końcu ostatniego wyrzucania elementów bezużytecznych.|  
|**Promowana pamięć z gen 0**|Wyświetla bajty pamięci, które przetrwać wyrzucania elementów bezużytecznych i są promowane z generacji 0 do generacji 1. Obiekty, które są promowane tylko dlatego, że oczekują na sfinalizowanie nie są uwzględnione w tym liczniku. Ten licznik nie kumuluje się; wyświetla wartość obserwowaną na końcu ostatniego wyrzucania elementów bezużytecznych.|  
|**Promowana pamięć z gen 1**|Wyświetla bajty pamięci, które przetrwać wyrzucania elementów bezużytecznych i są promowane z generacji 1 do generacji 2. Obiekty, które są promowane tylko dlatego, że oczekują na sfinalizowanie nie są uwzględnione w tym liczniku. Ten licznik nie kumuluje się; wyświetla wartość obserwowaną na końcu ostatniego wyrzucania elementów bezużytecznych. Ten licznik jest resetowany do 0, jeśli ostatni wyrzucania elementów bezużytecznych był tylko kolekcji generacji 0.|  

## <a name="networking-performance-counters"></a>Liczniki wydajności sieci  

Kategoria Net CLR Networking konsoli Wydajności zawiera liczniki, które zawierają informacje o danych wysyłanych i odbieranych przez aplikację za pośrednictwem sieci. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Bajty odebrane**|Skumulowana całkowita liczba bajtów <xref:System.Net.Sockets.Socket> odebranych <xref:System.AppDomain> przez wszystkie obiekty w obrębie od momentu rozpoczęcia procesu. Numer ten zawiera dane i wszelkie informacje o protokole, które nie są zdefiniowane przez protokół TCP/IP.|  
|**Bajty wysłane**|Skumulowana liczba bajtów <xref:System.Net.Sockets.Socket> wysyłanych <xref:System.AppDomain> przez wszystkie obiekty w obrębie od momentu rozpoczęcia procesu. Numer ten zawiera dane i wszelkie informacje o protokole, które nie są zdefiniowane przez protokół TCP/IP.|  
|**Połączenia ustanowione**|Łączna całkowita liczba <xref:System.Net.Sockets.Socket> obiektów dla gniazd strumienia, <xref:System.AppDomain> które kiedykolwiek były połączone w ramach od rozpoczęcia procesu.|  
|**Odebrane datagramy**|Łączna łączna liczba pakietów datagramu <xref:System.Net.Sockets.Socket> odebranych <xref:System.AppDomain> przez wszystkie obiekty w ramach procesu rozpoczętego.|  
|**Wysłane datagramy**|Łączna łączna liczba pakietów datagramu <xref:System.Net.Sockets.Socket> wysyłanych <xref:System.AppDomain> przez wszystkie obiekty w ramach procesu.|  
|**Średnia żywotność httpWebRequest**|Średni czas do zakończenia <xref:System.Net.HttpWebRequest> dla wszystkich obiektów, które <xref:System.AppDomain> zakończyły się w ostatnim interwale w ciągu od rozpoczęcia procesu.|  
|**HttpWebRequest średni czas kolejki**|Średni czas w kolejce <xref:System.Net.HttpWebRequest> dla wszystkich obiektów, które opuściły <xref:System.AppDomain> kolejkę w ostatnim interwale w ciągu od rozpoczęcia procesu.|  
|**Utworzone httpWebRequests/s**|Liczba obiektów <xref:System.Net.HttpWebRequest> utworzonych na <xref:System.AppDomain>sekundę w pliku .|  
|**HttpWebRequests w kolejce/s**|Liczba <xref:System.Net.HttpWebRequest> obiektów, które zostały dodane do kolejki <xref:System.AppDomain>na sekundę w programie .|  
|**HttpWebRequests przerwane/s**|Liczba obiektów, <xref:System.Net.HttpWebRequest> w których <xref:System.Net.HttpWebRequest.Abort%2A> aplikacja wywoływała <xref:System.AppDomain>metodę na sekundę w obrębie .|  
|**HttpWebRequests nie powiodło się/s**|Liczba <xref:System.Net.HttpWebRequest> obiektów, które otrzymały nieudany kod stanu z <xref:System.AppDomain>serwera na sekundę w programie .|  
  
 Obsługiwanych jest kilka klas liczników wydajności sieci:  
  
- Liczniki zdarzeń, które mierzą liczbę zdarzeń.  
  
- Liczniki danych, które mierzą ilość wysyłanych lub odbieranych danych.  
  
- Liczniki czasu trwania, które mierzą, jak długo różne procesy trwać. Czasy są mierzone na obiektach każdego interwału (zwykle w sekundach) po ich wyjęcie z różnych stanów.  
  
- Liczniki na interwał, które mierzą liczbę obiektów, które robią określone przejście na interwał (zwykle na sekundę).  
  
Liczniki wydajności sieci dla zdarzeń są następujące:  
  
- **Połączenia ustanowione**  
  
- **Odebrane datagramy**  
  
- **Wysłane datagramy**  
  
 Te liczniki wydajności zapewniają liczbę od momentu rozpoczęcia procesu. Liczba <xref:System.Net.Sockets.Socket> nawiązanych połączeń obejmuje <xref:System.Net.Sockets.Socket> jawne wywołanie metody przez aplikację dla ustanowionego połączenia gniazda strumienia, <xref:System.Net.FtpWebRequest> <xref:System.Net.WebClient>a także wewnętrzne wywołania przez inne klasy (<xref:System.Net.HttpWebRequest>, , , i <xref:System.Net.Sockets.TcpClient>, na przykład) do <xref:System.Net.Sockets.Socket> klasy  
  
 Liczba **odebranych datagramów** i **wysłanych datagramów** obejmuje pakiety <xref:System.Net.Sockets.Socket> datagramów wysyłane lub odbierane przy użyciu<xref:System.Net.Sockets.UdpClient>jawnych wywołań metod przez aplikację, a także wewnętrzne wywołania przez inne klasy ( , na przykład) do <xref:System.Net.Sockets.Socket>. Klasa. Liczba **danych otrzymanych** i **wysłanych datagramów** może być również używana do zapewnienia bardzo surowej miary liczby bajtów wysłanych lub odebranych przy użyciu datagramów przy założeniu średniego rozmiaru dla datagramu.  
  
 Liczniki wydajności sieci dla danych są następujące:  
  
- **Bajty odebrane**  
  
- **Bajty wysłane**  
  
 Powyższe liczniki zapewniają liczbę bajtów od momentu rozpoczęcia procesu.  
  
 Istnieją dwa liczniki czasu trwania, które <xref:System.Net.HttpWebRequest> mierzą, jak długo zajęło obiektom przejście przez cały ich cykl życia lub tylko jego część:  
  
- **Średnia żywotność httpWebRequest**  
  
- **HttpWebRequest średni czas kolejki**  
  
 Dla **licznika HttpWebRequest średni okres istnienia,** okres istnienia większości <xref:System.Net.HttpWebRequest> obiektów zawsze rozpoczyna się od czasu, że obiekt jest tworzony do czasu, że strumień odpowiedzi jest zamknięty przez aplikację. Istnieją dwa niezbyt częste przypadki:  
  
- Jeśli aplikacja nigdy <xref:System.Net.HttpWebRequest.GetResponse%2A> nie <xref:System.Net.HttpWebRequest.BeginGetResponse%2A> wywołuje lub metody, <xref:System.Net.HttpWebRequest> a następnie okres istnienia obiektu jest ignorowany.  
  
- Jeśli <xref:System.Net.HttpWebRequest> obiekt zgłasza <xref:System.Net.WebException> podczas <xref:System.Net.HttpWebRequest.GetResponse%2A> wywoływania <xref:System.Net.HttpWebRequest.EndGetResponse%2A> lub metody, okres istnienia kończy się, gdy wyjątek. Technicznie podstawowy strumień odpowiedzi jest również zamknięty w tym momencie (strumień odpowiedzi zwrócony użytkownikowi jest naprawdę strumień pamięci zawierający kopię strumienia odpowiedzi).  
  
 Istnieją cztery liczniki, <xref:System.Net.HttpWebRequest> które śledzą pewne problemy z obiektami na interwał. Te liczniki wydajności mogą pomóc deweloperom aplikacji, administratorom <xref:System.Net.HttpWebRequest> i pracownikom pomocy technicznej lepiej zrozumieć, co robią obiekty. Liczniki są następujące:  
  
- **Utworzone httpWebRequests/s**  
  
- **HttpWebRequests w kolejce/s**  
  
- **HttpWebRequests przerwane/s**  
  
- **HttpWebRequests nie powiodło się/s**  
  
 Dla **httpWebRequests Aborted/sec** licznika, <xref:System.Net.HttpWebRequest.Abort%2A> wewnętrzne wywołania są również liczone. Te wywołania wewnętrzne są zwykle spowodowane przez limity czasu, które aplikacja może chcieć zmierzyć.  
  
 Licznik **HttpWebRequests failed/sec** zawiera <xref:System.Net.HttpWebRequest> liczbę obiektów, które otrzymały kod stanu, który nie powiódł się z serwera na sekundę. Oznacza to, że kod stanu odebrany z serwera Http na końcu żądania nie był w zakresie od 200 do 299. Kody stanu, które są obsługiwane i spowodować nowe żądanie (wiele z 401 nieautoryzowane kody stanu, na przykład) zakończy się niepowodzeniem lub nie zakończy się niepowodzeniem na podstawie wyniku ponawiania. Jeśli aplikacja będzie zobaczyć błąd na podstawie ponowienia próby, a następnie ten licznik jest zwiększany.  
  
 Liczniki wydajności sieci można uzyskać dostęp <xref:System.Diagnostics.PerformanceCounter> i zarządzane przy <xref:System.Diagnostics> użyciu i powiązanych klas w obszarze nazw. Liczniki wydajności sieci można również wyświetlać za pomocą konsoli Monitor wydajności systemu Windows.  
  
 Liczniki wydajności sieci muszą być włączone w pliku konfiguracyjnym, który ma być używany. Wszystkie liczniki wydajności sieci są włączone lub wyłączone przy jednym ustawieniu w pliku konfiguracyjnym. Nie można włączyć ani wyłączyć indywidualnych liczników wydajności sieci. Aby uzyskać więcej informacji, zobacz [ \<performanceCounter> Element (Ustawienia sieciowe)](../configure-apps/file-schema/network/performancecounter-element-network-settings.md).  
  
 Jeśli liczniki sieciowe są włączone, spowoduje to utworzenie i zaktualizowanie zarówno liczników wydajności dla aplikacji, jak i globalnej wydajności. Jeśli ta opcja jest wyłączona, aplikacja nie dostarczy żadnych danych licznika wydajności sieci.  
  
 Liczniki wydajności są pogrupowane w kategorie. Aplikacja może wyświetlić listę wszystkich kategorii z następującym przykładowym kodem:  
  
```csharp
PerformanceCounterCategory[] Array = PerformanceCounterCategory.GetCategories();  
for (int i = 0; i < Array.Length; i++)  
{  
    Console.Out.WriteLine("{0}. Name={1} Help={2}", i, Array[i].CategoryName, Array[i].CategoryHelp);  
}  
```  
  
 Liczniki wydajności sieci są wymienione w dwóch kategoriach:  
  
- ".NET CLR Networking" - oryginalne liczniki wydajności wprowadzone w wersji 2 programu .NET Framework i obsługiwane w programie .NET Framework w wersji 2 i nowszej.  
  
- ".NET CLR Networking 4.0.0.0" - Wszystkie powyższe liczniki gniazd oraz nowe liczniki wydajności obsługiwane w programie .NET Framework w wersji 4 i nowszych. Te nowe liczniki zawierają <xref:System.Net.HttpWebRequest> informacje o wydajności obiektów.  
  
 Aby uzyskać więcej informacji na temat uzyskiwania dostępu do liczników wydajności i zarządzania nimi w aplikacji, zobacz [Liczniki wydajności](performance-counters.md).  

## <a name="security-performance-counters"></a>Liczniki wydajności zabezpieczeń  
 Kategoria zabezpieczeń programu .NET CLR w konsoli Wydajności zawiera liczniki, które zawierają informacje o kontrolach zabezpieczeń przeprowadzanych przez środowisko wykonawcze wspólnego języka dla aplikacji. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**# Kontrolki czasu łącza**|Wyświetla całkowitą liczbę kontroli zabezpieczeń dostępu do kodu w czasie łącza od momentu rozpoczęcia aplikacji. Sprawdzanie zabezpieczeń dostępu do kodu w czasie łącza są wykonywane, gdy wywołujący wymaga określonego uprawnienia w czasie kompilacji just-in-time (JIT). Sprawdzanie czasu łącza jest wykonywane raz na rozmówcę. Liczba ta nie wskazuje na poważne problemy z wydajnością; świadczy jedynie o działalności systemu bezpieczeństwa.|  
|**% czasu w kontrolach RT**|Wyświetla procent czasu, który upłynął na wykonywanie kontroli zabezpieczeń dostępu do kodu środowiska uruchomieniowego od ostatniego przykładu. Ten licznik jest aktualizowany na końcu kontroli zabezpieczeń programu .NET Framework. To nie jest średnia; reprezentuje ostatnią zaobserwowaną wartość.|  
|**% czasu Sig Uwierzytelnianie**|Zarezerwowane do użytku w przyszłości.|  
|**Głębokość chodzenia stosu**|Wyświetla głębokość stosu podczas tej ostatniej kontroli zabezpieczeń dostępu do kodu środowiska wykonawczego. Sprawdzanie zabezpieczeń dostępu do kodu środowiska uruchomieniowego są wykonywane przez przejście stosu. Ten licznik nie jest średnią; wyświetla tylko ostatnią zaobserwowaną wartość.|  
|**Sprawdzanie całkowitego czasu wykonywania**|Wyświetla całkowitą liczbę kontroli zabezpieczeń dostępu do kodu środowiska uruchomieniowego przeprowadzonych od momentu uruchomienia aplikacji. Sprawdzanie zabezpieczeń dostępu do kodu środowiska uruchomieniowego są wykonywane, gdy wywołujący wymaga określonego uprawnienia. Sprawdzanie środowiska uruchomieniowego jest dokonywane przy każdym wywołaniu przez wywołującego i sprawdza bieżący stos wątku wywołującego. W przypadku użycia z **licznika głębokość spaceru stosu,** ten licznik wskazuje karę wydajności, która występuje dla kontroli zabezpieczeń.|  
  
## <a name="see-also"></a>Zobacz też

- [Liczniki wydajności](performance-counters.md)
- [Profilowanie środowiska uruchomieniowego](runtime-profiling.md)
