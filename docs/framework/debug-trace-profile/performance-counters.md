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
ms.openlocfilehash: 4839513f28de0fd79de7a8dc5245d4d0a2fb1622
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123803"
---
# <a name="performance-counters-in-the-net-framework"></a>Liczniki wydajności w oprogramowaniu .NET Framework
Ten temat zawiera listę liczników wydajności można znaleźć w [Windows Performance Monitor](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc749249%28v=ws.11%29).  
  
-   [Liczniki wydajności wyjątków](#exception)  
  
-   [Liczniki wydajności międzyoperacyjności](#interop)  
  
-   [Liczniki wydajności JIT](#jit)  
  
-   [Ładowanie liczników wydajności](#loading)  
  
-   [Liczniki wydajności blokady i wątku](#lockthread)  
  
-   [Liczniki wydajności pamięci](#memory)  
  
-   [Liczniki wydajności funkcji sieciowych](#networking)  
  
-   [Liczniki wydajności zabezpieczeń](#security)  
  
<a name="exception"></a>   
## <a name="exception-performance-counters"></a>Liczniki wydajności wyjątków  
 Kategoria wydajności konsoli wyjątki .NET CLR zawiera liczniki, które zawierają informacje o wyjątki generowane przez aplikację. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Liczba wyjątków zgłoszony**|Wyświetla całkowitą liczbę wyjątków zgłaszanych od czasu uruchomienia aplikacji. Obejmuje to zarówno wyjątki .NET i niezarządzanymi wyjątkami przekonwertowanymi na wyjątki platformy .NET. Na przykład wartość HRESULT zwracane z niezarządzanego kodu jest konwertowana na wyjątek w kodzie zarządzanym.<br /><br /> Ten licznik obejmuje zarówno obsługiwanych i nieobsługiwanych wyjątków. Wyjątki, które jest zgłaszany ponownie są zliczane ponownie.|  
|**Liczba wyjątków / s**|Wyświetla liczbę wyjątków zgłaszanych na sekundę. Obejmuje to zarówno wyjątki .NET i niezarządzanymi wyjątkami przekonwertowanymi na wyjątki platformy .NET. Na przykład wartość HRESULT zwracane z niezarządzanego kodu jest konwertowana na wyjątek w kodzie zarządzanym.<br /><br /> Ten licznik obejmuje zarówno obsługiwanych i nieobsługiwanych wyjątków. Nie jest średnią wraz z upływem czasu; Wyświetla różnicy między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania. Ten licznik jest wskazuje potencjalne problemy z wydajnością, jeśli jest to duży (> 100s) liczba wyjątków są zgłaszane.|  
|**liczba filtrów / sekundę**|Wyświetla liczbę wykonanych w ciągu sekundy filtry wyjątków .NET. Oblicza filtra wyjątku niezależnie od tego, czy wyjątek jest obsługiwany.<br /><br /> Ten licznik nie jest średnią wraz z upływem czasu; Wyświetla różnicy między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Liczba Finallys / sekundę**|Wyświetla liczbę bloki finally wykonanych w ciągu sekundy. A na koniec bloku jest gwarantowane do wykonania, niezależnie od tego, jak został zakończony bloku try.  Tylko na koniec obliczane są bloki wykonywane dla wyjątku. na koniec bloki na ścieżkach normalne kodu przez ten licznik nie są uwzględniane.<br /><br /> Ten licznik nie jest średnią wraz z upływem czasu; Wyświetla różnicy między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Throw do przechwytywania głębokości / sekundę**|Wyświetla liczbę ramek stosu, przesunięta z ramki, który wygenerował wyjątek do ramki, obsługi wyjątków, na sekundę. Ten licznik powraca do zera po wprowadzeniu obsługi wyjątków, dlatego wyjątków zagnieżdżonych widoczne Głębokość stosu obsługi do obsługi.<br /><br /> Ten licznik nie jest średnią wraz z upływem czasu; Wyświetla różnicy między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
  
<a name="interop"></a>   
## <a name="interop-performance-counters"></a>Liczniki wydajności międzyoperacyjności  
 Kategoria wydajności konsoli .NET CLR Interop zawiera liczniki, które zawierają informacje o interakcji aplikacji z składników COM, usług COM + i zewnętrzne biblioteki typów. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Liczba otoki**|Wyświetla bieżącą liczbę wywoływanych otok COM (otoki). CCW jest serwer proxy dla obiektu zarządzanego, do którego nastąpiło odwołanie z niezarządzanego klienta COM. Ten licznik wskazuje liczbę zarządzanych obiektów, odwołuje się kod niezarządzany COM.|  
|**# marshalingu**|Wyświetla łączną liczbę razy argumentów i zwracanych wartości mają został przekazany z zarządzanego do kodu niezarządzanego i odwrotnie, od czasu uruchomienia aplikacji. Ten licznik nie jest zwiększana, gdy wycinki są śródwierszowych. (Wycinków odpowiadają za kierowanie argumentami i zwracane wartości). Wycinki kodu są zazwyczaj śródwierszowych, jeśli marshaling obciążenie jest mały.|  
|**Liczba wycinków**|Wyświetla bieżącą liczbę wycinków utworzone przez środowisko uruchomieniowe języka wspólnego. Wycinki kodu są odpowiedzialni za kierowanie argumentami i wartości zwracanych z kodu zarządzanego na niezarządzany i odwrotnie, podczas wywołania międzyoperacyjnego modelu COM lub platformy wywoływać wywołania.|  
|**Liczba eksportów TLB / sekundę**|Zarezerwowane do użytku w przyszłości.|  
|**Liczba Importy TLB / sekundę**|Zarezerwowane do użytku w przyszłości.|  
  
<a name="jit"></a>   
## <a name="jit-performance-counters"></a>liczniki wydajności JIT  
 Kategoria wydajności konsoli .NET CLR JIT zawiera liczniki, które zawierają informacje dotyczące kodu, który został skompilowany JIT. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Liczba bajtów IL w trybie JIT**|Wyświetla całkowitą liczbę bajtów intermediate language (MSIL) firmy Microsoft, skompilowane przez kompilator just-in-time (JIT) od czasu uruchomienia aplikacji. Ten licznik jest odpowiednikiem **łączna liczba bajtów IL w trybie JIT** licznika.|  
|**Liczba metod w trybie JIT**|Wyświetla łączną liczbę metod kompilowanego dokładnie na czas od momentu jej pracę. Ten licznik nie ma wstępnie kompilowany metody.|  
|**% Czasu w trybie Jit**|Przedstawia wartość procentową czasu przetwarzania w kompilacji JIT od czasu ostatniej fazie kompilacji JIT. Ten licznik jest aktualizowany na końcu każdej fazie kompilacji JIT. Fazy kompilacji JIT występuje, gdy metoda i jego zależności są kompilowane.|  
|**IL bajtów w trybie JIT / sekundę**|Wyświetla liczbę bajtów MSIL, które są kompilowanego dokładnie na czas na sekundę. Ten licznik nie jest średnią wraz z upływem czasu; Wyświetla różnicy między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Błędy standardowe Jit**|Wyświetla szczytowa liczba metody, które kompilator JIT ma kompilacja nie powiodła się od czasu uruchomienia aplikacji. Ten błąd może wystąpić, jeśli nie można zweryfikować kod języka MSIL lub jeśli wystąpił błąd wewnętrzny w kompilatorze JIT.|  
|**Łączna liczba bajtów IL w trybie JIT**|Wyświetla całkowitą liczbę bajtów MSIL kompilowanego dokładnie na czas od momentu jej pracę. Ten licznik jest odpowiednikiem **liczba bajtów IL w trybie JIT** licznika.|  
  
<a name="loading"></a>   
## <a name="loading-performance-counters"></a>Ładowanie liczników wydajności  
 Kategoria .NET CLR ładowania konsoli wydajności zawiera liczniki, które zawierają informacje dotyczące zestawów, klas i domen aplikacji, które są ładowane. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**% Czasu ładowania**|Zarezerwowane do użytku w przyszłości.|  
|**Długość wyszukiwania zestawu**|Zarezerwowane do użytku w przyszłości.|  
|**Bajty w stercie modułu ładującego**|Wyświetla bieżący rozmiar w bajtach pamięci przydzielonej przez moduł ładujący klasy we wszystkich domenach aplikacji. Pamięć zadeklarowana to będąca fizycznych miejsce zarezerwowane w pliku stronicowania na dysku.|  
|**Bieżący domen aplikacji**|Wyświetla bieżący numer domen aplikacji, które są ładowane w tej aplikacji.|  
|**Aktualna liczba zestawów**|Wyświetla bieżąca liczba zestawów załadowanych domen aplikacji wszystkich aktualnie uruchomionej aplikacji. Jeśli zestaw jest ładowany jako neutralny dla domen z wielu domen aplikacji, ten licznik jest zwiększany tylko raz.|  
|**Bieżącej klasy załadowany**|Wyświetla bieżącą liczbę klas ładowany na wszystkich zestawów.|  
|**Liczba domen aplikacji**|Wyświetla liczbę domen aplikacji załadowane na sekundę. Ten licznik nie jest średnią wraz z upływem czasu; Wyświetla różnicy między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Liczba domen aplikacji zwolnione**|Wyświetla liczbę domen aplikacji, które pozostaną niezaładowane na sekundę. Ten licznik nie jest średnią wraz z upływem czasu; Wyświetla różnicy między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Liczba zestawów**|Wyświetla liczbę zestawów załadowanych na sekundę we wszystkich domenach aplikacji. Jeśli zestaw jest ładowany jako neutralny dla domen z wielu domen aplikacji, ten licznik jest zwiększany tylko raz.<br /><br /> Ten licznik nie jest średnią wraz z upływem czasu; Wyświetla różnicy między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Załadowano stopień klas**|Wyświetla liczbę klas załadowane na sekundę w przypadku wszystkich zestawów. Ten licznik nie jest średnią wraz z upływem czasu; Wyświetla różnicy między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Współczynnik błędów ładowania**|Wyświetla liczbę klas, których nie można załadować na sekundę. Ten licznik nie jest średnią wraz z upływem czasu; Wyświetla różnicy między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.<br /><br /> Błędy ładowania może wystąpić z wielu powodów, takich jak nieodpowiednie zabezpieczeń lub nieprawidłowy format. Aby uzyskać szczegółowe informacje Zobacz profilowanie usługi pomocy.|  
|**Łączna liczba błędów ładowania**|Przedstawia szczytową liczbę klas, które nie zostały załadowane od czasu uruchomienia aplikacji.<br /><br /> Błędy ładowania może wystąpić z wielu powodów, takich jak nieodpowiednie zabezpieczeń lub nieprawidłowy format. Aby uzyskać szczegółowe informacje Zobacz profilowanie usługi pomocy.|  
|**Łączna liczba domen aplikacji**|Wyświetla szczytowa liczba domen aplikacji załadowane od czasu uruchomienia aplikacji.|  
|**Łączna liczba domen aplikacji zwolnione**|Wyświetla łączną liczbę domen aplikacji, które pozostaną niezaładowane od czasu uruchomienia aplikacji. Jeśli domena aplikacji jest ładowany i zwolnione wiele razy, ten licznik zwiększa każdorazowo, gdy domena aplikacji jest zwalniana.|  
|**Łączna liczba zestawów**|Wyświetla łączną liczbę zestawów załadowanych od czasu uruchomienia aplikacji. Jeśli zestaw jest ładowany jako neutralny dla domen z wielu domen aplikacji, ten licznik jest zwiększany tylko raz.|  
|**Łączna liczba klasy załadowany**|Wyświetla skumulowaną liczbę klas ładowany na wszystkie zestawy, od czasu uruchomienia aplikacji.|  
  
<a name="lockthread"></a>   
## <a name="lock-and-thread-performance-counters"></a>Liczniki wydajności blokady i wątku  
 Kategoria wydajności konsoli .NET CLR LocksAndThreads zawiera liczniki, które zawierają informacje o zarządzanych blokad i wątków używanych przez aplikację. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Liczba bieżących wątków logiczne**|Wyświetla liczbę wątków zarządzanych obiekty w aplikacji. Ten licznik przechowuje licznik jednocześnie działające i zatrzymane wątków. Ten licznik nie jest średnią wraz z upływem czasu; Wyświetla ostatnią odczytaną wartość.|  
|**Liczba bieżących wątków fizycznych**|Wyświetla liczbę wątków natywnych systemu operacyjnego, utworzone i należą do środowiska uruchomieniowego języka wspólnego pełnić rolę podstawowej wątków dla wątków zarządzanych obiektów. Wartość tego licznika nie obejmuje wykorzystywanych przez środowisko uruchomieniowe w operacjach wewnętrzne; wątków jest podzbiorem wątki w procesie systemu operacyjnego.|  
|**Liczba bieżących wątków rozpoznane**|Wyświetla liczbę wątków, które obecnie są rozpoznawane przez środowisko uruchomieniowe. Te wątki są skojarzone z odpowiedniego obiektu wątków zarządzanych. Środowisko wykonawcze nie tworzy te wątki, ale uruchamianych wewnątrz środowiska uruchomieniowego co najmniej raz.<br /><br /> Tylko unikatowe wątki są śledzone; wątki mających taki sam identyfikator wątku, które ponownie środowisko uruchomieniowe lub są tworzone ponownie po zakończeniu wątku nie są liczone dwa razy.|  
|**Liczba całkowita liczba wątków rozpoznane**|Wyświetla całkowitą liczbę wątków, które zostały uznane przez środowisko uruchomieniowe od czasu uruchomienia aplikacji. Te wątki są skojarzone z odpowiedniego obiektu wątków zarządzanych. Środowisko wykonawcze nie tworzy te wątki, ale uruchamianych wewnątrz środowiska uruchomieniowego co najmniej raz.<br /><br /> Tylko unikatowe wątki są śledzone; wątki mających taki sam identyfikator wątku, które ponownie środowisko uruchomieniowe lub są tworzone ponownie po zakończeniu wątku nie są liczone dwa razy.|  
|**Współczynnik rywalizacji o zasoby / sekundę**|Wyświetla szybkość jaką wątków w środowisku uruchomieniowym próba uzyskania blokady zarządzanych niepomyślnie.|  
|**Bieżąca długość kolejki**|Wyświetla całkowitą liczbę wątków, które aktualnie oczekują na uzyskanie zarządzanej blokady w aplikacji. Ten licznik nie jest średnią wraz z upływem czasu; Wyświetla ostatnią odczytaną wartość.|  
|**Długość kolejki / s**|Wyświetla liczbę wątków na sekundę, które oczekują na uzyskanie blokady w aplikacji. Ten licznik nie jest średnią wraz z upływem czasu; Wyświetla różnicy między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Szczytowy długość kolejki**|Wyświetla całkowitą liczbę wątków, które oczekiwany zablokować zarządzanych od czasu uruchomienia aplikacji.|  
|**Liczba wątków rozpoznawanym / sekundę**|Wyświetla liczbę wątków na sekundę, które zostały uznane przez środowisko uruchomieniowe. Te wątki są skojarzone z odpowiedniego obiektu wątków zarządzanych. Środowisko wykonawcze nie tworzy te wątki, ale uruchamianych wewnątrz środowiska uruchomieniowego co najmniej raz.<br /><br /> Tylko unikatowe wątki są śledzone; wątki mających taki sam identyfikator wątku, które ponownie środowisko uruchomieniowe lub są tworzone ponownie po zakończeniu wątku nie są liczone dwa razy.<br /><br /> Ten licznik nie jest średnią wraz z upływem czasu; Wyświetla różnicy między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Całkowita liczba rywalizacji**|Wyświetla całkowitą liczbę razy wątków w środowisku uruchomieniowym podjęto próbę uzyskania blokady zarządzanych niepomyślnie.|  
  
<a name="memory"></a>   
## <a name="memory-performance-counters"></a>Liczniki wydajności pamięci  
 Kategoria wydajności konsoli pamięć .NET CLR zawiera liczniki, które zawierają informacje dotyczące modułu odśmiecania pamięci. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Liczba bajtów we wszystkich Stertach**|Przedstawia sumę **Gen 1, Rozmiar sterty**, **Gen 2. Generace**, i **duży rozmiar sterty obiektu** liczników. Ten licznik wskazuje aktualnie przydzielonej pamięci w bajtach na wyrzucanie elementów bezużytecznych stosów.|  
|**# Obsługuje GC**|Wyświetla bieżącą liczbę uchwyty wyrzucania elementów bezużytecznych w użyciu. Uchwyty wyrzucania elementów bezużytecznych są dojścia do zasobów spoza środowiska uruchomieniowego języka wspólnego i środowisku zarządzanym.|  
|**# Pokolenia 0**|Przedstawia liczbę przypadków, gdy obiekty generacji 0 (czyli najmłodszych, ostatnio przydzielone obiekty) są bezużyteczne, od czasu uruchomienia aplikacji.<br /><br /> Generację 0 wyrzucania elementów bezużytecznych występuje, gdy ilość dostępnej pamięci w generacji 0 nie jest wystarczająca do obsługi żądania przydzielenia. Ten licznik jest zwiększany po zakończeniu generację 0 wyrzucania elementów bezużytecznych. Wyższej generacji wyrzucania elementów bezużytecznych uwzględniają wszystkie niższych generacji. Ten licznik jest jawnie zwiększany po wyższym wyrzucania elementów bezużytecznych generacji (generacja 1 lub 2).<br /><br /> Ten licznik wskazuje ostatnią odczytaną wartość. **_Global\_**  wartość licznika jest niedokładna i należy ją ignorować.|  
|**# Pokolenia 1**|Przedstawia liczbę przypadków, gdy obiekty generacji 1 są bezużyteczne, od czasu uruchomienia aplikacji.<br /><br /> Licznik jest zwiększany po zakończeniu generację 1 wyrzucania elementów bezużytecznych. Wyższej generacji wyrzucania elementów bezużytecznych uwzględniają wszystkie niższych generacji. Ten licznik jest jawnie zwiększany po wyższym wyrzucania elementów bezużytecznych generacji (generacja 2).<br /><br /> Ten licznik wskazuje ostatnią odczytaną wartość. **_Global\_**  wartość licznika jest niedokładna i należy ją ignorować.|  
|**# Pokolenia 2**|Przedstawia liczbę przypadków, gdy obiekty generacji 2 są bezużyteczne, od czasu uruchomienia aplikacji. Licznik jest zwiększany na końcu 2 wyrzucania elementów bezużytecznych generacji (nazywany także pełne wyrzucanie elementów bezużytecznych).<br /><br /> Ten licznik wskazuje ostatnią odczytaną wartość. **_Global\_**  wartość licznika jest niedokładna i należy ją ignorować.|  
|**# Wywołane GC**|Przedstawia szczytową liczbę razy, wyrzucanie elementów bezużytecznych zostało wykonane z powodu jawnym wywołaniem <xref:System.GC.Collect%2A?displayProperty=nameWithType>. Jest dobrą praktyką, aby umożliwić moduł zbierający elementy bezużyteczne dostosować częstotliwość jego kolekcjach.|  
|**Liczba obiektów przypięte**|Wyświetla liczbę obiektów przypiętych podczas ostatniego wyrzucania elementów bezużytecznych. Przypięte obiekt jest obiektem, który moduł odśmiecania pamięci nie można przenieść w pamięci. Ten licznik śledzi przypiętych tylko obiekty, które są bezużyteczne sterty. Na przykład wyrzucanie elementów bezużytecznych generacji 0 powoduje, że wyliczenie obiektów przypiętych tylko w stosie generacji 0.|  
|**Liczba bloków ujścia w użyciu**|Wyświetla bieżąca liczba bloków synchronizacji w użyciu. Bloki synchronizacji są przydzielone do przechowywania informacji o synchronizacji struktur danych dla obiektów. Przechowują słabe odwołania do obiektów zarządzanych i musi zostać przeprowadzone skanowanie przez moduł odśmiecania pamięci. Bloki synchronizacji nie są ograniczone do przechowywania informacji o synchronizacji; można również przechowywać metadanych międzyoperacyjne COM. Ten licznik wskazuje problemy z wydajnością za pomocą intensywnie korzysta z podstawowych synchronizacji.|  
|**# Łączna liczba przydzielonych bajtów**|Wyświetlana jest ilość pamięci wirtualnej, w bajtach, aktualnie przydzielonej przez moduł odśmiecania pamięci. Pamięć zadeklarowana to pamięć fizyczna, dla której zarezerwowano miejsce w pliku stronicowania na dysku.|  
|**# Łączna liczba Zarezerwowane bajty**|Wyświetlana jest ilość pamięci wirtualnej, w bajtach, obecnie jest zarezerwowana przez moduł odśmiecania pamięci. Zarezerwowanej pamięci jest miejsce pamięci wirtualnej przeznaczone dla aplikacji, w przypadku nie dysku lub stron pamięci głównej.|  
|**% Czasu odzyskiwania pamięci**|Wyświetla procent minionego czasu, jaki był poświęcony na wykonywanie wyrzucania elementów bezużytecznych od ostatniego cyklu wyrzucania elementów w kolekcji. Ten licznik wskazuje zazwyczaj pracy wykonanej przez moduł garbage collector zbieranie i compact pamięci w imieniu aplikacji. Ten licznik jest aktualizowany tylko na końcu każdego wyrzucania elementów bezużytecznych. Ten licznik nie jest średnią; wartość odzwierciedla ostatnią odczytaną wartość.|  
|**Przydzielone bajty/s**|Wyświetla liczbę bajtów przydzielanych na stercie wyrzucania elementów bezużytecznych na sekundę. Ten licznik jest aktualizowany na końcu każdego wyrzucania elementów bezużytecznych, nie na każdej alokacji. Ten licznik nie jest średnią wraz z upływem czasu; Wyświetla różnicy między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Pozostałości finalizacji jest zakończona**|Wyświetla liczbę zebranych elementów bezużytecznych obiektów, które przeżyły kolekcji, ponieważ oczekują one można sfinalizować. Jeśli te obiekty przechowują odwołania do innych obiektów, tych obiektów również przetrwać, ale nie są liczone przez ten licznik. **Promowane finalizacji pamięci z generacji 0** reprezentuje pamięć, które przetrwały ze względu na finalizację.<br /><br /> Ten licznik nie jest zbiorcza; na koniec każdego wyrzucania elementów bezużytecznych z liczbą pozostałości jest aktualizowany podczas tylko tej określonej kolekcji. Ten licznik wskazuje dodatkowe obciążenie, które aplikacja może pociągnąć za sobą ze względu na finalizację.|  
|**Rozmiar sterty pokolenia 0**|Wyświetla maksymalna liczba bajtów, które mogą zostać zaalokowane w generacji 0. Bieżąca liczba bajtów przydzielonych w generacji 0 nie oznacza.<br /><br /> Wyrzucanie elementów bezużytecznych generacji 0 występuje, gdy alokacje od ostatniego zebrania przekroczenie tego rozmiaru. Rozmiar generacji 0 jest ona dostrojona przez moduł odśmiecania pamięci i można zmieniać podczas wykonywania aplikacji. Na koniec bezużytecznych generacji 0 rozmiar generacji 0 sterta to 0 bajtów. Ten licznik wskazuje rozmiar w bajtach, przydziały, które wywołuje dalej generację 0 wyrzucania elementów bezużytecznych.<br /><br /> Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, nie na każdej alokacji.|  
|**Velikost haldy 0 o podwyższonym poziomie bajtów na sekundę**|Wyświetla bajtów na sekundę, które są przenoszone z generacji 0 do 1. generacji. Pamięć jest podnoszony podczas jego przeżyje wyrzucania elementów bezużytecznych. Ten licznik jest wskaźnikiem stosunkowo długotrwałe obiektów tworzonych w ciągu sekundy.<br /><br /> Ten licznik wyświetla różnicę między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Velikost haldy 1. generace**|Wyświetla bieżąca liczba bajtów w generacji 1; Ten licznik nie wyświetla maksymalny rozmiar elementów w generacji 1. Obiekty nie są bezpośrednio przydzielone w tej generacji; są one promowane z poprzedniej generacji 0 wyrzucania elementów bezużytecznych. Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, nie na każdej alokacji.|  
|**Velikost haldy 1 o podwyższonym poziomie bajtów na sekundę**|Wyświetla bajtów na sekundę, które są przenoszone z generacji 1 do 2. generacji. Ten licznik nie są objęte obiekty, które są przenoszone tylko w przypadku, ponieważ oczekują one można sfinalizować.<br /><br /> Pamięć jest podnoszony podczas jego przeżyje wyrzucania elementów bezużytecznych. Nic nie zostanie podwyższony z generacji 2, ponieważ jest on najstarsze generacji. Ten licznik jest wskaźnikiem bardzo długotrwałe obiekty, tworzona na sekundę.<br /><br /> Ten licznik wyświetla różnicę między wartościami odczytanymi w ostatnich dwóch próbek podzielona przez długość interwału próbkowania.|  
|**Velikost haldy 2. generace**|Wyświetla bieżąca liczba bajtów w generacji 2. Obiekty nie są bezpośrednio przydzielone w tej generacji; są one promowane z generacji 1 podczas poprzedniej generacji 1 wyrzucania elementów bezużytecznych. Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, nie na każdej alokacji.|  
|**Duży rozmiar sterty obiektów**|Wyświetla bieżący rozmiar w bajtach sterty obiektów wielkich. Obiekty, które są większe niż około rozmiarze 85 000 bajtów są traktowane jako dużych obiektów moduł odśmiecania pamięci i są bezpośrednio przydzielone w stosie specjalne; nie są one promowane do generacji. Ten licznik jest aktualizowany na końcu wyrzucania elementów bezużytecznych, nie na każdej alokacji.|  
|**Identyfikator procesu**|Wyświetla identyfikator procesu wystąpienia procesu CLR, która jest monitorowana.|  
|**Podwyższono poziom pamięci finalizacji jest zakończona z pokolenia 0**|Wyświetla bajtów pamięci, które są przenoszone z generacji 0 do generacji 1, tylko w przypadku, ponieważ oczekują one można sfinalizować. Ten licznik nie jest zbiorcza; wyświetlana jest wartość zaobserwowane na końcu ostatniego wyrzucania elementów bezużytecznych.|  
|**Podwyższono poziom pamięci z pokolenia 0**|Wyświetla bajtów pamięci przetrwać wyrzucania elementów bezużytecznych, które są przenoszone z generacji 0 do 1. generacji. Ten licznik nie są objęte obiekty, które są przenoszone tylko w przypadku, ponieważ oczekują one można sfinalizować. Ten licznik nie jest zbiorcza; wyświetlana jest wartość zaobserwowane na końcu ostatniego wyrzucania elementów bezużytecznych.|  
|**Podwyższono poziom ilość pamięci Gen 1**|Wyświetla bajtów pamięci przetrwać wyrzucania elementów bezużytecznych, które są przenoszone z generacji 1 do 2. generacji. Ten licznik nie są objęte obiekty, które są przenoszone tylko w przypadku, ponieważ oczekują one można sfinalizować. Ten licznik nie jest zbiorcza; wyświetlana jest wartość zaobserwowane na końcu ostatniego wyrzucania elementów bezużytecznych. Ten licznik jest resetowany do 0, jeśli bezużytecznych generacji 0, który jest tylko ostatnich wyrzucania elementów bezużytecznych.|  
  
<a name="networking"></a>   
## <a name="networking-performance-counters"></a>Liczniki wydajności funkcji sieciowych  
 Kategoria .NET CLR sieci wydajności konsoli zawiera liczniki, które zawierają informacje o danych, które aplikacja wysyła i odbiera za pośrednictwem sieci. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**Odebrane bajty**|Łączna liczba Skumulowana liczba bajtów odebranych przez wszystkie <xref:System.Net.Sockets.Socket> obiektów w ramach <xref:System.AppDomain> od momentu uruchomienia procesu. Ta liczba obejmuje dane i wszelkie informacje protokołu, który nie jest zdefiniowany przez protokół TCP/IP.|  
|**Bajty wysłane**|Skumulowana liczba bajtów wysłanych przez wszystkie <xref:System.Net.Sockets.Socket> obiektów w ramach <xref:System.AppDomain> od momentu uruchomienia procesu. Ta liczba obejmuje dane i wszelkie informacje protokołu, który nie jest zdefiniowany przez protokół TCP/IP.|  
|**Ustanowionych połączeń**|Skumulowana liczba <xref:System.Net.Sockets.Socket> obiektów dla gniazda strumieni, które nigdy nie zostały połączone w ramach <xref:System.AppDomain> od momentu uruchomienia procesu.|  
|**Odebrane datagramy**|Łączna liczba Skumulowana liczba odebrane przez wszystkie pakiety datagram <xref:System.Net.Sockets.Socket> obiektów w ramach <xref:System.AppDomain> od momentu uruchomienia procesu.|  
|**Wysłane datagramy**|Łączna liczba Skumulowana liczba wysłanych przez wszystkich pakietów datagram <xref:System.Net.Sockets.Socket> obiektów w ramach <xref:System.AppDomain> od momentu uruchomienia procesu.|  
|**HttpWebRequest średni okres istnienia**|Średni czas ukończenia dla wszystkich <xref:System.Net.HttpWebRequest> obiektów, które zostało zakończone w ostatniego interwału w ramach <xref:System.AppDomain> od momentu uruchomienia procesu.|  
|**HttpWebRequest Średni czas oczekiwania**|Średni czas na kolejki dla wszystkich <xref:System.Net.HttpWebRequest> obiektów, które pozostanie kolejki w ostatniego interwału w ramach <xref:System.AppDomain> od momentu uruchomienia procesu.|  
|**HttpWebRequests utworzone na sekundę**|Liczba <xref:System.Net.HttpWebRequest> obiektów utworzonych w ciągu sekundy <xref:System.AppDomain>.|  
|**HttpWebRequests/s**|Liczba <xref:System.Net.HttpWebRequest> obiekty, które zostały dodane do kolejki na sekundę w ramach <xref:System.AppDomain>.|  
|**Przerwano HttpWebRequests na sekundę**|Liczba <xref:System.Net.HttpWebRequest> obiekty, których aplikacja o nazwie <xref:System.Net.HttpWebRequest.Abort%2A> metody na sekundę w ramach <xref:System.AppDomain>.|  
|**HttpWebRequests nie powiodło się na sekundę**|Liczba <xref:System.Net.HttpWebRequest> obiektów, które otrzymały kod stanu nie powiodło się z serwera na sekundę w ramach <xref:System.AppDomain>.|  
  
 Istnieje kilka rodzajów liczniki wydajności obsługiwanych funkcji sieciowych:  
  
-   Liczniki zdarzeń, które mierzą liczbę przypadków, gdy niektóre zdarzenia.  
  
-   Liczniki danych, które mierzą ilość danych wysyłanych lub odbieranych.  
  
-   Czas trwania liczniki, które mierzą procesy jak długo różne potrwać. Czas, w którym są mierzone na obiektach każdego interwału (zwykle w ciągu kilku sekund) po pochodzą z różnych stanów.  
  
-   Liczniki dla interwału, mierzących liczbę obiektów, które wykorzystują określonego przejścia dla interwału (zwykle na sekundę).  
  
 Następujące liczniki wydajności funkcji sieciowych dla zdarzeń:  
  
-   **Ustanowionych połączeń**  
  
-   **Odebrane datagramy**  
  
-   **Wysłane datagramy**  
  
 Te liczniki wydajności zawierają liczby, od momentu uruchomienia procesu. Liczbę <xref:System.Net.Sockets.Socket> ustanowionych połączeń zawiera jawne <xref:System.Net.Sockets.Socket> metoda wywołuje przez aplikację dla połączenia gniazda strumienia, który został ustanowiony również jako wewnętrzne wywołania innych klas (<xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.WebClient>, i <xref:System.Net.Sockets.TcpClient>, na przykład) do <xref:System.Net.Sockets.Socket> klasy  
  
 Liczniki dla **Odebrane datagramy** i **wysyłane datagramy** obejmuje datagram pakiety wysyłane lub odbierane za pomocą jawnego <xref:System.Net.Sockets.Socket> metoda wywołuje przez aplikację jako wewnętrznych oraz wywołań przez inne klasy (<xref:System.Net.Sockets.UdpClient>, na przykład) do <xref:System.Net.Sockets.Socket>. Klasa. Zliczeń **Odebrane datagramy** i **wysyłane datagramy** może również służyć do zapewnienia bardzo surowych miary liczbę bajtów wysłanych lub odebranych przy użyciu datagramy, zakładając, że średni rozmiar datagramu.  
  
 Liczniki wydajności funkcji sieciowych dla danych są następujące:  
  
-   **Odebrane bajty**  
  
-   **Bajty wysłane**  
  
 Liczniki powyżej Podaj liczbę bajtów, od momentu uruchomienia procesu.  
  
 Istnieją dwa liczniki czas trwania, które mierzą się, jak długo <xref:System.Net.HttpWebRequest> obiektów dopuszczone albo ich całe życie cykl lub po prostu część go:  
  
-   **HttpWebRequest średni okres istnienia**  
  
-   **HttpWebRequest Średni czas oczekiwania**  
  
 Dla **średni okres istnienia HttpWebRequest** licznik okres istnienia większość <xref:System.Net.HttpWebRequest> obiektów zawsze zaczyna się od czasu utworzenia obiektu, aż do czasu, który w strumieniu odpowiedzi jest zamknięty przez aplikację. Istnieją dwa przypadki nietypowe:  
  
-   Jeśli aplikacja nigdy nie wywołuje <xref:System.Net.HttpWebRequest.GetResponse%2A> lub <xref:System.Net.HttpWebRequest.BeginGetResponse%2A> metody, a następnie okres istnienia <xref:System.Net.HttpWebRequest> obiektu jest ignorowana.  
  
-   Jeśli <xref:System.Net.HttpWebRequest> obiektu zgłasza <xref:System.Net.WebException> podczas wywoływania <xref:System.Net.HttpWebRequest.GetResponse%2A> lub <xref:System.Net.HttpWebRequest.EndGetResponse%2A> metod, okres istnienia kończy się, gdy wyjątek jest zgłaszany. Z technicznego punktu widzenia zasadniczy strumień odpowiedzi także jest zamknięty w tym momencie (w strumieniu odpowiedzi zwrócone do użytkownika jest naprawdę strumień pamięci, zawierający kopię w strumieniu odpowiedzi).  
  
 Istnieją cztery liczniki, które śledzą pewnych <xref:System.Net.HttpWebRequest> obiektu problemy dla interwału. Te liczniki wydajności mogą pomóc deweloperom aplikacji i administratorów i działu pomocy technicznej lepiej zrozumieć, jakie <xref:System.Net.HttpWebRequest> robią obiektów. Następujące liczniki:  
  
-   **HttpWebRequests utworzone na sekundę**  
  
-   **HttpWebRequests/s**  
  
-   **Przerwano HttpWebRequests na sekundę**  
  
-   **HttpWebRequests nie powiodło się na sekundę**  
  
 Dla **Aborted HttpWebRequests na sekundę** licznik, wewnętrzny wywołania <xref:System.Net.HttpWebRequest.Abort%2A> są również uwzględniane. Te wewnętrzne wywołania są zazwyczaj spowodowane przekroczenia limitu czasu, aplikacja może być konieczne mierzenie.  
  
 **HttpWebRequests nie powiodło się/s** licznika zawiera liczbę <xref:System.Net.HttpWebRequest> obiektów, które otrzymały stan niepowodzenia kodu z serwera na sekundę. Oznacza to, że kod stanu otrzymany z serwera Http, na końcu żądania nie jest w zakresie od 200 do 299. Kody stanu, które są obsługiwane i powoduje nowe żądanie (wiele kodów stanu 401 nieautoryzowane, na przykład) będą się nie powieść lub nie nie w zależności od wyniku ponawiania prób. Jeśli aplikacja będzie wyświetlony komunikat o błędzie, w oparciu o ponowienie próby, ten licznik jest zwiększany.  
  
 Liczniki wydajności funkcji sieciowych można uzyskać dostęp i zarządzane przy użyciu <xref:System.Diagnostics.PerformanceCounter> i pokrewne klasy w <xref:System.Diagnostics> przestrzeni nazw. Liczniki wydajności funkcji sieciowych można również wyświetlać za pomocą konsoli programu Windows Performance Monitor.  
  
 Liczniki wydajności sieci muszą być włączone w pliku konfiguracji do użycia. Wszystkie liczniki wydajności funkcji sieciowych są włączone lub wyłączone przy użyciu pojedynczego ustawienia w pliku konfiguracji. Poszczególne liczniki wydajności funkcji sieciowych nie może być włączona lub wyłączona. Aby uzyskać więcej informacji, zobacz [ \<performanceCounter >, Element (ustawienia sieci)](../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md).  
  
 Jeżeli są włączone liczniki klas sieciowych, spowoduje to utworzenie i zaktualizuj per-AppDomain oraz z liczników wydajności globalnego. Wyłączenie tej opcji, aplikacja nie zapewnia żadnych sieci danych licznika wydajności.  
  
 Liczniki wydajności są podzielone na kategorie. Aplikację można wyświetlić listę wszystkich kategorii w poniższym przykładowym kodem:  
  
```  
PerformanceCounterCategory[] Array = PerformanceCounterCategory.GetCategories();  
for (int i = 0; i < Array.Length; i++)  
{  
    Console.Out.WriteLine("{0}. Name={1} Help={2}", i, Array[i].CategoryName, Array[i].CategoryHelp);  
}  
```  
  
 Liczniki wydajności funkcji sieciowych są wymienione w dwie kategorie:  
  
-   ".NET CLR sieci" - oryginalnego liczniki wydajności, które są wprowadzone w .NET Framework w wersji 2 i obsługiwane w systemie .NET Framework w wersji 2 lub nowszy.  
  
-   ".NET CLR sieci 4.0.0.0" - wszystkie powyższe gniazda liczników i nowe liczniki wydajności, które są obsługiwane w systemie .NET Framework w wersji 4 lub nowszy. Te nowe liczniki Podaj informacje o wydajności na <xref:System.Net.HttpWebRequest> obiektów.  
  
 Aby uzyskać więcej informacji na temat dostęp i zarządzanie liczników wydajności w aplikacji, zobacz [liczniki wydajności](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
<a name="security"></a>   
## <a name="security-performance-counters"></a>Liczniki wydajności zabezpieczeń  
 Kategoria wydajności konsoli .NET CLR zabezpieczeń zawiera liczniki, które zapewniają, że informacje o zabezpieczeniach sprawdzanych środowiska uruchomieniowego języka wspólnego dla aplikacji. W poniższej tabeli opisano te liczniki wydajności.  
  
|Licznik wydajności|Opis|  
|-------------------------|-----------------|  
|**# Sprawdzanie w czasie łącza**|Wyświetla łączną liczbę zabezpieczenia dostępu kodu w czasie konsolidacji sprawdza, czy od czasu uruchomienia aplikacji. Sprawdzanie zabezpieczeń dostępu kodu w czasie konsolidacji są wykonywane, gdy obiekt wywołujący żąda uprawnienia określonego podczas kompilacji just-in-time (JIT). Sprawdź czas łącza jest wykonywana raz na obiekt wywołujący. Ten licznik nie jest wskaźnikiem poważnych problemów z wydajnością; jest ona jedynie wskaźnikiem aktywności systemu zabezpieczeń.|  
|**% Czasu w kontrolach RT**|Przedstawia wartość procentową czasu wykonywania testy środowiska uruchomieniowego kodu dostępu zabezpieczeń od ostatniej próbki. Ten licznik jest aktualizowany na końcu sprawdzanie zabezpieczeń .NET Framework. Nie jest to wartość średnia; reprezentuje ostatnią odczytaną wartość.|  
|**% Czasu Sig uwierzytelniania**|Zarezerwowane do użytku w przyszłości.|  
|**Głębokość przeszukiwania stosu**|Wyświetla Głębokość stosu podczas ostatniego sprawdzanie zabezpieczeń dostępu kodu środowiska uruchomieniowego. Sprawdzanie zabezpieczeń dostępu kodu środowiska uruchomieniowego są wykonywane przez zalet stosu. Ten licznik nie jest średnią; Wyświetla ostatnią odczytaną wartość.|  
|**Sprawdzanie całkowitego czasu wykonania**|Wyświetla łączną liczbę kod środowiska uruchomieniowego dostępu kontrole zabezpieczeń wykonywane od czasu uruchomienia aplikacji. Kod środowiska uruchomieniowego dostęp zabezpieczeń, które testy są wykonywane, gdy określone uprawnienie wymagane przez obiekt wywołujący. Sprawdzanie środowiska uruchomieniowego jest wykonywane przy każdym wywołaniu przez obiekt wywołujący i sprawdza, czy bieżącego stosu wątku wywołującego. Gdy jest używane z **głębokość zaprezentuje stosu** licznika, ten licznik wskazuje spadek wydajności, występujący do sprawdzania zabezpieczeń.|  
  
## <a name="see-also"></a>Zobacz też  
 [Liczniki wydajności](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 [Profilowanie środowiska uruchomieniowego](../../../docs/framework/debug-trace-profile/runtime-profiling.md)
