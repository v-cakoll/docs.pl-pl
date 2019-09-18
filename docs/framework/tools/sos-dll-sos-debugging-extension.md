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
ms.openlocfilehash: 9a8d41228c46de0f18b5a92def0591d6373d3d69
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044098"
---
# <a name="sosdll-sos-debugging-extension"></a>SOS. dll (rozszerzenie debugowania SOS)

Rozszerzenie debugowania SOS (SOS. dll) ułatwia debugowanie programów zarządzanych w programie Visual Studio i w debugerze systemu Windows (WinDbg. exe) przez podanie informacji o środowisku uruchomieniowym języka wspólnego (CLR). To narzędzie wymaga włączenia debugowania niezarządzanego w projekcie. SOS.dll jest automatycznie instalowany z .NET Framework. Aby użyć SOS. dll w programie Visual Studio, zainstaluj [zestaw sterowników systemu Windows (WDK)](/windows-hardware/drivers/download-the-wdk).

## <a name="syntax"></a>Składnia

```console
![command] [options]
```

## <a name="commands"></a>Polecenia

|Polecenie|Opis|
|-------------|-----------------|
|**AnalyzeOOM** (**Ao**)|Wyświetla informacje na temat ostatnich braku pamięci (OOM), które wystąpiły w żądaniu alokacji do sterty wyrzucania elementów bezużytecznych. (W module odśmiecania pamięci dla serwera wyświetla OOM, jeżeli wystąpił, dla każdej sterty modułu odśmiecania pamięci.)|
|**BPMD** [ **-nofuturemodule**] [\<nazwa*metody*nazwy*modułu*>  < \<>][ **-MD** >]-list-Wyczyść oczekujący numer punktu przerwania`MethodDesc`\< >  **-ClearAll**|Tworzy punkt przerwania w określonej metodzie w określonym module.<br /><br /> Jeśli określony moduł i metoda nie zostały załadowane, to polecenie czeka na powiadomienie, że moduł został załadowany i skompilowany „just in time” (JIT) przed utworzeniem punktu przerwania.<br /><br /> Można zarządzać listą oczekujących punktów przerwania, korzystając z opcji **-list**, **-Clear**i **-ClearAll** :<br /><br /> Opcja **-list** generuje listę wszystkich oczekujących punktów przerwania. Jeśli oczekujący punkt przerwania ma niezerowy identyfikator modułu, ten punkt przerwania jest właściwy dla funkcji w tym określonym załadowanym module. Jeśli oczekujący punkt przerwania ma zerowy identyfikator modułu, ten punkt przerwania ma zastosowanie do modułów, które nie zostały jeszcze załadowane.<br /><br /> Użyj opcji **-Clear** lub **-ClearAll** , aby usunąć oczekujące punkty przerwania z listy.|
|**CLRStack** [ **-a**] [ **-l**] [ **-p**] [ **-n**]|Dostarcza ślad stosu wyłącznie dla kodu zarządzanego.<br /><br /> Opcja **-p** pokazuje argumenty funkcji zarządzanej.<br /><br /> Opcja **-l** pokazuje informacje o zmiennych lokalnych w ramce. Rozszerzenie debugowania SOS nie może pobrać lokalnych nazw, więc dane wyjściowe dla lokalnych nazw mają format \< *wartość* *adresu* >  **=** \<lokalnego >.<br /><br /> Opcja **-a**(All) jest skrótem- **l** i **-p** połączonym.<br /><br /> Opcja **-n** wyłącza wyświetlanie nazw plików źródłowych i numerów wierszy. Jeśli opcja debugera SYMOPT_LOAD_LINES jest określona, SOS będzie wyszukiwać symbole dla każdej ramki zarządzanej i jeśli wyszukiwanie zakończy się pomyślnie, wyświetlona zostanie odpowiadająca nazwa pliku źródłowego i numer wiersza. Nie można określić parametru **-n** (brak numerów wierszy), aby wyłączyć to zachowanie.<br /><br /> Rozszerzenie debugowania SOS nie wyświetla ramek przejścia na platformach opartych o procesory x64 i IA-64.|
|**COMState**|Wyświetla listę modeli com dla każdego wątku i wskaźnika, `Context` jeśli jest dostępny.|
|**DumpArray** [ **-Start** \< *startIndex*>] [ **-Długość** \< *długości >]* [ **-Details**] [ **-nofields**] \< *adres obiektu tablicy*><br /><br /> —lub—<br /><br /> **Da** [ **-Start** \< *startIndex*>] [ **-Długość** \< *długości >]* [ **-detail**] [ **-nofields**] *adres obiektu tablicy*>|Sprawdza elementy obiektu tablicowego.<br /><br /> Opcja **-Start** określa początkowy indeks, w którym mają być wyświetlane elementy.<br /><br /> Opcja **-Length** określa liczbę elementów do wyświetlenia.<br /><br /> Opcja **-Details** wyświetla szczegóły elementu przy użyciu formatów **DumpObj** i **DumpVC** .<br /><br /> Opcja **-nofields** uniemożliwia wyświetlanie tablic. Ta opcja jest dostępna tylko wtedy, gdy określono opcję **-detail** .|
|**DumpAssembly** \< *adres zestawu*>|Wyświetla informacje o zestawie.<br /><br /> Polecenie **DumpAssembly** wyświetla listę wielu modułów, jeśli istnieją.<br /><br /> Adres zestawu można uzyskać za pomocą polecenia **DumpDomain** .|
|**DumpClass** \< *Adres EEClass*>|Wyświetla informacje o `EEClass` strukturze skojarzonej z typem.<br /><br /> Polecenie **DumpClass** wyświetla wartości pól statycznych, ale nie wyświetla niestatycznych wartości pól.<br /><br /> Użyj polecenia **DumpMT**, **DumpObj**, **Name2EE**lub **Token2EE** , aby uzyskać `EEClass` adres struktury.|
|**DumpDomain** [\<*adres domeny*>]|Wylicza każdy <xref:System.Reflection.Assembly> obiekt, który jest ładowany w określonym <xref:System.AppDomain> adresie obiektu.  Gdy jest wywoływana bez parametrów, polecenie **DumpDomain** wyświetla wszystkie <xref:System.AppDomain> obiekty w procesie.|
|**DumpHeap** [ **-stat**] [ **-Strings**] [ **-Short**] [ **-minimalny** \< *rozmiar*>] [ **-Maksymalny** \< *rozmiar*>] [ **-thinlock**] [ **-startAtLowerBound**] [ **-MT** \< *Metoda adresu*>] [ **-Type Nazwa typu** *częściowego*>] [*Start* [End]] \<|Wyświetla informacje dotyczące sterty zebranej podczas odśmiecania pamięci i statystyk odśmiecania w stosunku do obiektów.<br /><br /> Polecenie **DumpHeap** wyświetla ostrzeżenie, jeśli wykryje nadmierną fragmentację w stercie modułu wyrzucania elementów bezużytecznych.<br /><br /> Opcja **-stat** ogranicza dane wyjściowe do podsumowania typu statystycznego.<br /><br /> Opcja **-Strings** ogranicza dane wyjściowe do statystycznego podsumowania wartości ciągu.<br /><br /> Opcja **-Short** ogranicza dane wyjściowe tylko do adresu każdego obiektu. Dzięki temu można łatwo strumieniować dane wyjściowe z polecenia do innego polecenia debugera w celu automatyzacji.<br /><br /> Opcja **-min** ignoruje obiekty, które są mniejsze niż `size` parametr określony w bajtach.<br /><br /> Opcja **-Max** ignoruje obiekty, które są większe niż `size` parametr określony w bajtach.<br /><br /> Opcja **-thinlock** raportuje ThinLocks.  Aby uzyskać więcej informacji, zobacz **SyncBlk** polecenie.<br /><br /> `-startAtLowerBound` Opcja wymusza, że sterta rozpocznie się z dolną granicą podanego zakresu adresów. Podczas fazy planowania sterta często nie posiada funkcji przechodzenia, ponieważ obiekty są przenoszone. Ta opcja wymusza, aby **DumpHeap** się rozpocząć od określonego dolnego ograniczenia. Należy podać adres prawidłowego obiektu jako dolną granicę, aby ta opcja działała. Można wyświetlić pamięć pod adresem błędnego obiektu, aby ręcznie odnaleźć następną tabelę metod. Jeśli wyrzucanie elementów bezużytecznych jest obecnie `memcopy`w wywołaniu, można również znaleźć adres następnego obiektu przez dodanie rozmiaru na adres początkowy, który jest dostarczany jako parametr.<br /><br /> Opcja **-MT** wyświetla tylko te obiekty, które odpowiadają określonej `MethodTable` strukturze.<br /><br /> Opcja **-Type** wyświetla tylko te obiekty, których nazwa typu jest dopasowaniem podciągu określonego ciągu.<br /><br /> `start` Parametr rozpoczyna wyświetlanie listy z podanego adresu.<br /><br /> `end` Parametr powoduje zatrzymanie listy o określonym adresie.|
|**DumpIL** &#124; *Zarządzany obiekt elementu DynamicMethod* &#124;> wskaźnikDynamicMethodDesc\<> MethodDesc \< \<               >|Wyświetla język pośredni Microsoft (MSIL) skojarzony z zarządzaną metodą.<br /><br /> Należy zauważyć, że dynamiczny MSIL jest emitowany inaczej od MSIL, który jest ładowany z zestawu. Dynamiczny MSIL odnosi się do obiektów w tablicy obiektu zarządzanego, a nie do tokenów metadanych.|
|**DumpLog** [ **-addr** \< *addressOfStressLog*>] [<*Filenam*`e`>]|Zapisuje zawartość dziennika obciążenia pamięci do określonego pliku. Jeśli nazwa nie zostanie określona, polecenie tworzy plik o nazwie StressLog.txt w bieżącym katalogu.<br /><br /> Dziennik obciążenia pamięci pomaga w diagnozowaniu błędów obciążenia pamięci bez używania blokad lub we/wy. Aby włączyć dziennik obciążeniowy, ustaw następujące klucze rejestru w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework<br /><br /> (DWORD) StressLog = 1<br /><br /> (DWORD) LogFacility = 0xffffffff<br /><br /> (DWORD) StressLogSize = 65536<br /><br /> Opcjonalna `-addr` opcja umożliwia określenie dziennika obciążeniowego innego niż domyślny.|
|**DumpMD** \< *Adres MethodDesc*>|Wyświetla informacje o `MethodDesc` strukturze pod podanym adresem.<br /><br /> Można użyć polecenia **IP2MD** , aby uzyskać `MethodDesc` adres struktury z funkcji zarządzanej.|
|**DumpMT** [ **-MD**] \< *Adres metody*>|Wyświetla informacje dotyczące tabeli metod pod podanym adresem. Określenie opcji **-MD** powoduje wyświetlenie listy wszystkich metod zdefiniowanych za pomocą obiektu.<br /><br /> Każdy obiekt zarządzany zawiera wskaźnik tabeli metod.|
|**DumpMethodSig** sigaddr > <*moduleadd* \<`r`>|Wyświetla informacje o `MethodSig` strukturze pod podanym adresem.|
|**DumpModule** [ **-MT**] \< *Adres modułu*>|Wyświetla informacje dotyczące modułu pod podanym adresem. Opcja **-MT** wyświetla typy zdefiniowane w module i typy, do których odwołuje się moduł<br /><br /> Aby pobrać adres modułu, można użyć polecenia **DumpDomain** lub **DumpAssembly** .|
|**DumpObj** [ **-nofields**] \< *adres obiektu*><br /><br /> —lub—<br /><br /> **Wykonaj** \< *adres obiektu*>|Wyświetla informacje dotyczące obiektu pod podanym adresem. Polecenie **DumpObj** wyświetla pola, `EEClass` informacje o strukturze, tabelę metod i rozmiar obiektu.<br /><br /> Można użyć polecenia **DumpStackObjects** , aby pobrać adres obiektu.<br /><br /> Należy pamiętać, że można uruchomić polecenie **DumpObj** w polach typu `CLASS` , ponieważ są one również obiektami.<br /><br /> Opcja nofields uniemożliwia wyświetlanie pól obiektu, jest przydatna w przypadku obiektów, takich jak ciąg. `-`|
|**DumpRuntimeTypes**|Wyświetla obiekty typu środowiska uruchomieniowego w stercie modułu odśmiecania pamięci i wyświetla ich nazwy skojarzonych typów i tabele metod.|
|**DumpStack** [ **-EE**] [ **-n**] [`top` *stos* [`bottom`St]`k`]|Wyświetla ślad stosu.<br /><br /> Opcja **-EE** powoduje, że polecenie **DumpStack** wyświetla tylko funkcje zarządzane. Użyj parametrów `bottom` i, aby ograniczyć ramki stosu wyświetlane na platformach x86. `top`<br /><br /> Opcja **-n** wyłącza wyświetlanie nazw plików źródłowych i numerów wierszy. Jeśli opcja debugera SYMOPT_LOAD_LINES jest określona, SOS będzie wyszukiwać symbole dla każdej ramki zarządzanej i jeśli wyszukiwanie zakończy się pomyślnie, wyświetlona zostanie odpowiadająca nazwa pliku źródłowego i numer wiersza. Nie można określić parametru **-n** (brak numerów wierszy), aby wyłączyć to zachowanie.<br /><br /> Na platformach x86 i x64 polecenie **DumpStack** tworzy pełny ślad stosu.<br /><br /> Na platformach opartych na procesorze IA-64 polecenie **DumpStack** naśladuje polecenie " **K** " debugera. Parametry `top` i`bottom` są ignorowane na platformach opartych na procesorze IA-64.|
|**DumpSig** \< *sigaddr* moduleaddr> \<>|Wyświetla informacje o `Sig` strukturze pod podanym adresem.|
|**DumpSigElem** \< *sigaddr* moduleaddr> \<>|Wyświetla jeden element obiektu podpisu. W większości przypadków należy używać **DumpSig** do przeglądania poszczególnych obiektów sygnatur. Jeśli jednak podpis został uszkodzony w jakiś sposób, można użyć **DumpSigElem** do odczytania prawidłowych części tego elementu.|
|**DumpStackObjects** [ **-verify**] [`top` *stos* [`bottom` *Stack*]]<br /><br /> —lub—<br /><br /> **Obiekty DSO** [ **-verify**] [`top` *stos* [`bottom` *Stack*]]|Wyświetla wszystkie zarządzane obiekty znalezione w granicach bieżącego stosu.<br /><br /> Opcja **-verify** sprawdza poprawność każdego pola niestatycznego `CLASS` pola obiektu.<br /><br /> Użyj polecenia **DumpStackObject** z poleceniami śledzenia stosu, takimi jak polecenie **K** i polecenie **CLRStack** , aby określić wartości zmiennych lokalnych i parametrów.|
|**DumpVC** *Adres adresu* *metody*>  \<\<>|Wyświetla informacje dotyczące pól klasy wartości pod podanym adresem.<br /><br /> Parametr **metody** umożliwia **DumpVC** poprawnego interpretowania pól. Klasy wartości nie posiadają tabeli metod jako ich pierwsze pole.|
|**EEHeap** [ **-GC**] [ **-Loader**]|Wyświetla informacje o pamięci procesu używanej przez wewnętrzne struktury danych środowiska CLR.<br /><br /> Opcje **-GC** i **-Loader** ograniczają dane wyjściowe tego polecenia do struktur danych modułu zbierającego elementy bezużyteczne lub modułów ładujących.<br /><br /> Informacje dotyczące modułu odśmiecania pamięci wyświetlają zakresy każdego segmentu w zarządzanej stercie.  Jeśli wskaźnik mieści się w zakresie segmentów podanym przez **-GC**, wskaźnik jest wskaźnikiem obiektu.|
|**EEStack** [ **-Short**] [ **-EE**]|Uruchamia polecenie **DumpStack** we wszystkich wątkach procesu.<br /><br /> Opcja **-EE** jest przenoszona bezpośrednio do polecenia **DumpStack** . **-Krótki** parametr ogranicza dane wyjściowe do następujących rodzajów wątków:<br /><br /> Wątki, które uzyskały blokadę.<br /><br /> Wątki, które zostały zatrzymane w celu umożliwienia odśmiecenia pamięci.<br /><br /> Wątki, które są obecnie w kodzie zarządzanym.|
|**EEVersion**|Wyświetla wersję środowiska CLR.|
|**Ehinfo** [\<*MethodDesc adres*>] [\<*adres kodu*>]|Wyświetla bloki obsługi wyjątków w określonej metodzie.  To polecenie wyświetla adresy kodu i przesunięcia dla bloku klauzuli ( `try` bloku) i bloku obsługi `catch` (bloku).|
|**Często zadawane pytania**|Wyświetla najczęściej zadawane pytania.|
|**FinalizeQueue** [ **-szczegóły**] &#124; [ **-już**] [ **-Short**]|Wyświetla wszystkie obiekty zarejestrowane dla finalizacji.<br /><br /> Opcja **-detail** wyświetla dodatkowe informacje o `SyncBlocks` tym, które muszą zostać wyczyszczone, i wszelkie `RuntimeCallableWrappers` (RCW), które oczekują na oczyszczenie. Obie te struktury danych są buforowane i oczyszczane przez wątek finalizatora w trakcie jego działania.<br /><br /> `-allReady` Opcja wyświetla wszystkie obiekty, które są gotowe do sfinalizowania, bez względu na to, czy są one już oznaczone przez odzyskiwanie pamięci jako takie, czy zostaną oznaczone przez następne wyrzucanie elementów bezużytecznych. Obiekty, które znajdują się na liście „gotowych do finalizacji”, są obiektami, które można sfinalizować i które nie są już zakorzenione. Ta opcja może być bardzo kosztowna, ponieważ weryfikuje, czy wszystkie obiekty w kolejkach, które można sfinalizować, są nadal zakorzenione.<br /><br /> `-short` Opcja ogranicza dane wyjściowe do adresu każdego obiektu. Jeśli jest używany w połączeniu z **-już**, wylicza wszystkie obiekty, które mają finalizator, który nie jest już odblokowany. Jeśli jest używana samodzielnie, wyświetla listę wszystkich obiektów w kolejkach możliwych do sfinalizowania i „gotowych do finalizacji”.|
|**FindAppDomain** \< *Adres obiektu*>|Określa domenę aplikacji obiektu pod podanym adresem.|
|**FindRoots** **-Gen** &#124; &#124; N > — Wygeneruj dowolny\<adresobiektu \<>|Powoduje przerwanie debugowania w obiekcie debugowanym podczas kolejnego zbierania dla określonej generacji. Efekt jest resetowany natychmiast po wystąpieniu przerwania. Aby przerwać podczas kolejnego zbierania, należy ponownie wydać polecenie. *\<Adresu obiektu>* formularz tego polecenia jest używany po wystąpieniu przerwania spowodowane **-gen** lub **—dowolnego ogólnego** wystąpił. W tym czasie debugowanego obiektu jest w odpowiednim stanie dla **FindRoots** , aby identyfikować elementy główne dla obiektów z bieżących generacji wybrakowanych.|
|**GCHandles** [ **-perdomain**]|Wyświetla statystyki dotyczące uchwytów modułu odśmiecania pamięci w procesie.<br /><br /> Opcja **-perdomain** rozmieszcza dane statystyczne według domeny aplikacji.<br /><br /> Użyj polecenia **GCHandles** , aby znaleźć przecieki pamięci spowodowane przez przecieki w obsłudze elementów bezużytecznych. Przykładowo wyciek pamięci występuje, gdy kod zachowuje dużą tablicę, ponieważ silny uchwyt modułu odśmiecania pamięci nadal na nią wskazuje, a uchwyt został odrzucony bez jej zwolnienia.|
|**GCHandleLeaks**|Wyszukuje w pamięci dowolnych odwołań do silnych i przypiętych uchwytów modułu odśmiecania pamięci w procesie i wyświetla wyniki. Jeśli zostanie znalezione dojście, polecenie **GCHandleLeaks** wyświetla adres odwołania. Jeśli uchwyt nie zostanie znaleziony w pamięci, polecenie wyświetli powiadomienie.|
|**GCInfo** \<*Adres kodu* *MethodDesc*>\<>|Wyświetla dane, które wskazują, kiedy rejestry lub lokalizacje stosu zawierają obiekty zarządzane. Jeśli występuje odśmiecanie pamięci, moduł musi znać lokalizacje odwołań do obiektów, aby móc je zaktualizować za pomocą nowych wartości wskaźnika obiektu.|
|**Gcroot** [ **-nostacks**] \< *Adres obiektu*>|Wyświetla informacje dotyczące odwołań (lub korzeni) do obiektu pod podanym adresem.<br /><br /> **Gcroot** polecenie bada całe zarządzane sterty i tabelę dojść dla dojść w innych obiektach i uchwytach na stosie. Każdy stos jest następnie przeszukiwany w celu znalezienia wskaźników do obiektów; kolejka finalizatorów również będzie przeszukiwana.<br /><br /> To polecenie nie określa, czy korzeń stosu jest nieprawidłowy lub odrzucony. Użyj poleceń **CLRStack** i **U** , aby rozłożyć ramkę, do której należy wartość lokalna lub argument, aby określić, czy katalog główny stosu jest nadal używany.<br /><br /> Opcja **-nostacks** ogranicza wyszukiwanie do dojść do modułu zbierającego elementy bezużyteczne i osiągalnych obiektów.|
|**GCWhere**  *\<adresu obiektu>*|Wyświetla lokalizację i rozmiar przekazanego argumentu w stercie modułu odśmiecania pamięci. Gdy argument znajduje się w stercie zarządzanej, ale nie jest prawidłowym adresem obiektu, rozmiar zostanie wyświetlony jako 0 (zero).|
|**Pomoc** [\<*polecenie*>] [`faq`]|Wyświetla wszystkie dostępne polecenia, gdy parametr nie jest określony, lub wyświetla szczegółowe informacje pomocy dotyczące określonego polecenia.<br /><br /> `faq` Parametr wyświetla odpowiedzi na często zadawane pytania.|
|**HeapStat** [ **-inclUnrooted** &#124; **-IU**]|Wyświetla rozmiary generacji dla każdej sterty i całkowitą ilość wolnego miejsca w każdej generacji na każdym stosie. Jeśli opcja-**inclUnrooted** jest określona, raport zawiera informacje o zarządzanych obiektach z sterty wyrzucania elementów bezużytecznych, która nie jest już w katalogu głównym.|
|**HistClear**|Zwalnia wszystkie zasoby używane przez rodzinę `Hist` poleceń.<br /><br /> Ogólnie rzecz biorąc nie trzeba jawnie wywoływać `HistClear`, ponieważ każda `HistInit` czyści poprzednie zasoby.|
|**HistInit**|Inicjuje struktury SOS z dziennika obciążenia zapisanego w obiekcie debugowanym.|
|**HistObj** *\<obj_address>*|Sprawdza wszystkie rekordy przeniesienia dziennika obciążenia i wyświetla łańcuch przeniesień modułu odśmiecania pamięci, które mogły doprowadzić do adresu przekazanego jako argument.|
|**HistObjFind**  *\<obj_address>*|Wyświetla wszystkie wpisy dziennika, które odwołują się do obiektu pod podanym adresem.|
|**HistRoot** *\<root>*|Wyświetla informacje powiązane zarówno z promocjami, jak i przeniesieniami określonego korzenia.<br /><br /> Wartość korzenia może być użyta do śledzenia ruchu obiektu za pomocą modułu odśmiecania pamięci.|
|**IP2MD** \< *Adres kodu*>|`MethodDesc` Wyświetla strukturę pod określonym adresem w kodzie, który został skompilowany w trybie JIT.|
|`ListNearObj`(`lno` *) obj_address\<>*|Wyświetla obiekty poprzedzające i następujące po określonym adresie. Polecenie wyszukuje adres w stercie modułu odśmiecania pamięci podobny do prawidłowego początku obiektu zarządzanego (na podstawie prawidłowej metody tabel) i obiektu następującego po adresie argumentu.|
|**MinidumpMode** [**0**] [**1**]|Uniemożliwia uruchamianie poleceń niebezpiecznych podczas używania minizrzutu.<br /><br /> Przekaż **wartość 0** , aby wyłączyć tę funkcję lub **1** , aby włączyć tę funkcję. Domyślnie wartość **MinidumpMode** jest równa **0**.<br /><br /> Minizrzutów utworzony za pomocą polecenia **. dump/m** lub polecenia **. dump** mają ograniczone dane specyficzne dla środowiska CLR i umożliwiają poprawne uruchamianie tylko podzbioru poleceń sos. Niektóre polecenia mogą zakończyć się nieoczekiwanym błędem, ponieważ wymagane obszary pamięci nie są mapowane lub są tylko częściowo mapowane. Ta opcja chroni przed uruchamianiem poleceń niebezpiecznych w stosunku do minizrzutów.|
|**Name2EE** \<typ nazwymodułulub> *Nazwa metody*\<><br /><br /> —lub—<br /><br /> **Name2EE** \< nazwamodułu>! *Typ lub nazwa metody* \<>|Wyświetla strukturę i `EEClass` strukturę określonego typu lub metody w określonym module. `MethodTable`<br /><br /> Określony moduł musi zostać załadowany w procesie.<br /><br /> Aby uzyskać poprawną nazwę typu, przejrzyj moduł przy użyciu [Ildasm. exe (Il dezasembler)](ildasm-exe-il-disassembler.md). Możesz również przekazać `*` jako parametr nazwy modułu, aby przeszukać wszystkie załadowane moduły zarządzane. Parametr *name modułu* może być również nazwą debugera dla modułu, taką jak `mscorlib` lub. `image00400000`<br /><br /> To polecenie obsługuje składnię debugera systemu Windows <`module`<>`!``type`>. Typ musi być w pełni kwalifikowany.|
|**ObjSize** [\<*Object address*>] &#124; [ **-aggregate**] [ **-stat**]|Wyświetla rozmiar określonego obiektu. Jeśli nie określisz żadnych parametrów, polecenie **ObjSize** Wyświetla rozmiar wszystkich obiektów znalezionych w zarządzanych wątkach, wyświetla wszystkie uchwyty modułu wyrzucania elementów bezużytecznych w procesie i sumuje rozmiar wszystkich obiektów wskazywanych przez te uchwyty. **ObjSize** polecenie zawiera rozmiar wszystkich obiektów podrzędnych oprócz elementu nadrzędnego.<br /><br /> Opcja **-Aggregate** może być używana w połączeniu z argumentem **-stat** , aby uzyskać szczegółowy widok typów, które są nadal odblokowane. Za pomocą **! DumpHeap-stat** i **! ObjSize-Aggregate-stat**, można określić, które obiekty nie są już w katalogu głównym, i diagnozować różne problemy z pamięcią.|
|**PrintException** [ **-nested**] [ **-linie**] [\<*Adres obiektu wyjątku*>]<br /><br /> —lub—<br /><br /> **Środowisko PE** [ **-nested**] [\<*Adres obiektu wyjątku*>]|Wyświetla i formatuje pola dowolnego obiektu pochodnego od <xref:System.Exception> klasy pod określonym adresem. Jeśli nie określisz adresu, polecenie **PrintException** wyświetli ostatni wyjątek zgłoszony w bieżącym wątku.<br /><br /> Opcja **-nested** wyświetla szczegóły dotyczące zagnieżdżonych obiektów wyjątków.<br /><br /> Opcja **-wierszy** wyświetla informacje o źródle, jeśli są dostępne.<br /><br /> To polecenie służy do formatowania i wyświetlania `_stackTrace` pola, które jest tablicą binarną.|
|**ProcInfo** [ **-ENV**] [ **-Time**] [ **-MEM**]|Wyświetla zmienne środowiskowe dla procesu, czasu procesora dla jądra i statystyki użycia pamięci.|
|**RCWCleanupList** \< *Adres RCWCleanupList*>|Wyświetla listę otok wywoływanych w czasie wykonywania pod określonym adresem, które czekają na oczyszczanie.|
|**SaveModule***Nazwa pliku* adresupodstawowego\<>  \<>|Zapisuje określony obraz, który jest załadowany do pamięci pod podanym adresem, do określonego pliku.|
|**SOSFlush**|Opróżnia wewnętrzną pamięć podręczną SOS.|
|**StopOnException** [ **-pochodne**] [ **-Create** &#124; **-create2**]>  Numer pseudo-Registerwyjątku\< \<>|Powoduje zatrzymanie debugera, gdy określony wyjątek zostanie zgłoszony, ale kontynuuje działanie, gdy zgłaszane są inne wyjątki.<br /><br /> Opcja **pochodna** przechwytuje określony wyjątek i każdy wyjątek, który pochodzi od określonego wyjątku.|
|**SyncBlk** [ **-wszystkie** &#124; \< *SyncBlk numer*>]|Wyświetla określoną `SyncBlock` strukturę lub wszystkie `SyncBlock` struktury.  Jeśli nie przeszedł żadnych argumentów, polecenie **SyncBlk** wyświetla `SyncBlock` strukturę odpowiadającą obiektom należącym do wątku.<br /><br /> `SyncBlock` Struktura jest kontenerem dla dodatkowych informacji, które nie muszą być tworzone dla każdego obiektu. Może przechowywać dane międzyoperacyjnego modelu COM, kody skrótów i informacje dotyczące blokowania na potrzeby operacji bezpiecznych wątkowo.|
|**ThreadPool**|Wyświetla informacje o puli wątków zarządzanych, w tym liczbę żądań pracy w kolejce, liczbę wątków portu zakończenia i liczbę czasomierzy.|
|**Token2EE** *token nazwy* *modułu*>  \<\<>|Zamienia określony token metadanych w określonym module na `MethodTable` strukturę lub `MethodDesc` strukturę.<br /><br /> Można przekazać `*` parametr name modułu, aby znaleźć, do czego mapowania tokenów w każdym załadowanym module zarządzanym. Możesz również przekazać nazwę debugera dla modułu, na przykład `mscorlib` lub. `image00400000`|
|**Wątki** [ **-Live**] [ **-Special**]|Wyświetla wszystkie zarządzane wątki w procesie.<br /><br /> **Wątki** polecenie wyświetla identyfikator skrócony DEBUGERA, identyfikator wątku CLR i identyfikator wątku systemu operacyjnego.  Ponadto **wątki** polecenie wyświetla kolumnę domeny, która wskazuje domenę aplikacji, w której wykonywany jest wątek, kolumnę apt, która wyświetla tryb apartamentu com, i kolumnę wyjątku, która wyświetla ostatni wyjątek zgłoszony w nici.<br /><br /> Opcja **-Live** Wyświetla wątki skojarzone z aktywnym wątkiem.<br /><br /> Opcja **-Special** wyświetla wszystkie wątki specjalne utworzone przez środowisko CLR. Specjalne wątki obejmują wątki odzyskiwania pamięci (w współbieżności i wyrzucanie elementów bezużytecznych serwera), wątki pomocnika debugera, wątki finalizatorów, <xref:System.AppDomain> zwalnianie wątków i wątki czasomierza puli wątków.|
|*Pole wartości stanu*  **\< ThreadState** **>**|Wyświetla stan wątku. Parametr jest wartością `State` pola w danych wyjściowych raportu **wątki.** `value`<br /><br /> Przykład:<br /><br /> `0:003> !Threads     ThreadCount:      2     UnstartedThread:  0     BackgroundThread: 1     PendingThread:    0     DeadThread:       0     Hosted Runtime:   no                                           PreEmptive   GC Alloc           Lock            ID OSID ThreadOBJ    State     GC       Context       Domain   Count APT Exception        0    1  250 0019b068      a020 Disabled 02349668:02349fe8 0015def0     0 MTA        2    2  944 001a6020      b220 Enabled  00000000:00000000 0015def0     0 MTA (Finalizer)     0:003> !ThreadState b220         Legal to Join         Background         CLR Owns         CoInitialized         In Multi Threaded Apartment`|
|**TraverseHeap** [ **-XML**] \< *Nazwa pliku*>|Zapisuje informacje dotyczące sterty do określonego pliku w formacie zrozumiałym dla profilera CLR. Opcja **-XML** powoduje, że polecenie **TraverseHeap** formatuje plik jako XML.<br /><br /> Profiler CLR można pobrać z [Centrum pobierania Microsoft](https://go.microsoft.com/fwlink/?LinkID=67325).|
|**U** [ **-GCInfo**] [ **-ehinfo**] [ **-n**] \< *MethodDesc adres*> &#124; \< *adres*>|Przedstawia oddzielny do adnotacji metodę zarządzaną określoną przez `MethodDesc` wskaźnik struktury dla metody lub przez adres kodu w treści metody. **P** polecenie wyświetla całą metodę od początku do końca, z adnotacjami, które konwertują tokeny metadanych na nazwy.<br /><br /> Opcja **-GCInfo** powoduje, że polecenie **U** wyświetla `GCInfo` strukturę dla metody.<br /><br /> Opcja **-ehinfo** wyświetla informacje o wyjątkach dla metody. Te informacje można również uzyskać za pomocą polecenia **ehinfo** .<br /><br /> Opcja **-n** wyłącza wyświetlanie nazw plików źródłowych i numerów wierszy. Jeśli opcja debugera SYMOPT_LOAD_LINES jest określona, SOS wyszukuje symbole dla każdej zarządzanej ramki i jeśli wyszukiwanie zakończy się pomyślnie, wyświetla odpowiadającą nazwę pliku źródłowego i numer wiersza. Możesz określić opcję **-n** , aby wyłączyć to zachowanie.|
|**VerifyHeap**|Sprawdza sterty modułu odśmiecania pamięci w poszukiwaniu objawów uszkodzeń i wyświetla znalezione błędy.<br /><br /> Uszkodzenie sterty może być spowodowane przez wywołania platformy, które są konstruowane niepoprawnie.|
|**VerifyObj** \< *adres obiektu*>|Sprawdza, czy obiekt, który jest przekazywany jako argument posiada oznaki uszkodzenia.|
|**VMMap**|Przechodzi wirtualną przestrzeń adresową i wyświetla typ ochrony stosowany do każdego regionu.|
|**VMStat**|Dostarcza widok podsumowania wirtualnej przestrzeni adresowej, uporządkowany według typów ochrony stosowanych do pamięci (wolna, zarezerwowana, zatwierdzona, prywatna, mapowana, obrazów). Kolumna TOTAL wyświetla wynik z kolumny AVERAGE pomnożony przez kolumnę BLK COUNT.|

## <a name="remarks"></a>Uwagi

Rozszerzenie debugowania SOS umożliwia wyświetlenie informacji o kodzie działającym wewnątrz środowiska CLR. Przykładowo rozszerzenia debugowania SOS można użyć do wyświetlania informacji na temat zarządzanej sterty, wyszukiwania uszkodzeń sterty, wyświetlania typów danych wewnętrznych używanych przez środowisko uruchomieniowe i wyświetlania informacji o całym zarządzanym kodzie działającym wewnątrz środowiska uruchomieniowego.

Aby użyć rozszerzenia debugowania SOS w programie Visual Studio, zainstaluj [zestaw sterowników systemu Windows (WDK)](/windows-hardware/drivers/download-the-wdk). Aby uzyskać informacje na temat zintegrowanego środowiska debugowania w programie Visual Studio, zobacz [środowiska debugowania](/windows-hardware/drivers/debugger/debuggers-in-the-debugging-tools-for-windows-package).

Można również użyć rozszerzenia debugowania SOS przez załadowanie go do [debugera WinDbg. exe](/windows-hardware/drivers/debugger/debugger-download-tools) i wykonywanie poleceń w programie WinDbg. exe.

Aby załadować rozszerzenie debugowania SOS do debugera WinDbg.exe, należy uruchomić następujące polecenie w narzędziu:

```console
.loadby sos clr
```

WinDbg.exe i program Visual Studio używają wersji SOS.dll, która odpowiada aktualnie używanej wersji Mscorwks.dll. Domyślnie należy użyć wersji programu SOS.dll, który odpowiada aktualnej wersji Mscorwks.dll.

Aby użyć pliku zrzutu utworzonego na innym komputerze, należy upewnić się, że plik Mscorwks.dll dodany podczas instalacji znajduje się w ścieżce symbolu i załadować odpowiadającą wersję SOS.dll.

Aby załadować określoną wersję SOS.dll, należy wpisać następujące polecenie w debugerze systemu Windows:

```console
.load <full path to sos.dll>
```

## <a name="examples"></a>Przykłady

Następujące polecenie wyświetla zawartość tablicy pod adresem `00ad28d0`.  Wyświetlanie zaczyna się od drugiego elementu, a następnie wyświetlonych zostaje pięć kolejnych elementów.

```console
!dumparray -start 2 -length 5 -detail 00ad28d0
```

Następujące polecenie wyświetla zawartość zestawu pod adresem `1ca248`.

```console
!dumpassembly 1ca248
```

Następujące polecenie wyświetla informacje o stercie modułu odśmiecania pamięci.

```console
!dumpheap
```

Następujące polecenie zapisuje zawartość dziennika obciążenia pamięci do pliku (domyślnego) o nazwie StressLog.txt w bieżącym katalogu.

```console
!DumpLog
```

Następujące polecenie wyświetla `MethodDesc` strukturę pod adresem `902f40`.

```console
!dumpmd 902f40
```

Następujące polecenie wyświetla informacje o module pod adresem `1caa50`.

```console
!dumpmodule 1caa50
```

Następujące polecenie wyświetla informacje o obiekcie pod adresem `a79d40`.

```console
!DumpObj a79d40
```

Następujące polecenie wyświetla pola klasy wartości pod adresem `00a79d9c` przy użyciu tabeli metod pod adresem. `0090320c`

```console
!DumpVC 0090320c 00a79d9c
```

Następujące polecenie wyświetla pamięć procesu używaną przez moduł odśmiecania pamięci.

```console
!eeheap -gc
```

Następujące polecenie wyświetla wszystkie obiekty zaplanowane do finalizacji.

```console
!finalizequeue
```

Następujące polecenie określa domenę aplikacji obiektu pod adresem `00a79d98`.

```console
!findappdomain 00a79d98
```

Następujące polecenie wyświetla wszystkie uchwyty modułu odśmiecania pamięci w bieżącym procesie.

```console
!gcinfo 5b68dbb8
```

Następujące polecenie `MethodTable` wyświetla struktury i `Main` `EEClass` dla metody w klasie `MainClass` w module `unittest.exe`.

```console
!name2ee unittest.exe MainClass.Main
```

Następujące polecenie wyświetla informacje o tokenie metadanych pod adresem `02000003` w module. `unittest.exe`

```console
!token2ee unittest.exe 02000003
```

## <a name="see-also"></a>Zobacz także

- [Narzędzia](index.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
