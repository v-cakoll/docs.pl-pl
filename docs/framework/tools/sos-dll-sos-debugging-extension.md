---
title: SOS.dll (rozszerzenie do debugowania SOS)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging extensions
- SOS debugging extensions
- SOS.dll
ms.assetid: 9ac1b522-77ab-4cdc-852a-20fcdc9ae498
caps.latest.revision: "55"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e35880e0f068ebcbc2b51ae3e8c3f9d2671cea1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="sosdll-sos-debugging-extension"></a>SOS.dll (rozszerzenie do debugowania SOS)
Rozszerzenie debugowania SOS (SOS.dll) ułatwia debugowanie programów zarządzanych w Visual Studio i debugerze systemu Windows (WinDbg.exe) poprzez dostarczanie informacji na temat wewnętrznego środowiska uruchomieniowego języka wspólnego (CLR). To narzędzie wymaga włączenia debugowania niezarządzanego w projekcie. SOS.dll jest automatycznie instalowany z .NET Framework. Aby użyć SOS.dll w programie Visual Studio, zainstalować [zestaw sterowników systemu Windows (WDK)](http://msdn.microsoft.com/windows/hardware/hh852362).  
  
> [!NOTE]
>  Jeśli używasz [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], SOS.dll jest obsługiwana w debugera systemu Windows w programie Visual Studio, ale nie w oknie bezpośrednim debuger programu Visual Studio.  
  
## <a name="syntax"></a>Składnia  
  
```  
![command] [options]   
```  
  
## <a name="commands"></a>Polecenia  
  
|Polecenie|Opis|  
|-------------|-----------------|  
|**AnalyzeOOM** (**ao**)|Wyświetla informacje o ostatnim OOM, który wystąpił w żądaniu alokacji w stercie modułu odśmiecania pamięci. (W module odśmiecania pamięci dla serwera wyświetla OOM, jeżeli wystąpił, dla każdej sterty modułu odśmiecania pamięci.)|  
|**BPMD** [**- nofuturemodule**] [\<*nazwy modułu*> \<*nazwę metody*>] [**- MD** <`MethodDesc`>] **— lista** **-wyczyść** \< *oczekujących numer punktu przerwania* >  **- clearall**|Tworzy punkt przerwania w określonej metodzie w określonym module.<br /><br /> Jeśli określony moduł i metoda nie zostały załadowane, to polecenie czeka na powiadomienie, że moduł został załadowany i skompilowany „just in time” (JIT) przed utworzeniem punktu przerwania.<br /><br /> Lista oczekujących punktów przerwania można zarządzać za pomocą **— lista**, **-wyczyść**, i **- clearall** opcje:<br /><br /> **— Lista** opcja generuje listę wszystkich oczekujących punktów przerwania. Jeśli oczekujący punkt przerwania ma niezerowy identyfikator modułu, ten punkt przerwania jest właściwy dla funkcji w tym określonym załadowanym module. Jeśli oczekujący punkt przerwania ma zerowy identyfikator modułu, ten punkt przerwania ma zastosowanie do modułów, które nie zostały jeszcze załadowane.<br /><br /> Użyj **-wyczyść** lub **- clearall** opcję, aby usunąć oczekujących punktów przerwania z listy.|  
|**CLRStack** [**-**] [**-l**] [**-p**] [**-n**]|Dostarcza ślad stosu wyłącznie dla kodu zarządzanego.<br /><br /> **-P** opcja powoduje wyświetlenie argumenty funkcji zarządzanego.<br /><br /> **-L** opcji przedstawia informacje o zmiennych lokalnych w ramce. Rozszerzenie debugowania SOS nie można pobrać nazwy lokalne, dzięki czemu dane wyjściowe dla lokalnych nazw jest w formacie \< *adresu lokalnego* >   **=**  \< *wartość*>.<br /><br /> **-**(Wszystkie) opcja jest skrót **-l** i **-p**połączeniu.<br /><br />  **-n**  Opcji wyłącza wyświetlanie nazwy pliku źródłowego i numery wierszy. Jeśli opcja debugera SYMOPT_LOAD_LINES jest określona, SOS będzie wyszukiwać symbole dla każdej ramki zarządzanej i jeśli wyszukiwanie zakończy się pomyślnie, wyświetlona zostanie odpowiadająca nazwa pliku źródłowego i numer wiersza.  **-n**  (Bez numerów wierszy) powoduje wyłączenie tej funkcji można określić parametru.<br /><br /> Rozszerzenie debugowania SOS nie wyświetla ramek przejścia na platformach opartych o procesory x64 i IA-64.|  
|**COMState**|Wyświetla listę modelu apartamentu COM dla każdego wątku i `Context` wskaźnika, jeśli jest dostępna.|  
|**DumpArray** [**-start** \< *startIndex*>] [**-długość** \< *długość*>] [**— szczegóły**] [**- nofields**] \< *tablicy adres obiektu*><br /><br /> —lub—<br /><br /> **DA** [**-start** \< *startIndex*>] [**-długość** \< *długość*>] [**— szczegóły**] [**- nofields**] *tablicy adres obiektu*>|Sprawdza elementy obiektu tablicowego.<br /><br /> **-Start** opcja określa początkowy indeks, w którym można wyświetlić elementy.<br /><br /> **-Długość** opcja określa, ile elementów do wyświetlenia.<br /><br /> **— Szczegóły** opcja wyświetla szczegóły przy użyciu elementu **DumpObj** i **DumpVC** formatów.<br /><br /> **- Nofields** opcji uniemożliwia wyświetlanie tablic. Ta opcja jest dostępna tylko wtedy, gdy **— szczegóły** określono opcję.|  
|**DumpAssembly** \< *adres zestawu*>|Wyświetla informacje o zestawie.<br /><br /> **DumpAssembly** polecenia zawiera wiele modułów, jeśli istnieją.<br /><br /> Adres zestawu można uzyskać za pomocą **DumpDomain** polecenia.|  
|**DumpClass** \< *EEClass adresu*>|Przedstawia informacje na temat `EEClass` skojarzony z typem struktury.<br /><br /> **DumpClass** polecenie wyświetla wartości pól statycznych, ale nie są wyświetlane wartości niestatycznego pola.<br /><br /> Użyj **DumpMT**, **DumpObj**, **Name2EE**, lub **Token2EE** polecenie, aby uzyskać `EEClass` strukturę adresu.|  
|**DumpDomain** [\<*adres domeny*>]|Wylicza każdego <xref:System.Reflection.Assembly> obiekt załadowany w ramach określonego <xref:System.AppDomain> obiekt adres.  Gdy wywoływana bez parametrów **DumpDomain** polecenie wyświetla listę wszystkich <xref:System.AppDomain> obiektów w procesie.|  
|**DumpHeap** [**-stat**] [**— ciągi**] [**-krótki**] [**-min** \< *rozmiar*>] [**-max** \< *rozmiar*>] [**- thinlock**] [**- startAtLowerBound**] [**- mt** \< *adres MethodTable*>] [**— typ** \< *nazwy typu częściowego*>] [*start* [*zakończenia*]]|Wyświetla informacje dotyczące sterty zebranej podczas odśmiecania pamięci i statystyk odśmiecania w stosunku do obiektów.<br /><br /> **DumpHeap** polecenie wyświetla ostrzeżenie, jeśli wykryje nadmiernej fragmentacji w stercie modułu zbierającego elementy bezużyteczne.<br /><br /> **-Stat** opcja ogranicza dane wyjściowe do podsumowanie typów statystycznych.<br /><br /> **— Ciągi** opcja ogranicza dane wyjściowe do wartości ciągu statystyczne podsumowania.<br /><br /> **-Krótki** opcji ogranicza dane wyjściowe z adresem każdego obiektu. Dzięki temu można łatwo strumieniować dane wyjściowe z polecenia do innego polecenia debugera w celu automatyzacji.<br /><br /> **-Min** opcja ignoruje obiekty, które mają mniej niż `size` parametr podany w bajtach.<br /><br /> **-Max** opcja ignoruje obiektów, które są większe niż `size` parametr podany w bajtach.<br /><br /> **- Thinlock** opcji raporty ThinLocks.  Aby uzyskać więcej informacji, zobacz **SyncBlk** polecenia.<br /><br /> `-startAtLowerBound` Opcja wymusza stercie rozpoczęcie dolna granica zakresu podany adres. Podczas fazy planowania sterta często nie posiada funkcji przechodzenia, ponieważ obiekty są przenoszone. Ta opcja wymusza **DumpHeap** zacząć jej przechodzenia w określonym dolną granicę. Należy podać adres prawidłowego obiektu jako dolną granicę, aby ta opcja działała. Można wyświetlić pamięć pod adresem błędnego obiektu, aby ręcznie odnaleźć następną tabelę metod. Jeśli odzyskiwanie pamięci jest obecnie w wywołaniu `memcopy`, można go również może znaleźć adres następnego obiektu, dodając rozmiar początkowy adres, który jest ona podawana jako parametr.<br /><br /> **- Mt** opcja wyświetla tylko te obiekty, które odpowiadają określonym `MethodTable` struktury.<br /><br /> **— Typ** opcja wyświetla tylko te obiekty, których nazwa typu jest zgodna podciąg określonego ciągu.<br /><br /> `start` Parametru zaczyna się lista z określonego adresu.<br /><br /> `end` Parametr zatrzymuje listę pod określonym adresem.|  
|**DumpIL** \< *obiektu zarządzanego elementu DynamicMethod*> &#124;       \< *Wskaźnika DynamicMethodDesc*> &#124;        \< *MethodDesc wskaźnika*>|Wyświetla język pośredni Microsoft (MSIL) skojarzony z zarządzaną metodą.<br /><br /> Należy zauważyć, że dynamiczny MSIL jest emitowany inaczej od MSIL, który jest ładowany z zestawu. Dynamiczny MSIL odnosi się do obiektów w tablicy obiektu zarządzanego, a nie do tokenów metadanych.|  
|**DumpLog** [**- addr** \< *addressOfStressLog*>] [<*Filenam*`e`>]|Zapisuje zawartość dziennika obciążenia pamięci do określonego pliku. Jeśli nazwa nie zostanie określona, polecenie tworzy plik o nazwie StressLog.txt w bieżącym katalogu.<br /><br /> Dziennik obciążenia pamięci pomaga w diagnozowaniu błędów obciążenia pamięci bez używania blokad lub we/wy. Aby włączyć dziennik akcent, ustaw następujące klucze rejestru w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework:<br /><br /> (DWORD) StressLog = 1<br /><br /> (DWORD) LogFacility = 0xffffffff<br /><br /> (DWORD) StressLogSize = 65536<br /><br /> Opcjonalny `-addr` opcja pozwala określić dziennik akcent innych niż domyślne dziennika.|  
|**DumpMD** \< *MethodDesc adresu*>|Przedstawia informacje na temat `MethodDesc` struktury pod określonym adresem.<br /><br /> Można użyć **IP2MD** polecenie, aby uzyskać `MethodDesc` struktury adres z funkcją zarządzaną.|  
|**DumpMT** [**-MD**] \< *MethodTable adresu*>|Wyświetla informacje dotyczące tabeli metod pod podanym adresem. Określanie **-MD** opcja powoduje wyświetlenie listy wszystkich metod zdefiniowane z obiektem.<br /><br /> Każdy obiekt zarządzany zawiera wskaźnik tabeli metod.|  
|**DumpMethodSig** \< *sigaddr*><*moduleadd*`r`>|Przedstawia informacje na temat `MethodSig` struktury pod określonym adresem.|  
|**DumpModule** [**- mt**] \< *adresów modułu*>|Wyświetla informacje dotyczące modułu pod podanym adresem. **- Mt** opcja wyświetla typy zdefiniowane w module i typy odwołuje się moduł<br /><br /> Można użyć **DumpDomain** lub **DumpAssembly** polecenie, aby pobrać adres modułu.|  
|**DumpObj** [**- nofields**] \< *obiekt adresu*><br /><br /> —lub—<br /><br /> **CZY** \< *obiekt adresu*>|Wyświetla informacje dotyczące obiektu pod podanym adresem. **DumpObj** polecenie wyświetla pola, `EEClass` struktury informacji o tabeli — Metoda i rozmiar obiektu.<br /><br /> Można użyć **DumpStackObjects** polecenie, aby pobrać adres obiektu.<br /><br /> Należy pamiętać, że można uruchomić **DumpObj** polecenia dla pól typu `CLASS` ponieważ są one również obiektów.<br /><br /> `-` **Nofields** opcja zapobiega pola obiektu będzie wyświetlany, jest przydatne w przypadku obiektów, takich jak ciąg.|  
|**DumpRuntimeTypes**|Wyświetla obiekty typu środowiska uruchomieniowego w stercie modułu odśmiecania pamięci i wyświetla ich nazwy skojarzonych typów i tabele metod.|  
|**DumpStack** [**- EE**] [**-n**] [`top` *stosu* [`bottom` *stos* `k`]]|Wyświetla ślad stosu.<br /><br /> **- EE** opcji powoduje, że **DumpStack** polecenie, aby wyświetlić tylko zarządzanego funkcji. Użyj `top` i `bottom` parametrów, aby ograniczyć liczbę ramek stosu wyświetlany na x86 platform.<br /><br />  **-n**  Opcji wyłącza wyświetlanie nazwy pliku źródłowego i numery wierszy. Jeśli opcja debugera SYMOPT_LOAD_LINES jest określona, SOS będzie wyszukiwać symbole dla każdej ramki zarządzanej i jeśli wyszukiwanie zakończy się pomyślnie, wyświetlona zostanie odpowiadająca nazwa pliku źródłowego i numer wiersza.  **-n**  (Bez numerów wierszy) powoduje wyłączenie tej funkcji można określić parametru.<br /><br /> Na x86 i x64 64 **DumpStack** polecenie tworzy ślad stosu pełne.<br /><br /> Na platformach opartych na protokole IA-64 **DumpStack** polecenia naśladuje debugera **K** polecenia. `top` i `bottom` parametry są ignorowane na platformach opartych na protokole IA-64.|  
|**DumpSig** \< *sigaddr*> \<*moduleaddr*>|Przedstawia informacje na temat `Sig` struktury pod określonym adresem.|  
|**DumpSigElem** \< *sigaddr*> \<*moduleaddr*>|Wyświetla jeden element obiektu podpisu. W większości przypadków należy użyć **DumpSig** spojrzeć na poszczególne podpisu obiektów. Jednak jeśli podpis jest uszkodzone w sposób, można użyć **DumpSigElem** odczytać prawidłowe części.|  
|**DumpStackObjects** [**-Sprawdź**] [`top` *stosu* [`bottom` *stosu*]]<br /><br /> —lub—<br /><br /> **DSO** [**-Sprawdź**] [`top` *stosu* [`bottom` *stosu*]]|Wyświetla wszystkie zarządzane obiekty znalezione w granicach bieżącego stosu.<br /><br /> **-Sprawdź** opcja sprawdza poprawność każdego niestatyczna `CLASS` pole pole obiektu.<br /><br /> Użyj **DumpStackObject** polecenia za pomocą polecenia śledzenia stosu, takich jak **K** polecenia i **CLRStack** polecenie, aby określić wartości zmiennych lokalnych i Parametry.|  
|**DumpVC** \< *adres MethodTable*> \<*adresu*>|Wyświetla informacje dotyczące pól klasy wartości pod podanym adresem.<br /><br /> **MethodTable** parametr umożliwia **DumpVC** polecenie, aby poprawnie zinterpretować pól. Klasy wartości nie posiadają tabeli metod jako ich pierwsze pole.|  
|**EEHeap** [**-gc**] [**— moduł ładujący**]|Wyświetla informacje dotyczące zużywanej pamięci procesu przez wewnętrzne struktury danych środowiska uruchomieniowego języka wspólnego.<br /><br /> **-Gc** i **— moduł ładujący** opcje ograniczyć dane wyjściowe tego polecenia, aby moduł zbierający elementy bezużyteczne lub modułu ładującego struktury danych.<br /><br /> Informacje dotyczące modułu odśmiecania pamięci wyświetlają zakresy każdego segmentu w zarządzanej stercie.  Jeśli wskaźnik mieści się w zakresie segmentu, podane przez **-gc**, wskaźnik jest wskaźnik do obiektu.|  
|**EEStack** [**-krótki**] [**- EE**]|Uruchamia **DumpStack** na wszystkie wątki tego procesu.<br /><br /> **- EE** opcji jest przekazywany bezpośrednio do **DumpStack** polecenia. **-Krótki** parametr ogranicza dane wyjściowe do następujące rodzaje wątków:<br /><br /> Wątki, które uzyskały blokadę.<br /><br /> Wątki, które zostały zatrzymane w celu umożliwienia odśmiecenia pamięci.<br /><br /> Wątki, które są obecnie w kodzie zarządzanym.|  
|**EEVersion**|Wyświetla wersję środowiska uruchomieniowego języka wspólnego.|  
|**EHInfo** [\<*adres MethodDesc*>] [\<*kod adres*>]|Wyświetla bloki obsługi wyjątków w określonej metodzie.  To polecenie wyświetla adresy kodu i przesunięcia bloku klauzuli ( `try` bloku) i bloku obsługi ( `catch` bloku).|  
|**FAQ**|Wyświetla najczęściej zadawane pytania.|  
|**FinalizeQueue** [**— szczegóły**] &#124; [**- allReady**] [**-krótki**]|Wyświetla wszystkie obiekty zarejestrowane dla finalizacji.<br /><br /> **— Szczegóły** opcja wyświetla dodatkowe informacje o `SyncBlocks` wymagających na oczyszczenie i wszystkie `RuntimeCallableWrappers` (RCWs) który await oczyszczania. Obie te struktury danych są buforowane i oczyszczane przez wątek finalizatora w trakcie jego działania.<br /><br /> `-allReady` Opcja wyświetla wszystkie obiekty, które są gotowe do finalizacji, niezależnie od tego, czy są już oznaczane jako takie wyrzucanie elementów bezużytecznych, czy zostaną oznaczone przez dalej wyrzucanie elementów bezużytecznych. Obiekty, które znajdują się na liście „gotowych do finalizacji”, są obiektami, które można sfinalizować i które nie są już zakorzenione. Ta opcja może być bardzo kosztowna, ponieważ weryfikuje, czy wszystkie obiekty w kolejkach, które można sfinalizować, są nadal zakorzenione.<br /><br /> `-short` Opcja ogranicza dane wyjściowe do adresu każdego obiektu. Jeśli jest on używany w połączeniu z **- allReady**, jego wylicza wszystkie obiekty, które ma finalizator, które już są osadzone. Jeśli jest używana samodzielnie, wyświetla listę wszystkich obiektów w kolejkach możliwych do sfinalizowania i „gotowych do finalizacji”.|  
|**FindAppDomain** \< *obiekt adresu*>|Określa domenę aplikacji obiektu pod podanym adresem.|  
|**FindRoots** **-gen** \< *N*> &#124; **-gł żadnego** &#124;\< *obiekt adresu*>|Powoduje przerwanie debugowania w obiekcie debugowanym podczas kolejnego zbierania dla określonej generacji. Efekt jest resetowany natychmiast po wystąpieniu przerwania. Aby przerwać podczas kolejnego zbierania, należy ponownie wydać polecenie.  *\<Obiekt adres >* forma to polecenie jest używana po podziale spowodowane **-gen** lub **-gł żadnego** wystąpił. W tym czasie obiekt debugowany znajduje się w stanie prawo **FindRoots** do identyfikowania katalogów głównych dla obiektów z bieżącego potępiła generacji.|  
|**Związane** [**- perdomain**]|Wyświetla statystyki dotyczące uchwytów modułu odśmiecania pamięci w procesie.<br /><br /> **- Perdomain** opcji rozmieszcza statystyk według domeny aplikacji.<br /><br /> Użyj **związane** polecenie, aby znaleźć spowodowane przez moduł zbierający elementy bezużyteczne dojścia przecieki przecieki pamięci. Przykładowo wyciek pamięci występuje, gdy kod zachowuje dużą tablicę, ponieważ silny uchwyt modułu odśmiecania pamięci nadal na nią wskazuje, a uchwyt został odrzucony bez jej zwolnienia.|  
|**GCHandleLeaks**|Wyszukuje w pamięci dowolnych odwołań do silnych i przypiętych uchwytów modułu odśmiecania pamięci w procesie i wyświetla wyniki. Jeśli zostanie znaleziony uchwytu, **GCHandleLeaks** polecenie wyświetla adres odwołania. Jeśli uchwyt nie zostanie znaleziony w pamięci, polecenie wyświetli powiadomienie.|  
|**GCInfo** \< *adres MethodDesc*>\<*kod adres*>|Wyświetla dane, które wskazują, kiedy rejestry lub lokalizacje stosu zawierają obiekty zarządzane. Jeśli występuje odśmiecanie pamięci, moduł musi znać lokalizacje odwołań do obiektów, aby móc je zaktualizować za pomocą nowych wartości wskaźnika obiektu.|  
|**GCRoot** [**- nostacks**] \< *obiekt adresu*>|Wyświetla informacje dotyczące odwołań (lub korzeni) do obiektu pod podanym adresem.<br /><br /> **GCRoot** polecenie sprawdza cały sterty zarządzanej i tabeli dojścia dojść w innych obiektów i obsługuje na stosie. Każdy stos jest następnie przeszukiwany w celu znalezienia wskaźników do obiektów; kolejka finalizatorów również będzie przeszukiwana.<br /><br /> To polecenie nie określa, czy korzeń stosu jest nieprawidłowy lub odrzucony. Użyj **CLRStack** i **U** poleceń do ramki, w której wartość lokalnego lub argumentu, należy w celu ustalenia, czy główny stos jest nadal używany przekształcenia.<br /><br /> **- Nostacks** opcji ogranicza wyszukiwanie do modułu zbierającego elementy bezużyteczne dojść i freachable obiektów.|  
|**GCWhere***\<obiekt adres >* |Wyświetla lokalizację i rozmiar przekazanego argumentu w stercie modułu odśmiecania pamięci. Gdy argument znajduje się w stercie zarządzanej, ale nie jest prawidłowym adresem obiektu, rozmiar zostanie wyświetlony jako 0 (zero).|  
|**Pomoc** [\<*polecenia*>] [`faq`]|Wyświetla wszystkie dostępne polecenia, gdy parametr nie jest określony, lub wyświetla szczegółowe informacje pomocy dotyczące określonego polecenia.<br /><br /> `faq` Parametr wyświetla odpowiedzi na często zadawane pytania.|  
|**HeapStat** [**- inclUnrooted** &#124; **-iu**]|Wyświetla rozmiary generacji dla każdej sterty i całkowitą ilość wolnego miejsca w każdej generacji na każdym stosie. Jeśli**inclUnrooted** opcji jest określony, raport zawiera informacje o zarządzanych obiektach ze stosu kolekcji pamięci, który nie jest ścieżką do katalogu głównego.|  
|**HistClear**|Zwalnia wszelkie zasoby używane przez rodziny `Hist` poleceń.<br /><br /> Ogólnie rzecz biorąc, nie trzeba jawnie wywołać `HistClear`, ponieważ każdy `HistInit` czyści poprzednie zasobów.|  
|**HistInit**|Inicjuje struktury SOS z dziennika obciążenia zapisanego w obiekcie debugowanym.|  
|**HistObj** *< obj_address >*|Sprawdza wszystkie rekordy przeniesienia dziennika obciążenia i wyświetla łańcuch przeniesień modułu odśmiecania pamięci, które mogły doprowadzić do adresu przekazanego jako argument.|  
|**HistObjFind***< obj_address >* |Wyświetla wszystkie wpisy dziennika, które odwołują się do obiektu pod podanym adresem.|  
|**HistRoot**  *\<główny >*|Wyświetla informacje powiązane zarówno z promocjami, jak i przeniesieniami określonego korzenia.<br /><br /> Wartość korzenia może być użyta do śledzenia ruchu obiektu za pomocą modułu odśmiecania pamięci.|  
|**IP2MD** \< *kod adres*>|Wyświetla `MethodDesc` struktury pod określonym adresem w kodzie, która została skompilowana JIT.|  
|`ListNearObj`(`lno`) *< obj_address >*|Wyświetla obiekty poprzedzające i następujące po określonym adresie. Polecenie wyszukuje adres w stercie modułu odśmiecania pamięci podobny do prawidłowego początku obiektu zarządzanego (na podstawie prawidłowej metody tabel) i obiektu następującego po adresie argumentu.|  
|**MinidumpMode** [**0**] [**1**]|Uniemożliwia uruchamianie poleceń niebezpiecznych podczas używania minizrzutu.<br /><br /> Przekaż **0** Aby wyłączyć tę funkcję lub **1** Aby włączyć tę funkcję. Domyślnie **MinidumpMode** ma wartość **0**.<br /><br /> Minizrzutów utworzone za pomocą **.dump /m** polecenia lub **.dump** polecenia mają ograniczoną dane specyficzne dla środowiska CLR i pozwala na uruchamianie tylko podzestaw poleceń SOS poprawnie. Niektóre polecenia mogą zakończyć się nieoczekiwanym błędem, ponieważ wymagane obszary pamięci nie są mapowane lub są tylko częściowo mapowane. Ta opcja chroni przed uruchamianiem poleceń niebezpiecznych w stosunku do minizrzutów.|  
|**Name2EE** \< *nazwy modułu*> \<*nazwy typu lub metody*><br /><br /> —lub—<br /><br /> **Name2EE** \< *nazwy modułu*>**!** \< *nazwy typu lub metody*>|Wyświetla `MethodTable` struktury i `EEClass` struktury dla określonego typu lub metody w określonym module.<br /><br /> Określony moduł musi zostać załadowany w procesie.<br /><br /> Można pobrać nazwy odpowiedniego typu, przeglądać modułu przy użyciu [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md). Można również przekazać `*` jako moduł parametru nazwy do wyszukania wszystkich załadowanych modułów zarządzanych. *Nazwy modułu* parametru można też debugera nazwę modułu, takich jak `mscorlib` lub `image00400000`.<br /><br /> To polecenie obsługuje składnia debugera systemu Windows <`module`>`!`<`type`>. Typ musi być w pełni kwalifikowany.|  
|**ObjSize** [\<*obiekt adres*>] &#124; [**— łączny**] [**-stat**]|Wyświetla rozmiar określonego obiektu. Jeśli nie określono żadnych parametrów, **ObjSize** polecenie wyświetla rozmiar wszystkich znalezionych w zarządzanych wątkach, wyświetla wszystkie dojścia modułu zbierającego elementy bezużyteczne procesu i sumy rozmiaru elementów wskazywana przez uchwytów. **ObjSize** polecenie zawiera rozmiar wszystkich obiektów podrzędnych oprócz obiektu nadrzędnego.<br /><br /> **— Łączny** opcji można użyć w połączeniu z **-stat** argumentu, aby uzyskać szczegółowy widok typy, które nadal są osadzone. Za pomocą **! dumpheap-stat** i **! objsize-agregacji - stat**, można określić obiekty, które już są umieszczone i diagnozowanie różne problemy z pamięcią.|  
|**PrintException** [**-zagnieżdżonych**] [**-wiersze**] [\<*adres obiektu wyjątku*>]<br /><br /> —lub—<br /><br /> **PE** [**-zagnieżdżonych**] [\<*adres obiektu wyjątku*>]|Wyświetla i formaty pól obiektu pochodną <xref:System.Exception> klasy pod określonym adresem. Jeśli nie określisz adresu **PrintException** polecenie wyświetla ostatniego wyjątek w bieżącym wątku.<br /><br /> **-Zagnieżdżonych** opcja wyświetla szczegółowe informacje o obiektach zagnieżdżonych wyjątku.<br /><br /> **-Wiersze** opcja wyświetla informacje o źródle, jeśli jest dostępna.<br /><br /> Możesz użyć tego polecenia i widoku `_stackTrace` pola, które jest tablicą binarnego.|  
|**ProcInfo** [**- env**] [**— czas**] [**-mem**]|Wyświetla zmienne środowiskowe dla procesu, czasu procesora dla jądra i statystyki użycia pamięci.|  
|**RCWCleanupList** \< *RCWCleanupList adresu*>|Wyświetla listę otok wywoływanych w czasie wykonywania pod określonym adresem, które czekają na oczyszczanie.|  
|**SaveModule** \< *adres bazowy*> \<*Filename*>|Zapisuje określony obraz, który jest załadowany do pamięci pod podanym adresem, do określonego pliku.|  
|**SOSFlush**|Opróżnia wewnętrzną pamięć podręczną SOS.|  
|**StopOnException** [**-pochodnych**] [**— tworzenie** &#124; **-create2**] \< *wyjątek*> \<*pseudorejestr numer*>|Powoduje zatrzymanie debugera, gdy określony wyjątek zostanie zgłoszony, ale kontynuuje działanie, gdy zgłaszane są inne wyjątki.<br /><br /> **-Pochodnych** opcji połowy określonego wyjątku i co wyjątek, który pochodzi z określonym wyjątkiem.|  
|**SyncBlk** [**— wszystkie** &#124; \< *numer syncblk*>]|Wyświetla określony `SyncBlock` struktura lub wszyscy `SyncBlock` struktury.  Jeśli wszystkie argumenty nie są przekazywane **SyncBlk** polecenie wyświetla `SyncBlock` struktury odpowiadający obiektów, które należą do firmy przez wątek.<br /><br /> A `SyncBlock` struktury jest kontenerem, aby uzyskać dodatkowe informacje, które nie muszą zostać utworzone dla każdego obiektu. Może przechowywać dane międzyoperacyjnego modelu COM, kody skrótów i informacje dotyczące blokowania na potrzeby operacji bezpiecznych wątkowo.|  
|**Puli wątków**|Wyświetla informacje o puli wątków zarządzanych, w tym liczbę żądań pracy w kolejce, liczbę wątków portu zakończenia i liczbę czasomierzy.|  
|**Token2EE** \< *nazwy modułu*> \<*tokenu*>|Włącza tokenu w określonym module w określonych metadanych `MethodTable` struktury lub `MethodDesc` struktury.<br /><br /> Można przekazać `*` dla parametru nazwy modułu można znaleźć tokenu mapowany na, w każdym załadowany moduł zarządzany. Można również przekazać debugera nazwę modułu, takich jak `mscorlib` lub `image00400000`.|  
|**Wątki** [**-live**] [**-specjalne**]|Wyświetla wszystkie zarządzane wątki w procesie.<br /><br /> **Wątków** polecenie wyświetla debugera identyfikator skrócona, wspólny identyfikator wątku czasu wykonywania języka i identyfikator wątku systemu operacyjnego.  Ponadto **wątków** polecenie wyświetla domeny kolumny, która wskazuje domeny aplikacji, w którym jest wykonywany przez wątek, stanie kolumny, która wyświetla tryb apartamentu COM i wyświetlana ostatnia kolumna wyjątku wyjątek w wątku.<br /><br /> **-Live** opcja powoduje wyświetlenie wątki skojarzone z wątkiem na żywo.<br /><br /> **-Specjalne** opcja wyświetla wszystkie wątki specjalne utworzone przez środowisko CLR. Specjalne wątków obejmują wątków kolekcji pamięci (w pamięci równoczesnych i server), debuger pomocnika wątków, wątki finalizator <xref:System.AppDomain> zwolnić wątków i wątków z puli wątków czasomierza.|  
|**ThreadState \<**  *pola wartość stanu***>**|Wyświetla stan wątku. `value` Parametr ma wartość `State` w **wątków** raportu wyjściowego.<br /><br /> Przykład:<br /><br /> `0:003> !Threads     ThreadCount:      2     UnstartedThread:  0     BackgroundThread: 1     PendingThread:    0     DeadThread:       0     Hosted Runtime:   no                                           PreEmptive   GC Alloc           Lock            ID OSID ThreadOBJ    State     GC       Context       Domain   Count APT Exception        0    1  250 0019b068      a020 Disabled 02349668:02349fe8 0015def0     0 MTA        2    2  944 001a6020      b220 Enabled  00000000:00000000 0015def0     0 MTA (Finalizer)     0:003> !ThreadState b220         Legal to Join         Background         CLR Owns         CoInitialized         In Multi Threaded Apartment`|  
|**TraverseHeap** [**- xml**] \< *filename*>|Zapisuje informacje dotyczące sterty do określonego pliku w formacie zrozumiałym dla profilera CLR. **- Xml** opcji powoduje, że **TraverseHeap** polecenia do formatowania pliku w formacie XML.<br /><br /> Możesz pobrać Profiler CLR od [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=67325).|  
|**U** [**- gcinfo**] [**- ehinfo**] [**-n**] \< *adres MethodDesc*> & # 124; \< *Kod adres*>|Wyświetla adnotacjami dezasemblacji zarządzana metoda określona przez `MethodDesc` wskaźnik struktury dla metody lub przez kod adres w treści metody. **U** polecenie wyświetla całą metodę od początku do końca, przy użyciu adnotacji, które Konwertuj tokenów metadanych na nazwy.<br /><br /> **- Gcinfo** opcji powoduje, że **U** polecenie, aby wyświetlić `GCInfo` struktury dla metody.<br /><br /> **- Ehinfo** opcja wyświetla informacje o metodzie wyjątku. Możesz również uzyskać te informacje z **EHInfo** polecenia.<br /><br />  **-n**  Opcji wyłącza wyświetlanie nazwy pliku źródłowego i numery wierszy. Jeśli opcja debugera SYMOPT_LOAD_LINES jest określona, SOS wyszukuje symbole dla każdej zarządzanej ramki i jeśli wyszukiwanie zakończy się pomyślnie, wyświetla odpowiadającą nazwę pliku źródłowego i numer wiersza. Można określić  **-n**  opcję, aby wyłączyć to zachowanie.|  
|**VerifyHeap**|Sprawdza sterty modułu odśmiecania pamięci w poszukiwaniu objawów uszkodzeń i wyświetla znalezione błędy.<br /><br /> Uszkodzenie sterty może być spowodowane przez wywołania platformy, które są konstruowane niepoprawnie.|  
|**VerifyObj** \< *obiekt adresu*>|Sprawdza, czy obiekt, który jest przekazywany jako argument posiada oznaki uszkodzenia.|  
|**VMMap**|Przechodzi wirtualną przestrzeń adresową i wyświetla typ ochrony stosowany do każdego regionu.|  
|**Polecenie VMStat**|Dostarcza widok podsumowania wirtualnej przestrzeni adresowej, uporządkowany według typów ochrony stosowanych do pamięci (wolna, zarezerwowana, zatwierdzona, prywatna, mapowana, obrazów). Kolumna TOTAL wyświetla wynik z kolumny AVERAGE pomnożony przez kolumnę BLK COUNT.|  
  
## <a name="remarks"></a>Uwagi  
 Rozszerzenie debugowania SOS pozwala wyświetlić informacje dotyczące kodu, który działa wewnątrz środowiska uruchomieniowego języka wspólnego. Przykładowo rozszerzenia debugowania SOS można użyć do wyświetlania informacji na temat zarządzanej sterty, wyszukiwania uszkodzeń sterty, wyświetlania typów danych wewnętrznych używanych przez środowisko uruchomieniowe i wyświetlania informacji o całym zarządzanym kodzie działającym wewnątrz środowiska uruchomieniowego.  
  
 Aby użyć rozszerzenia debugowania SOS w programie Visual Studio, zainstalować [zestaw sterowników systemu Windows (WDK)](http://msdn.microsoft.com/windows/hardware/hh852362). Aby uzyskać informacje o zintegrowane środowisko debugowania w programie Visual Studio, zobacz [debugowania środowiska](http://msdn.microsoft.com/library/windows/hardware/hh406268.aspx) w Centrum deweloperów systemu Windows.  
  
 Umożliwia również rozszerzenie debugowania SOS przez załadowanie go w debugerze WinDbg.exe, który jest dostępny z [witrynie WDK i Developer Tools](http://go.microsoft.com/fwlink/?LinkId=103787)i wykonywania poleceń w WinDbg.exe.  
  
 Aby załadować rozszerzenie debugowania SOS do debugera WinDbg.exe, należy uruchomić następujące polecenie w narzędziu:  
  
```  
.loadby sos clr  
```  
  
 WinDbg.exe i program Visual Studio używają wersji SOS.dll, która odpowiada aktualnie używanej wersji Mscorwks.dll. W wersji 1.1 i 2.0 .NET Framework, SOS.dll jest zainstalowany w tym samym katalogu co Mscorwks.dll. Domyślnie należy użyć wersji programu SOS.dll, który odpowiada aktualnej wersji Mscorwks.dll.  
  
 Aby użyć pliku zrzutu utworzonego na innym komputerze, należy upewnić się, że plik Mscorwks.dll dodany podczas instalacji znajduje się w ścieżce symbolu i załadować odpowiadającą wersję SOS.dll.  
  
 Aby załadować określoną wersję SOS.dll, należy wpisać następujące polecenie w debugerze systemu Windows:  
  
```  
.load <full path to sos.dll>  
```  
  
## <a name="examples"></a>Przykłady  
 Polecenie wyświetla zawartość tablicy pod adresem `00ad28d0`.  Wyświetlanie zaczyna się od drugiego elementu, a następnie wyświetlonych zostaje pięć kolejnych elementów.  
  
```  
!dumparray -start 2 -length 5 -detail 00ad28d0   
```  
  
 Polecenie wyświetla zawartość zestawu pod adresem `1ca248`.  
  
```  
!dumpassembly 1ca248  
```  
  
 Następujące polecenie wyświetla informacje o stercie modułu odśmiecania pamięci.  
  
```  
!dumpheap  
```  
  
 Następujące polecenie zapisuje zawartość dziennika obciążenia pamięci do pliku (domyślnego) o nazwie StressLog.txt w bieżącym katalogu.  
  
```  
!DumpLog  
```  
  
 Następujące polecenie wyświetla `MethodDesc` struktury pod adresem `902f40`.  
  
```  
!dumpmd 902f40  
```  
  
 Następujące polecenie wyświetla informacje na temat modułu pod adresem `1caa50`.  
  
```  
!dumpmodule 1caa50  
```  
  
 Następujące polecenie wyświetla informacje o obiektach pod adresem `a79d40`.  
  
```  
!DumpObj a79d40  
```  
  
 Następujące polecenie wyświetla pola klasy wartości pod adresem `00a79d9c` przy użyciu tabeli Metoda pod adresem `0090320c`.  
  
```  
!DumpVC 0090320c 00a79d9c  
```  
  
 Następujące polecenie wyświetla pamięć procesu używaną przez moduł odśmiecania pamięci.  
  
```  
!eeheap -gc  
```  
  
 Następujące polecenie wyświetla wszystkie obiekty zaplanowane do finalizacji.  
  
```  
!finalizequeue  
```  
  
 Polecenie Określa domeny aplikacji obiektu pod adresem `00a79d98`.  
  
```  
!findappdomain 00a79d98  
```  
  
 Następujące polecenie wyświetla wszystkie uchwyty modułu odśmiecania pamięci w bieżącym procesie.  
  
```  
!gcinfo 5b68dbb8   
```  
  
 Następujące polecenie wyświetla `MethodTable` i `EEClass` struktur `Main` metody w klasie `MainClass` w module `unittest.exe`.  
  
```  
!name2ee unittest.exe MainClass.Main  
```  
  
 Polecenie wyświetla informacje o tokenie metadanych pod adresem `02000003` w module `unittest.exe`.  
  
```  
!token2ee unittest.exe 02000003  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
