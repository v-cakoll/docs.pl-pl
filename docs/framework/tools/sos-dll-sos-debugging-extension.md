---
title: SOS.dll (rozszerzenie do debugowania SOS)
ms.date: 03/30/2017
helpviewer_keywords:
- debugging extensions
- SOS debugging extensions
- SOS.dll
ms.assetid: 9ac1b522-77ab-4cdc-852a-20fcdc9ae498
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c038b66e4ed62d614a25e717c52fdcc9c5f9a23
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44208838"
---
# <a name="sosdll-sos-debugging-extension"></a>SOS.dll (rozszerzenie do debugowania SOS)
Rozszerzenie debugowania SOS (SOS.dll) ułatwia debugowanie programów zarządzanych w programie Visual Studio i w debugerze Windows (WinDbg.exe) poprzez dostarczanie informacji na temat wewnętrznego środowiska środowiska uruchomieniowego języka wspólnego (CLR). To narzędzie wymaga włączenia debugowania niezarządzanego w projekcie. SOS.dll jest automatycznie instalowany z .NET Framework. Aby użyć SOS.dll w programie Visual Studio, zainstaluj [Windows Driver Kit (WDK)](https://msdn.microsoft.com/windows/hardware/hh852362).  
  
> [!NOTE]
>  Jeśli używasz [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], SOS.dll jest obsługiwany w debugerze Windows w programie Visual Studio, ale nie znajduje się w oknie bezpośrednim debugera programu Visual Studio.  
  
## <a name="syntax"></a>Składnia  
  
```  
![command] [options]   
```  
  
## <a name="commands"></a>Polecenia  
  
|Polecenie|Opis|  
|-------------|-----------------|  
|**AnalyzeOOM** (**ao**)|Wyświetla informacje o ostatnim OOM, który wystąpił w żądaniu alokacji w stercie modułu odśmiecania pamięci. (W module odśmiecania pamięci dla serwera wyświetla OOM, jeżeli wystąpił, dla każdej sterty modułu odśmiecania pamięci.)|  
|**BPMD** [**- nofuturemodule**] [\<*Nazwa modułu*> \<*nazwę metody*>] [**- md**   < `MethodDesc`>] **— lista** **-wyczyść** \< *oczekujące numer punktu przerwania* >  **- clearall**|Tworzy punkt przerwania w określonej metodzie w określonym module.<br /><br /> Jeśli określony moduł i metoda nie zostały załadowane, to polecenie czeka na powiadomienie, że moduł został załadowany i skompilowany „just in time” (JIT) przed utworzeniem punktu przerwania.<br /><br /> Lista oczekujących punktów przerwania można zarządzać za pomocą **— lista**, **-wyczyść**, i **- clearall** opcje:<br /><br /> **— Lista** opcja generuje listę wszystkich oczekujących punktów przerwania. Jeśli oczekujący punkt przerwania ma niezerowy identyfikator modułu, ten punkt przerwania jest właściwy dla funkcji w tym określonym załadowanym module. Jeśli oczekujący punkt przerwania ma zerowy identyfikator modułu, ten punkt przerwania ma zastosowanie do modułów, które nie zostały jeszcze załadowane.<br /><br /> Użyj **-wyczyść** lub **- clearall** opcję, aby usunąć oczekujące punkty przerwania z listy.|  
|**CLRStack** [**-**] [**-l**] [**-p**] [**- n**]|Dostarcza ślad stosu wyłącznie dla kodu zarządzanego.<br /><br /> **-P** opcji wyświetla argumenty dla funkcji zarządzanej.<br /><br /> **-L** opcja umożliwia pokazanie informacji o zmiennych lokalnych w ramce. Rozszerzenie debugowania SOS nie można pobrać nazw lokalnych, dlatego wyjściowe nazwy lokalne, jest w formacie \< *adresów lokalnych* >  **=** \< *wartość*>.<br /><br /> **-**(Wszystkie) opcja jest skrót **-l** i **-p**połączone.<br /><br /> **- N** opcji wyłącza wyświetlanie nazw plików źródłowych i numerów wierszy. Jeśli opcja debugera SYMOPT_LOAD_LINES jest określona, SOS będzie wyszukiwać symbole dla każdej ramki zarządzanej i jeśli wyszukiwanie zakończy się pomyślnie, wyświetlona zostanie odpowiadająca nazwa pliku źródłowego i numer wiersza. **- N** (bez numerów wierszy) można określić parametr, aby wyłączyć to zachowanie.<br /><br /> Rozszerzenie debugowania SOS nie wyświetla ramek przejścia na platformach opartych o procesory x64 i IA-64.|  
|**COMState**|Wyświetla model przedziału COM dla każdego wątku i `Context` wskaźnik, jeśli jest dostępny.|  
|**DumpArray** [**-start** \< *startIndex*>] [**— długość** \< *długość*>] [ **— szczegóły**] [**- nofields**] \< *adres obiektu array*><br /><br /> —lub—<br /><br /> **Akcelerator deweloperski w wersji** [**-start** \< *startIndex*>] [**— długość** \< *długość*>] [**— szczegóły**] [**- nofields**] *adres obiektu array*>|Sprawdza elementy obiektu tablicowego.<br /><br /> **-Start** opcja określa początkowy indeks, od którego należy wyświetlić elementy.<br /><br /> **— Długość** opcja określa, ile elementów do wyświetlenia.<br /><br /> **— Szczegóły** opcji Wyświetla szczegóły elementu za pomocą **DumpObj** i **DumpVC** formatów.<br /><br /> **- Nofields** opcji uniemożliwia wyświetlanie tablic. Ta opcja jest dostępna tylko wtedy, gdy **— szczegóły** określono opcję.|  
|**DumpAssembly** \< *adres zestawu*>|Wyświetla informacje o zestawie.<br /><br /> **DumpAssembly** polecenie wyświetla wiele modułów, jeśli takie istnieją.<br /><br /> Adres zestawu można uzyskać za pomocą **DumpDomain** polecenia.|  
|**DumpClass** \< *EEClass adresu*>|Przedstawia informacje na temat `EEClass` skojarzony z typem struktury.<br /><br /> **DumpClass** polecenie wyświetla wartości pól statycznych, ale nie wyświetla wartości pól niestatycznych.<br /><br /> Użyj **DumpMT**, **DumpObj**, **Name2EE**, lub **Token2EE** polecenie, aby uzyskać `EEClass` adres struktury.|  
|**DumpDomain** [\<*adresu domeny*>]|Wylicza każdy <xref:System.Reflection.Assembly> obiekt załadowany w ramach określonych <xref:System.AppDomain> adresu obiektu.  Gdy zostanie wywołana bez parametrów **DumpDomain** polecenie wyświetla listę wszystkich <xref:System.AppDomain> obiektów w procesie.|  
|**DumpHeap** [**-stat**] [**— ciągi**] [**— krótki**] [**-minutowy** \< *rozmiar*>] [**-max** \< *rozmiar*>] [**- thinlock**] [**- startAtLowerBound**] [**- mt** \< *adres MethodTable*>] [**— typ** \< *nazwy typu częściowego*>] [*start* [*zakończenia*]]|Wyświetla informacje dotyczące sterty zebranej podczas odśmiecania pamięci i statystyk odśmiecania w stosunku do obiektów.<br /><br /> **DumpHeap** polecenie wyświetli ostrzeżenie, jeśli wykryje nadmierną fragmentację w stercie modułu odśmiecania pamięci.<br /><br /> **-Stat** opcja ogranicza dane wyjściowe do statystycznego podsumowania typu.<br /><br /> **— Ciągi** opcja ogranicza dane wyjściowe do statystycznego podsumowania wartości ciągu.<br /><br /> **— Krótki** opcji ogranicza dane wyjściowe tylko do adresu każdego obiektu. Dzięki temu można łatwo strumieniować dane wyjściowe z polecenia do innego polecenia debugera w celu automatyzacji.<br /><br /> **-Minutowy** opcja ignoruje obiekty, które mają mniej niż `size` parametr podany w bajtach.<br /><br /> **-Max** opcja ignoruje obiekty, które są większe niż `size` parametr podany w bajtach.<br /><br /> **- Thinlock** opcji raportuje ThinLocks.  Aby uzyskać więcej informacji, zobacz **SyncBlk** polecenia.<br /><br /> `-startAtLowerBound` Opcja wymusza na stercie, aby rozpocząć dolnej granicy podanego zakresu adresów. Podczas fazy planowania sterta często nie posiada funkcji przechodzenia, ponieważ obiekty są przenoszone. Ta opcja wymusza **DumpHeap** rozpoczęcie przechodzenia w określonej dolnej granicy. Należy podać adres prawidłowego obiektu jako dolną granicę, aby ta opcja działała. Można wyświetlić pamięć pod adresem błędnego obiektu, aby ręcznie odnaleźć następną tabelę metod. Jeśli wyrzucanie elementów bezużytecznych jest obecnie dostępna w wywołaniu `memcopy`, również można znaleźć adres następnego obiektu przez dodanie rozmiaru do adresu początkowego, który jest dostarczany jako parametr.<br /><br /> **- Mt** opcji wyświetla tylko te obiekty, które odpowiadają określonej `MethodTable` struktury.<br /><br /> **— Typ** opcji wyświetla tylko te obiekty, których nazwa typu jest podciągiem odpowiadającym określonemu ciągowi.<br /><br /> `start` Parametru rozpoczyna wyświetlanie listy od określonego adresu.<br /><br /> `end` Parametr zatrzymuje wyświetlanie listy pod podanym adresem.|  
|**DumpIL** \< *obiektu zarządzanego elementu DynamicMethod*> &#124; \< *wskaźnik DynamicMethodDesc*> &#124; \<  *Wskaźnik MethodDesc*>|Wyświetla język pośredni Microsoft (MSIL) skojarzony z zarządzaną metodą.<br /><br /> Należy zauważyć, że dynamiczny MSIL jest emitowany inaczej od MSIL, który jest ładowany z zestawu. Dynamiczny MSIL odnosi się do obiektów w tablicy obiektu zarządzanego, a nie do tokenów metadanych.|  
|**DumpLog** [**- addr** \< *addressOfStressLog*>] [<*Filenam*`e`>]|Zapisuje zawartość dziennika obciążenia pamięci do określonego pliku. Jeśli nazwa nie zostanie określona, polecenie tworzy plik o nazwie StressLog.txt w bieżącym katalogu.<br /><br /> Dziennik obciążenia pamięci pomaga w diagnozowaniu błędów obciążenia pamięci bez używania blokad lub we/wy. Aby włączyć dziennik obciążenia, należy ustawić następujące klucze rejestru w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework:<br /><br /> (DWORD) StressLog = 1<br /><br /> (DWORD) LogFacility = 0xffffffff<br /><br /> (DWORD) StressLogSize = 65536<br /><br /> Opcjonalny `-addr` opcja umożliwia określenie dziennika obciążenia innego niż domyślny dziennik.|  
|**DumpMD** \< *MethodDesc adresu*>|Przedstawia informacje na temat `MethodDesc` struktury pod podanym adresem.<br /><br /> Możesz użyć **IP2MD** polecenie, aby uzyskać `MethodDesc` adres z funkcji zarządzanej struktury.|  
|**DumpMT** [**-MD**] \< *MethodTable adresu*>|Wyświetla informacje dotyczące tabeli metod pod podanym adresem. Określanie **-MD** opcji powoduje wyświetlenie listy wszystkich metod, zdefiniowanych za pomocą obiektu.<br /><br /> Każdy obiekt zarządzany zawiera wskaźnik tabeli metod.|  
|**DumpMethodSig** \< *sigaddr*><*moduleadd*`r`>|Przedstawia informacje na temat `MethodSig` struktury pod podanym adresem.|  
|**DumpModule** [**- mt**] \< *adres modułu*>|Wyświetla informacje dotyczące modułu pod podanym adresem. **- Mt** opcji Wyświetla typy zdefiniowane w module i typy określone przez moduł<br /><br /> Możesz użyć **DumpDomain** lub **DumpAssembly** polecenie, aby pobrać adres modułu.|  
|**DumpObj** [**- nofields**] \< *adresu obiektu*><br /><br /> —lub—<br /><br /> **CZY** \< *adresu obiektu*>|Wyświetla informacje dotyczące obiektu pod podanym adresem. **DumpObj** polecenie wyświetla pola, `EEClass` struktury informacje, tabelę metod i rozmiar obiektu.<br /><br /> Możesz użyć **DumpStackObjects** polecenie, aby pobrać adres obiektu.<br /><br /> Należy zauważyć, że można uruchomić **DumpObj** na pola typu polecenia `CLASS` ponieważ także są obiektami.<br /><br /> `-` **Nofields** opcja uniemożliwia pól obiektu są wyświetlane, jest to przydatne dla obiektów, takich jak ciągi.|  
|**DumpRuntimeTypes**|Wyświetla obiekty typu środowiska uruchomieniowego w stercie modułu odśmiecania pamięci i wyświetla ich nazwy skojarzonych typów i tabele metod.|  
|**DumpStack** [**- EE**] [**- n**] [`top` *stosu* [`bottom` *ń*`k`]]|Wyświetla ślad stosu.<br /><br /> **- EE** opcji powoduje, że **DumpStack** polecenie, aby wyświetlić tylko funkcje zarządzane. Użyj `top` i `bottom` parametry do ograniczenia ramek stosu wyświetlanych na x86 platform.<br /><br /> **- N** opcji wyłącza wyświetlanie nazw plików źródłowych i numerów wierszy. Jeśli opcja debugera SYMOPT_LOAD_LINES jest określona, SOS będzie wyszukiwać symbole dla każdej ramki zarządzanej i jeśli wyszukiwanie zakończy się pomyślnie, wyświetlona zostanie odpowiadająca nazwa pliku źródłowego i numer wiersza. **- N** (bez numerów wierszy) można określić parametr, aby wyłączyć to zachowanie.<br /><br /> Na x86 i x64 64 **DumpStack** polecenie tworzy pełny ślad stosu.<br /><br /> Na platformach komputerów z procesorami IA-64 **DumpStack** naśladuje polecenie debugera **K** polecenia. `top` i `bottom` parametry są ignorowane na platformach komputerów z procesorami IA-64.|  
|**DumpSig** \< *sigaddr*> \<*moduleaddr*>|Przedstawia informacje na temat `Sig` struktury pod podanym adresem.|  
|**DumpSigElem** \< *sigaddr*> \<*moduleaddr*>|Wyświetla jeden element obiektu podpisu. W większości przypadków należy używać **DumpSig** spojrzeć na poszczególnych obiektów. Jednak jeśli podpis została uszkodzona w jakiś sposób, możesz użyć **DumpSigElem** do odczytu jego prawidłowych fragmentów.|  
|**DumpStackObjects** [**— Sprawdź**] [`top` *stosu* [`bottom` *stosu*]]<br /><br /> —lub—<br /><br /> **DSO** [**— Sprawdź**] [`top` *stosu* [`bottom` *stosu*]]|Wyświetla wszystkie zarządzane obiekty znalezione w granicach bieżącego stosu.<br /><br /> **— Sprawdź** opcja sprawdza poprawność każdego niestatycznego `CLASS` pole pola obiektu.<br /><br /> Użyj **DumpStackObject** polecenia z poleceniami śledzenia stosu, taki jak **K** polecenia i **CLRStack** polecenie, aby określić wartości zmiennych lokalnych i Parametry.|  
|**DumpVC** \< *adres MethodTable*> \<*adresu*>|Wyświetla informacje dotyczące pól klasy wartości pod podanym adresem.<br /><br /> **MethodTable** parametr umożliwia **DumpVC** polecenie, aby poprawnie interpretowanie pola. Klasy wartości nie posiadają tabeli metod jako ich pierwsze pole.|  
|**EEHeap** [**-gc**] [**— moduł ładujący**]|Wyświetla informacje dotyczące zużywanej pamięci procesu przez wewnętrzne struktury danych środowiska CLR.<br /><br /> **-Gc** i **— moduł ładujący** opcje ograniczają dane wyjściowe tego polecenia do struktur danych modułu odśmiecania pamięci lub modułu ładującego.<br /><br /> Informacje dotyczące modułu odśmiecania pamięci wyświetlają zakresy każdego segmentu w zarządzanej stercie.  Jeśli wskaźnik mieści się w zakresie segmentu podanym przez **-gc**, wskaźnik jest wskaźnikiem obiektu.|  
|**EEStack** [**— krótki**] [**- EE**]|Przebiegi **DumpStack** polecenia we wszystkich wątkach w procesie.<br /><br /> **- EE** opcji jest przekazywana bezpośrednio do **DumpStack** polecenia. **— Krótki** parametr ogranicza dane wyjściowe do następujących rodzajów wątków:<br /><br /> Wątki, które uzyskały blokadę.<br /><br /> Wątki, które zostały zatrzymane w celu umożliwienia odśmiecenia pamięci.<br /><br /> Wątki, które są obecnie w kodzie zarządzanym.|  
|**EEVersion**|Wyświetla wersję środowiska CLR.|  
|**EHInfo** [\<*adres MethodDesc*>] [\<*kod adres*>]|Wyświetla bloki obsługi wyjątków w określonej metodzie.  To polecenie wyświetla adresy kodu i przesunięcia dla bloku klauzuli ( `try` bloku) i bloku obsługi ( `catch` bloku).|  
|**FAQ**|Wyświetla najczęściej zadawane pytania.|  
|**FinalizeQueue** [**— szczegóły**] &#124; [**- allReady**] [**— krótki**]|Wyświetla wszystkie obiekty zarejestrowane dla finalizacji.<br /><br /> **— Szczegóły** opcja wyświetla dodatkowe informacje dotyczące `SyncBlocks` które muszą zostać wyczyszczone, a także wszystkie `RuntimeCallableWrappers` (RCW) które czekają na oczyszczanie. Obie te struktury danych są buforowane i oczyszczane przez wątek finalizatora w trakcie jego działania.<br /><br /> `-allReady` Opcja wyświetla wszystkie obiekty, które są gotowe do finalizacji, niezależnie od tego, czy są już oznaczone przez wyrzucanie elementów bezużytecznych związku z tym, czy zostaną oznaczone podczas kolejnego odśmiecania. Obiekty, które znajdują się na liście „gotowych do finalizacji”, są obiektami, które można sfinalizować i które nie są już zakorzenione. Ta opcja może być bardzo kosztowna, ponieważ weryfikuje, czy wszystkie obiekty w kolejkach, które można sfinalizować, są nadal zakorzenione.<br /><br /> `-short` Opcja ogranicza dane wyjściowe do adresu każdego obiektu. Jeśli jest on używany w połączeniu z **- allReady**, wylicza wszystkie obiekty, które mają finalizatory, które nie są już zakorzenione. Jeśli jest używana samodzielnie, wyświetla listę wszystkich obiektów w kolejkach możliwych do sfinalizowania i „gotowych do finalizacji”.|  
|**FindAppDomain** \< *adresu obiektu*>|Określa domenę aplikacji obiektu pod podanym adresem.|  
|**FindRoots** **-gen** \< *N*> &#124; **-gen dowolne** &#124; \< *adresu obiektu*>|Powoduje przerwanie debugowania w obiekcie debugowanym podczas kolejnego zbierania dla określonej generacji. Efekt jest resetowany natychmiast po wystąpieniu przerwania. Aby przerwać podczas kolejnego zbierania, należy ponownie wydać polecenie. *\<Adresu obiektu >* formularz tego polecenia jest używany po wystąpieniu przerwania spowodowane **-gen** lub **— dowolnego ogólnego** wystąpił. W tym czasie obiekt debugowany jest w prawidłowym stanie, aby **FindRoots** zidentyfikowało korzenie obiektów z bieżących wybrakowanych generacji.|  
|**GCHandles** [**- perdomain**]|Wyświetla statystyki dotyczące uchwytów modułu odśmiecania pamięci w procesie.<br /><br /> **- Perdomain** opcji rozmieszcza statystyki według domeny aplikacji.<br /><br /> Użyj **GCHandles** polecenie, aby znaleźć wycieki pamięci spowodowane przez wycieki uchwytu modułu odśmiecania pamięci. Przykładowo wyciek pamięci występuje, gdy kod zachowuje dużą tablicę, ponieważ silny uchwyt modułu odśmiecania pamięci nadal na nią wskazuje, a uchwyt został odrzucony bez jej zwolnienia.|  
|**GCHandleLeaks**|Wyszukuje w pamięci dowolnych odwołań do silnych i przypiętych uchwytów modułu odśmiecania pamięci w procesie i wyświetla wyniki. Jeśli uchwyt zostanie znaleziony, **GCHandleLeaks** polecenie wyświetla adres odwołania. Jeśli uchwyt nie zostanie znaleziony w pamięci, polecenie wyświetli powiadomienie.|  
|**GCInfo** \< *adres MethodDesc*>\<*kod adres*>|Wyświetla dane, które wskazują, kiedy rejestry lub lokalizacje stosu zawierają obiekty zarządzane. Jeśli występuje odśmiecanie pamięci, moduł musi znać lokalizacje odwołań do obiektów, aby móc je zaktualizować za pomocą nowych wartości wskaźnika obiektu.|  
|**GCRoot** [**- nostacks**] \< *adresu obiektu*>|Wyświetla informacje dotyczące odwołań (lub korzeni) do obiektu pod podanym adresem.<br /><br /> **GCRoot** polecenie sprawdza całą zarządzaną stertę i tabelę uchwytów pod uchwytów w ramach innych obiektów i uchwytów na stosie. Każdy stos jest następnie przeszukiwany w celu znalezienia wskaźników do obiektów; kolejka finalizatorów również będzie przeszukiwana.<br /><br /> To polecenie nie określa, czy korzeń stosu jest nieprawidłowy lub odrzucony. Użyj **CLRStack** i **U** polecenia, aby zdemontować ramkę, której wartość lokalna lub argumentu, o których należy w celu określenia, czy korzeń stosu jest nadal w użyciu.<br /><br /> **- Nostacks** opcji ogranicza wyszukiwanie do uchwytów modułu odśmiecania pamięci i obiektów dostępnych dla finalizatora.|  
|**GCWhere***\<adresu obiektu >*|Wyświetla lokalizację i rozmiar przekazanego argumentu w stercie modułu odśmiecania pamięci. Gdy argument znajduje się w stercie zarządzanej, ale nie jest prawidłowym adresem obiektu, rozmiar zostanie wyświetlony jako 0 (zero).|  
|**Pomoc** [\<*polecenia*>] [`faq`]|Wyświetla wszystkie dostępne polecenia, gdy parametr nie jest określony, lub wyświetla szczegółowe informacje pomocy dotyczące określonego polecenia.<br /><br /> `faq` Parametru wyświetla odpowiedzi na często zadawane pytania.|  
|**HeapStat** [**- inclUnrooted** &#124; **-iu**]|Wyświetla rozmiary generacji dla każdej sterty i całkowitą ilość wolnego miejsca w każdej generacji na każdym stosie. Jeśli**inclUnrooted** opcja zostanie określona, raport zawiera informacje o obiektach zarządzanych ze stercie wyrzucania elementów bezużytecznych, który nie jest już zakorzeniony.|  
|**HistClear**|Zwalnia wszystkie zasoby używane przez rodzinę `Hist` poleceń.<br /><br /> Ogólnie rzecz biorąc, nie trzeba jawnie wywoływać `HistClear`, ponieważ każdy `HistInit` czyści poprzednie zasoby.|  
|**HistInit**|Inicjuje struktury SOS z dziennika obciążenia zapisanego w obiekcie debugowanym.|  
|**HistObj** *< obj_address >*|Sprawdza wszystkie rekordy przeniesienia dziennika obciążenia i wyświetla łańcuch przeniesień modułu odśmiecania pamięci, które mogły doprowadzić do adresu przekazanego jako argument.|  
|**HistObjFind***< obj_address >* |Wyświetla wszystkie wpisy dziennika, które odwołują się do obiektu pod podanym adresem.|  
|**HistRoot**  *\<główny >*|Wyświetla informacje powiązane zarówno z promocjami, jak i przeniesieniami określonego korzenia.<br /><br /> Wartość korzenia może być użyta do śledzenia ruchu obiektu za pomocą modułu odśmiecania pamięci.|  
|**IP2MD** \< *kod adres*>|Wyświetla `MethodDesc` struktury pod podanym adresem w kodzie, który został skompilowany JIT.|  
|`ListNearObj` (`lno`) *< obj_address >*|Wyświetla obiekty poprzedzające i następujące po określonym adresie. Polecenie wyszukuje adres w stercie modułu odśmiecania pamięci podobny do prawidłowego początku obiektu zarządzanego (na podstawie prawidłowej metody tabel) i obiektu następującego po adresie argumentu.|  
|**MinidumpMode** [**0**] [**1**]|Uniemożliwia uruchamianie poleceń niebezpiecznych podczas używania minizrzutu.<br /><br /> Przekaż **0** Aby wyłączyć tę funkcję lub **1** Aby włączyć tę funkcję. Domyślnie **MinidumpMode** wartość jest równa **0**.<br /><br /> Minizrzuty utworzone za pomocą **.dump /m** polecenia lub **.dump** polecenia mają ograniczone dane specyficzne dla środowiska CLR i pozwalają na poprawne uruchamianie tylko podzbioru poleceń SOS. Niektóre polecenia mogą zakończyć się nieoczekiwanym błędem, ponieważ wymagane obszary pamięci nie są mapowane lub są tylko częściowo mapowane. Ta opcja chroni przed uruchamianiem poleceń niebezpiecznych w stosunku do minizrzutów.|  
|**Name2EE** \< *Nazwa modułu*> \<*nazwy typu lub metody*><br /><br /> —lub—<br /><br /> **Name2EE** \< *Nazwa modułu*>**!** \< *nazwy typu lub metody*>|Wyświetla `MethodTable` struktury i `EEClass` struktury dla określonego typu lub metody w określonym module.<br /><br /> Określony moduł musi zostać załadowany w procesie.<br /><br /> Aby uzyskać nazwę odpowiedniego typu, należy przeglądać moduł przy użyciu [Ildasm.exe (dezasembler IL)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md). Można również przekazać `*` jako moduł parametru name, aby przeszukać wszystkie załadowane moduły zarządzane. *Nazwa modułu* parametru może być również nazwą debugera dla modułu, taką jak `mscorlib` lub `image00400000`.<br /><br /> To polecenie obsługuję składnię debuger Windows <`module`>`!`<`type`>. Typ musi być w pełni kwalifikowany.|  
|**ObjSize** [\<*adresu obiektu*>] &#124; [**— łączny**] [**-stat**]|Wyświetla rozmiar określonego obiektu. Jeśli nie określisz żadnych parametrów, **ObjSize** polecenie wyświetla rozmiar wszystkich obiektów znalezionych w zarządzanych wątkach, wyświetla wszystkie uchwyty modułu odśmiecania pamięci w procesie i sumuje rozmiar wszystkich obiektów wskazywany przez te uchwyty. **ObjSize** polecenie zawiera rozmiar wszystkich obiektów podrzędnych wraz z obiektem nadrzędnym.<br /><br /> **— Łączny** opcji można użyć w połączeniu z **-stat** argumentu, aby uzyskać szczegółowy widok typów, które nadal są zakorzenione. Za pomocą **! dumpheap-stat** i **! objsize-aggregate - stat**, można określić, które obiekty nie są już zakorzenione i diagnozować różne problemy z pamięcią.|  
|**PrintException** [**-zagnieżdżonych**] [**— linie**] [\<*adres obiektu wyjątku*>]<br /><br /> —lub—<br /><br /> **PE** [**-zagnieżdżonych**] [\<*adres obiektu wyjątku*>]|Wyświetla i formatuje pola dowolnego obiektu pochodzącego z <xref:System.Exception> klasy pod podanym adresem. Jeśli nie określisz adresu **PrintException** polecenie wyświetla ostatni wyjątek w bieżącym wątku.<br /><br /> **-Zagnieżdżonych** opcji Wyświetla szczegółowe informacje dotyczące zagnieżdżonych obiektów wyjątków.<br /><br /> **— Linie** opcji wyświetla informacje dotyczące źródła, jeśli jest dostępna.<br /><br /> Możesz użyć tego polecenia do formatowania i wyświetlania `_stackTrace` pola, które jest tablicą danych binarnych.|  
|**ProcInfo** [**- env**] [**— czas**] [**— zoptymalizowany pod kątem pamięci**]|Wyświetla zmienne środowiskowe dla procesu, czasu procesora dla jądra i statystyki użycia pamięci.|  
|**RCWCleanupList** \< *RCWCleanupList adresu*>|Wyświetla listę otok wywoływanych w czasie wykonywania pod określonym adresem, które czekają na oczyszczanie.|  
|**SaveModule** \< *adres podstawowy*> \<*nazwy pliku*>|Zapisuje określony obraz, który jest załadowany do pamięci pod podanym adresem, do określonego pliku.|  
|**SOSFlush**|Opróżnia wewnętrzną pamięć podręczną SOS.|  
|**StopOnException** [**-pochodnych**] [**— tworzenie** &#124; **-create2**] \< *wyjątek* >  \< *Numer pseudo-rejestru*>|Powoduje zatrzymanie debugera, gdy określony wyjątek zostanie zgłoszony, ale kontynuuje działanie, gdy zgłaszane są inne wyjątki.<br /><br /> **-Pochodnych** opcji przechwytuje określony wyjątek i każdy wyjątek, który pochodzi z określonego wyjątku.|  
|**SyncBlk** [**— wszystkie** &#124; \< *numer syncblk*>]|Wyświetla określoną `SyncBlock` struktura lub wszystkie `SyncBlock` struktury.  Jeśli nie przekażesz żadnych argumentów, **SyncBlk** polecenie wyświetla `SyncBlock` struktury odpowiadającą obiektom, które są własnością wątku.<br /><br /> A `SyncBlock` struktury jest kontenerem dla dodatkowych informacji, które nie muszą być tworzone dla każdego obiektu. Może przechowywać dane międzyoperacyjnego modelu COM, kody skrótów i informacje dotyczące blokowania na potrzeby operacji bezpiecznych wątkowo.|  
|**Puli wątków**|Wyświetla informacje o puli wątków zarządzanych, w tym liczbę żądań pracy w kolejce, liczbę wątków portu zakończenia i liczbę czasomierzy.|  
|**Token2EE** \< *Nazwa modułu*> \<*tokenu*>|Włącza tokenu w określonym module na określonych metadanych `MethodTable` struktury lub `MethodDesc` struktury.<br /><br /> Możesz przekazać `*` dla parametru module name dowiedzieć się, co mapuje dany token w każdym załadowanym module zarządzanym. Można również przekazać nazwę debugera dla modułu, takie jak `mscorlib` lub `image00400000`.|  
|**Wątki** [**— na żywo**] [**-specjalne**]|Wyświetla wszystkie zarządzane wątki w procesie.<br /><br /> **Wątków** polecenie wyświetla debugera skrócony identyfikator, identyfikator wątku środowiska CLR i identyfikator wątku systemu operacyjnego.  Ponadto **wątków** polecenie wyświetla kolumnę Domain wskazującą domenę aplikacji, w którym wykonywany jest wątek, kolumnę APT, w którym są wyświetlane jest tryb przedziałów COM oraz kolumnę Exception, który wyświetla ostatni wyjątek w wątku.<br /><br /> **— Na żywo** opcji wyświetla wątki skojarzone z żywym wątkiem.<br /><br /> **-Specjalne** opcja wyświetla wszystkie wątki specjalne utworzone przez środowisko CLR. Wątki specjalne obejmują wątków wyrzucania elementów bezużytecznych (w równolegle i serwer wyrzucania elementów bezużytecznych), wątki pomocnicze debugera, wątki finalizatorów, wątki <xref:System.AppDomain> wątków i wątki puli wątków czasomierza.|  
|**ThreadState \<**  *pole wartości stanu* **>**|Wyświetla stan wątku. `value` Parametr ma wartość `State` pole **wątków** danych wyjściowych raportu.<br /><br /> Przykład:<br /><br /> `0:003> !Threads     ThreadCount:      2     UnstartedThread:  0     BackgroundThread: 1     PendingThread:    0     DeadThread:       0     Hosted Runtime:   no                                           PreEmptive   GC Alloc           Lock            ID OSID ThreadOBJ    State     GC       Context       Domain   Count APT Exception        0    1  250 0019b068      a020 Disabled 02349668:02349fe8 0015def0     0 MTA        2    2  944 001a6020      b220 Enabled  00000000:00000000 0015def0     0 MTA (Finalizer)     0:003> !ThreadState b220         Legal to Join         Background         CLR Owns         CoInitialized         In Multi Threaded Apartment`|  
|**TraverseHeap** [**- xml**] \< *nazwy pliku*>|Zapisuje informacje dotyczące sterty do określonego pliku w formacie zrozumiałym dla profilera CLR. **- Xml** opcji powoduje, że **TraverseHeap** polecenie, aby sformatować plik jako XML.<br /><br /> Możesz pobrać Profiler CLR z [Microsoft Download Center](https://go.microsoft.com/fwlink/?LinkID=67325).|  
|**U** [**- gcinfo**] [**- ehinfo**] [**- n**] \< *adres MethodDesc*> &#124; \< *Kod adres*>|Wyświetla dezasemblację adnotacjami zarządzanej metody określonej przez `MethodDesc` wskaźnik struktury, metody lub przez adres kodu w treści metody. **U** polecenie wyświetla całą metodę od początku do końca z adnotacjami, które konwertują tokeny metadanych na nazwy.<br /><br /> **- Gcinfo** opcji powoduje, że **U** polecenie, aby wyświetlić `GCInfo` struktury dla metody.<br /><br /> **- Ehinfo** opcji wyświetla informacje dotyczące wyjątku dla metody. Możesz również uzyskać te informacje z **EHInfo** polecenia.<br /><br /> **- N** opcji wyłącza wyświetlanie nazw plików źródłowych i numerów wierszy. Jeśli opcja debugera SYMOPT_LOAD_LINES jest określona, SOS wyszukuje symbole dla każdej zarządzanej ramki i jeśli wyszukiwanie zakończy się pomyślnie, wyświetla odpowiadającą nazwę pliku źródłowego i numer wiersza. Można określić **- n** opcję, aby wyłączyć to zachowanie.|  
|**VerifyHeap**|Sprawdza sterty modułu odśmiecania pamięci w poszukiwaniu objawów uszkodzeń i wyświetla znalezione błędy.<br /><br /> Uszkodzenie sterty może być spowodowane przez wywołania platformy, które są konstruowane niepoprawnie.|  
|**VerifyObj** \< *adresu obiektu*>|Sprawdza, czy obiekt, który jest przekazywany jako argument posiada oznaki uszkodzenia.|  
|**VMMap**|Przechodzi wirtualną przestrzeń adresową i wyświetla typ ochrony stosowany do każdego regionu.|  
|**Polecenie VMStat**|Dostarcza widok podsumowania wirtualnej przestrzeni adresowej, uporządkowany według typów ochrony stosowanych do pamięci (wolna, zarezerwowana, zatwierdzona, prywatna, mapowana, obrazów). Kolumna TOTAL wyświetla wynik z kolumny AVERAGE pomnożony przez kolumnę BLK COUNT.|  
  
## <a name="remarks"></a>Uwagi  
 Rozszerzenie debugowania SOS pozwala wyświetlić informacje dotyczące kodu, który działa wewnątrz środowiska CLR. Przykładowo rozszerzenia debugowania SOS można użyć do wyświetlania informacji na temat zarządzanej sterty, wyszukiwania uszkodzeń sterty, wyświetlania typów danych wewnętrznych używanych przez środowisko uruchomieniowe i wyświetlania informacji o całym zarządzanym kodzie działającym wewnątrz środowiska uruchomieniowego.  
  
 Aby użyć rozszerzenia debugowania SOS w programie Visual Studio, zainstaluj [Windows Driver Kit (WDK)](https://msdn.microsoft.com/windows/hardware/hh852362). Aby uzyskać informacje na temat zintegrowanego środowiska debugowania w programie Visual Studio zobacz [środowiska debugowania](https://msdn.microsoft.com/library/windows/hardware/hh406268.aspx) w Centrum deweloperów Windows.  
  
 Można również użyć rozszerzenia debugowania SOS przez załadowanie go do debugera WinDbg.exe, który jest dostępny w [witrynie WDK i narzędzia dla deweloperów](https://go.microsoft.com/fwlink/?LinkId=103787)oraz wykonywania poleceń w ramach WinDbg.exe.  
  
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
 Następujące polecenie wyświetla zawartość tablicy pod adresem `00ad28d0`.  Wyświetlanie zaczyna się od drugiego elementu, a następnie wyświetlonych zostaje pięć kolejnych elementów.  
  
```  
!dumparray -start 2 -length 5 -detail 00ad28d0   
```  
  
 Następujące polecenie wyświetla zawartość zestawu pod adresem `1ca248`.  
  
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
  
 Następujące polecenie wyświetla informacje dotyczące modułu pod adresem `1caa50`.  
  
```  
!dumpmodule 1caa50  
```  
  
 Następujące polecenie wyświetla informacje dotyczące obiektu pod adresem `a79d40`.  
  
```  
!DumpObj a79d40  
```  
  
 Następujące polecenie wyświetla pola klasy wartości pod adresem `00a79d9c` przy użyciu tabeli metod pod adresem `0090320c`.  
  
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
  
 Następujące polecenie Określa domenę aplikacji obiektu pod adresem `00a79d98`.  
  
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
  
 Następujące polecenie wyświetla informacje dotyczące tokenu metadanych pod adresem `02000003` w module `unittest.exe`.  
  
```  
!token2ee unittest.exe 02000003  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
