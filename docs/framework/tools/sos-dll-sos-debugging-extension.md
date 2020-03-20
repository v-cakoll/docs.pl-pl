---
title: SOS.dll (rozszerzenie do debugowania SOS)
ms.date: 03/30/2017
helpviewer_keywords:
- debugging extensions
- SOS debugging extensions
- SOS.dll
ms.assetid: 9ac1b522-77ab-4cdc-852a-20fcdc9ae498
ms.openlocfilehash: 4c3a7f2798791f0c8a6b752f06bc2937fc970d40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715733"
---
# <a name="sosdll-sos-debugging-extension"></a>SOS.dll (rozszerzenie debugowania SOS)

Rozszerzenie debugowania SOS (SOS.dll) ułatwia debugowanie zarządzanych programów w programie Visual Studio i debugerze systemu Windows (WinDbg.exe), dostarczając informacji o wewnętrznym środowisku wspólnego środowiska wykonawczego języka (CLR). To narzędzie wymaga włączenia debugowania niezarządzanego w projekcie. SOS.dll jest automatycznie instalowany z .NET Framework. Aby użyć pliku SOS.dll w programie Visual Studio, zainstaluj [zestaw Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk).

## <a name="syntax"></a>Składnia

```console
![command] [options]
```

## <a name="commands"></a>Polecenia

|Polecenie|Opis|
|-------------|-----------------|
|**AnalyzeOOM** (**ao**)|Wyświetla informacje dotyczące ostatniego braku pamięci (OOM), które wystąpiły w żądaniu alokacji do sterty wyrzucania elementów bezużytecznych. (W module odśmiecania pamięci dla serwera wyświetla OOM, jeżeli wystąpił, dla każdej sterty modułu odśmiecania pamięci.)|
|**BPMD** [**-nofuturemodule**]\<[ nazwa*metody* *modułu*> \<>] [**-md**  < `MethodDesc`>] **-list** **-clear** \<pending *breakpoint number*> **-clearall**|Tworzy punkt przerwania w określonej metodzie w określonym module.<br /><br /> Jeśli określony moduł i metoda nie zostały załadowane, to polecenie czeka na powiadomienie, że moduł został załadowany i skompilowany „just in time” (JIT) przed utworzeniem punktu przerwania.<br /><br /> Listę oczekujących punktów przerwania można zarządzać za pomocą opcji **-list**, **-clear**i **-clearall:**<br /><br /> Opcja **-list** generuje listę wszystkich oczekujących punktów przerwania. Jeśli oczekujący punkt przerwania ma niezerowy identyfikator modułu, ten punkt przerwania jest właściwy dla funkcji w tym określonym załadowanym module. Jeśli oczekujący punkt przerwania ma zerowy identyfikator modułu, ten punkt przerwania ma zastosowanie do modułów, które nie zostały jeszcze załadowane.<br /><br /> Użyj opcji **-clear** lub **-clearall,** aby usunąć oczekujące punkty przerwania z listy.|
|**CLRStack** [**-a**] [**-l**] [**-p**] [**-n**]|Dostarcza ślad stosu wyłącznie dla kodu zarządzanego.<br /><br /> Opcja **-p** pokazuje argumenty funkcji zarządzanej.<br /><br /> Opcja **-l** pokazuje informacje o zmiennych lokalnych w ramce. Rozszerzenie debugowania SOS nie może pobrać nazw lokalnych, więc dane \<wyjściowe dla nazw lokalnych są w formacie>  **=** \< *wartość* *adresu lokalnego*>.<br /><br /> Opcja **-a**(wszystkie) jest skrótem do **-l** i **-p** w połączeniu.<br /><br /> Opcja **-n** wyłącza wyświetlanie nazw plików źródłowych i numerów wierszy. Jeśli opcja debugera SYMOPT_LOAD_LINES jest określona, SOS będzie wyszukiwać symbole dla każdej ramki zarządzanej i jeśli wyszukiwanie zakończy się pomyślnie, wyświetlona zostanie odpowiadająca nazwa pliku źródłowego i numer wiersza. Można określić parametr **-n** (Brak numerów wierszy), aby wyłączyć to zachowanie.<br /><br /> Rozszerzenie debugowania SOS nie wyświetla ramek przejścia na platformach opartych o procesory x64 i IA-64.|
|**Stan COM**|Wyświetla listę modelu apartamentu COM `Context` dla każdego wątku i wskaźnika, jeśli jest dostępny.|
|**DumpArray** [**-start** \< *startIndex*>] [**-length** \< *length*>] [**-details**] [**-nofields**] \<adres obiektu *tablicy*><br /><br /> — lub —<br /><br /> **DA** [**-start** \< *startIndex*>] [**-length** \< *length*>] [**-detail**] [**-nofields**] adres obiektu *tablicy*>|Sprawdza elementy obiektu tablicowego.<br /><br /> Opcja **-start** określa indeks początkowy, przy którym mają być wyświetlane elementy.<br /><br /> Opcja **-length** określa, ile elementów ma być pokazywalnych.<br /><br /> Opcja **-details** wyświetla szczegóły elementu przy użyciu **dumpobj** i **DumpVC** formatów.<br /><br /> Opcja **-nofields** uniemożliwia wyświetlanie tablic. Ta opcja jest dostępna tylko wtedy, gdy określono opcję **-detail.**|
|**DumpAssembly** \< *adres montażu*>|Wyświetla informacje o zestawie.<br /><br /> **DumpAssembly** polecenia wyświetla wiele modułów, jeśli istnieją.<br /><br /> Adres zestawu można uzyskać za pomocą polecenia **DumpDomain.**|
|Adres **DumpClass** \< *EEClass*>|Wyświetla informacje `EEClass` o strukturze skojarzonej z typem.<br /><br /> Polecenie **DumpClass** wyświetla wartości pól statycznych, ale nie wyświetla wartości pól niestatycznych.<br /><br /> Użyj **polecenia DumpMT**, **DumpObj**, **Name2EE**lub **Token2EE,** aby uzyskać adres `EEClass` struktury.|
|**DumpDomain** \<[*adres domeny*>]|Wylicza <xref:System.Reflection.Assembly> każdy obiekt, który <xref:System.AppDomain> jest ładowany w obrębie określonego adresu obiektu.  Po wywołaniu bez parametrów, **DumpDomain** polecenia wyświetla listę wszystkich <xref:System.AppDomain> obiektów w procesie.|
|**DumpHeap** [**-stat**] [**-strings**] [**-short**] [**-min** \< *size*>] [**-max** \< *size*>] [**-thinlock**] [**-startAtLowerBound**] [**-mt** \< *MethodTable address*>] [**-type** \<partial type *name*>][*start* [*end*]]|Wyświetla informacje dotyczące sterty zebranej podczas odśmiecania pamięci i statystyk odśmiecania w stosunku do obiektów.<br /><br /> **Polecenie DumpHeap** wyświetla ostrzeżenie, jeśli wykryje nadmierne fragmentacji w stercie modułu zbierającego elementy bezużyteczne.<br /><br /> Opcja **-stat** ogranicza dane wyjściowe do podsumowania typu statystycznego.<br /><br /> Opcja **-strings** ogranicza dane wyjściowe do statystycznego podsumowania wartości ciągu.<br /><br /> Opcja **-short** ogranicza dane wyjściowe tylko do adresu każdego obiektu. Dzięki temu można łatwo strumieniować dane wyjściowe z polecenia do innego polecenia debugera w celu automatyzacji.<br /><br /> Opcja **-min** ignoruje obiekty, które `size` są mniejsze niż parametr określony w bajtach.<br /><br /> Opcja **-max** ignoruje obiekty, które `size` są większe niż parametr określony w bajtach.<br /><br /> Opcja **-thinlock** raportuje ThinLocks.  Aby uzyskać więcej informacji, zobacz **syncblk** polecenia.<br /><br /> Opcja `-startAtLowerBound` wymusza spacer sterty, aby rozpocząć w dolnej granicy podanego zakresu adresów. Podczas fazy planowania sterta często nie posiada funkcji przechodzenia, ponieważ obiekty są przenoszone. Ta opcja wymusza **DumpHeap,** aby rozpocząć jego spacer w określonej dolnej granicy. Należy podać adres prawidłowego obiektu jako dolną granicę, aby ta opcja działała. Można wyświetlić pamięć pod adresem błędnego obiektu, aby ręcznie odnaleźć następną tabelę metod. Jeśli wyrzucanie elementów bezużytecznych `memcopy`jest obecnie w wywołaniu do , można również znaleźć adres następnego obiektu, dodając rozmiar do adresu początkowego, który jest dostarczany jako parametr.<br /><br /> Opcja **-mt** zawiera listę tylko tych `MethodTable` obiektów, które odpowiadają określonej strukturze.<br /><br /> Opcja **-type** zawiera listę tylko tych obiektów, których nazwa typu jest dopasowaniem podciągów określonego ciągu.<br /><br /> Parametr `start` rozpoczyna wyświetlanie listy od określonego adresu.<br /><br /> Parametr `end` zatrzymuje wyświetlanie listy pod określonym adresem.|
|\<Obiekt \< **Metody Programu> &#124; ** Wskaźnik> &#124;  Metody> &#124;  *Wskaźnik* \< *metody> &#124;  DumpIL Managed DynamicMethod* *Managed DynamicMethod object*>|Wyświetla język pośredni Microsoft (MSIL) skojarzony z zarządzaną metodą.<br /><br /> Należy zauważyć, że dynamiczny MSIL jest emitowany inaczej od MSIL, który jest ładowany z zestawu. Dynamiczny MSIL odnosi się do obiektów w tablicy obiektu zarządzanego, a nie do tokenów metadanych.|
|**DumpLog** [**-addr** \< *addressOfStressLog*>] [<*> Filenam]* `e`|Zapisuje zawartość dziennika obciążenia pamięci do określonego pliku. Jeśli nazwa nie zostanie określona, polecenie tworzy plik o nazwie StressLog.txt w bieżącym katalogu.<br /><br /> Dziennik obciążenia pamięci pomaga w diagnozowaniu błędów obciążenia pamięci bez używania blokad lub we/wy. Aby włączyć dziennik naprężeń, ustaw następujące klucze\\rejestru w obszarze HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . Netframework:<br /><br /> (DWORD) StressLog = 1<br /><br /> (DWORD) LogFacility = 0xffffffff<br /><br /> (DWORD) StressLogSize = 65536<br /><br /> `-addr` Opcjonalna opcja umożliwia określenie dziennika naprężeń innego niż dziennik domyślny.|
|Adres **metody DumpMDD** \< *MethodDesc address*>|Wyświetla informacje `MethodDesc` o strukturze pod określonym adresem.<br /><br /> Za pomocą polecenia **IP2MD** można `MethodDesc` uzyskać adres struktury z funkcji zarządzanej.|
|**DumpMT** [**-MD**] \< *MethodTable adres*>|Wyświetla informacje dotyczące tabeli metod pod podanym adresem. Określenie opcji **-MD** powoduje wyświetlenie listy wszystkich metod zdefiniowanych za pomocą obiektu.<br /><br /> Każdy obiekt zarządzany zawiera wskaźnik tabeli metod.|
|**DumpMethodSig** \< *sigaddr*> <*moduleadd*`r`>|Wyświetla informacje `MethodSig` o strukturze pod określonym adresem.|
|**DumpModule** [**-mt**] \< *Adres modułu*>|Wyświetla informacje dotyczące modułu pod podanym adresem. Opcja **-mt** wyświetla typy zdefiniowane w module oraz typy, do których odwołuje się moduł<br /><br /> Można użyć **DumpDomain** lub **DumpAssembly** polecenia, aby pobrać adres modułu.|
|**DumpObj** [**-nofields**] \< *adres obiektu*><br /><br /> — lub —<br /><br /> **Adres** \< *obiektu* DO>|Wyświetla informacje dotyczące obiektu pod podanym adresem. **Polecenie DumpObj** wyświetla pola, `EEClass` informacje o strukturze, tabelę metod i rozmiar obiektu.<br /><br /> Można użyć **Polecenia DumpStackObjects,** aby pobrać adres obiektu.<br /><br /> Należy zauważyć, że można uruchomić **DumpObj** polecenia na polach typu, `CLASS` ponieważ są one również obiekty.<br /><br /> Opcja `-` **nofields** zapobiega wyświetlaniu pól obiektu, jest przydatna w przypadku obiektów takich jak String.|
|**Typy dumpruntime**|Wyświetla obiekty typu środowiska uruchomieniowego w stercie modułu odśmiecania pamięci i wyświetla ich nazwy skojarzonych typów i tabele metod.|
|**DumpStack** [**-EE**] [`top` **-n**] [ *stos* `bottom` [ *stac*`k`]]|Wyświetla ślad stosu.<br /><br /> Opcja **-EE** powoduje, że polecenie **DumpStack** wyświetla tylko funkcje zarządzane. Użyj `top` parametrów i, `bottom` aby ograniczyć ramki stosu wyświetlane na platformach x86.<br /><br /> Opcja **-n** wyłącza wyświetlanie nazw plików źródłowych i numerów wierszy. Jeśli opcja debugera SYMOPT_LOAD_LINES jest określona, SOS będzie wyszukiwać symbole dla każdej ramki zarządzanej i jeśli wyszukiwanie zakończy się pomyślnie, wyświetlona zostanie odpowiadająca nazwa pliku źródłowego i numer wiersza. Można określić parametr **-n** (Brak numerów wierszy), aby wyłączyć to zachowanie.<br /><br /> Na platformach x86 i x64 polecenie **DumpStack** tworzy pełny ślad stosu.<br /><br /> Na platformach opartych na IA-64 polecenie **DumpStack** naśladuje polecenie **K** debugera. Parametry `top` `bottom` i parametry są ignorowane na platformach opartych na IA-64.|
|**DumpSig** \< *sigaddr*> \<*moduleaddr*>|Wyświetla informacje `Sig` o strukturze pod określonym adresem.|
|**DumpSigElem** \< *sigaddr*> \<*moduleaddr*>|Wyświetla jeden element obiektu podpisu. W większości przypadków należy użyć **DumpSig,** aby spojrzeć na poszczególne obiekty podpisu. Jednak jeśli podpis został uszkodzony w jakiś sposób, można użyć **DumpSigElem,** aby odczytać prawidłowe części.|
|**DumpStackObjects** [**-verify**`top` ]`bottom` [ *stos* [ *stos*]]<br /><br /> — lub —<br /><br /> **DSO** [**-verify**`top` ]`bottom` [ *stos* [ *stos*]]|Wyświetla wszystkie zarządzane obiekty znalezione w granicach bieżącego stosu.<br /><br /> Opcja **-verify** sprawdza poprawność każdego `CLASS` niestatycznego pola pola obiektu.<br /><br /> Użyj **polecenia DumpStackObject** z poleceniami śledzenia stosu, takimi jak polecenie **K** i **CLRStack,** aby określić wartości zmiennych lokalnych i parametrów.|
|> \<*Adres* **dumpVC** \< *MethodTable*>|Wyświetla informacje dotyczące pól klasy wartości pod podanym adresem.<br /><br /> **MethodTable** Parametr umożliwia **DumpVC** polecenia poprawnie interpretować pola. Klasy wartości nie posiadają tabeli metod jako ich pierwsze pole.|
|**EEHeap** [**-gc**] [**-loader**]|Wyświetla informacje o pamięci procesowej zużywanej przez wewnętrzne struktury danych CLR.<br /><br /> Opcje **-gc** i **-loader** ograniczają dane wyjściowe tego polecenia do struktur danych modułu zbierającego elementy bezużyteczne lub modułu ładującego.<br /><br /> Informacje dotyczące modułu odśmiecania pamięci wyświetlają zakresy każdego segmentu w zarządzanej stercie.  Jeśli wskaźnik mieści się w zakresie segmentu podanym przez **-gc,** wskaźnik jest wskaźnikiem obiektu.|
|**EEStack** [**-krótki**] [**-EE**]|Uruchamia **polecenie DumpStack** na wszystkich wątkach w procesie.<br /><br /> Opcja **-EE** jest przekazywana bezpośrednio do polecenia **DumpStack.** Parametr **-short** ogranicza dane wyjściowe do następujących rodzajów wątków:<br /><br /> Wątki, które uzyskały blokadę.<br /><br /> Wątki, które zostały zatrzymane w celu umożliwienia odśmiecenia pamięci.<br /><br /> Wątki, które są obecnie w kodzie zarządzanym.|
|**EEWersja**|Wyświetla wersję CLR.|
|**EHInfo** \<[*> adres MethodDesc]* [\<Adres*kodu*>]|Wyświetla bloki obsługi wyjątków w określonej metodzie.  To polecenie wyświetla adresy kodu i przesunięcia dla bloku `try` klauzul `catch` (bloku) i bloku obsługi (bloku).|
|**FAQ**|Wyświetla najczęściej zadawane pytania.|
|**FinalizeQueue** [**-detail**] &#124; [**-allReady**] [**-short**]|Wyświetla wszystkie obiekty zarejestrowane dla finalizacji.<br /><br /> Opcja **-detail** wyświetla dodatkowe `SyncBlocks` informacje o wszelkich, które muszą `RuntimeCallableWrappers` zostać oczyszczone, oraz o wszelkich (RCW), które czekają na oczyszczanie. Obie te struktury danych są buforowane i oczyszczane przez wątek finalizatora w trakcie jego działania.<br /><br /> Opcja `-allReady` wyświetla wszystkie obiekty, które są gotowe do finalizacji, niezależnie od tego, czy są one już oznaczone przez wyrzucania elementów bezużytecznych jako takie lub będą oznaczone przez następne wyrzucanie elementów bezużytecznych. Obiekty, które znajdują się na liście „gotowych do finalizacji”, są obiektami, które można sfinalizować i które nie są już zakorzenione. Ta opcja może być bardzo kosztowna, ponieważ weryfikuje, czy wszystkie obiekty w kolejkach, które można sfinalizować, są nadal zakorzenione.<br /><br /> Opcja `-short` ogranicza dane wyjściowe do adresu każdego obiektu. Jeśli jest używany w połączeniu z **-allReady**, wylicza wszystkie obiekty, które mają finalizatora, które nie są już zakorzenione. Jeśli jest używana samodzielnie, wyświetla listę wszystkich obiektów w kolejkach możliwych do sfinalizowania i „gotowych do finalizacji”.|
|*Adres obiektu* **FindAppDomain** \<>|Określa domenę aplikacji obiektu pod podanym adresem.|
|**FindRoots** **-gen** \< *N*> &#124; **-gen dowolny** \< *adres &#124;obiektu*>|Powoduje przerwanie debugowania w obiekcie debugowanym podczas kolejnego zbierania dla określonej generacji. Efekt jest resetowany natychmiast po wystąpieniu przerwania. Aby przerwać podczas kolejnego zbierania, należy ponownie wydać polecenie. * \<Adres obiektu>* formularza tego polecenia jest używany po wystąpieniu przerwy spowodowanej przez **-gen** lub **-gen.** W tym czasie debuggee jest w odpowiednim stanie **findroots** do identyfikowania katalogów głównych dla obiektów z bieżących potępionych pokoleń.|
|**GCHandles** [**-perdomena**]|Wyświetla statystyki dotyczące uchwytów modułu odśmiecania pamięci w procesie.<br /><br /> Opcja **-perdomain** rozmieszcza statystyki według domeny aplikacji.<br /><br /> Użyj **polecenia GCHandles,** aby znaleźć przecieki pamięci spowodowane przeciekami obsługi modułu zbierającego elementy bezużyteczne. Przykładowo wyciek pamięci występuje, gdy kod zachowuje dużą tablicę, ponieważ silny uchwyt modułu odśmiecania pamięci nadal na nią wskazuje, a uchwyt został odrzucony bez jej zwolnienia.|
|**GCHandleLeaks (GCHandleLeaks)**|Wyszukuje w pamięci dowolnych odwołań do silnych i przypiętych uchwytów modułu odśmiecania pamięci w procesie i wyświetla wyniki. Jeśli zostanie znaleziony dojście, polecenie **GCHandleLeaks** wyświetla adres odwołania. Jeśli uchwyt nie zostanie znaleziony w pamięci, polecenie wyświetli powiadomienie.|
|\<*Adres* *kodu*> **metody GCInfo** \<>|Wyświetla dane, które wskazują, kiedy rejestry lub lokalizacje stosu zawierają obiekty zarządzane. Jeśli występuje odśmiecanie pamięci, moduł musi znać lokalizacje odwołań do obiektów, aby móc je zaktualizować za pomocą nowych wartości wskaźnika obiektu.|
|**GCRoot** [**-nostacks**] \< *Adres obiektu*>|Wyświetla informacje dotyczące odwołań (lub korzeni) do obiektu pod podanym adresem.<br /><br /> Polecenie **GCRoot** sprawdza cały zarządzany stos i tabelę dojścia do uchwytów w innych obiektach i uchwytach na stosie. Każdy stos jest następnie przeszukiwany w celu znalezienia wskaźników do obiektów; kolejka finalizatorów również będzie przeszukiwana.<br /><br /> To polecenie nie określa, czy korzeń stosu jest nieprawidłowy lub odrzucony. Polecenia **CLRStack** i **U** można zdemontować ramkę, do której należy wartość lokalna lub argument, aby ustalić, czy katalog główny stosu jest nadal używany.<br /><br /> Opcja **-nostacks** ogranicza wyszukiwanie do uchwytów modułu zbierającego elementy bezużyteczne i obiektów osiągalnych.|
|**GCGdzie**  *\<adres obiektu>*|Wyświetla lokalizację i rozmiar przekazanego argumentu w stercie modułu odśmiecania pamięci. Gdy argument znajduje się w stercie zarządzanej, ale nie jest prawidłowym adresem obiektu, rozmiar zostanie wyświetlony jako 0 (zero).|
|**help** \<[*polecenie*>]`faq`[ ]|Wyświetla wszystkie dostępne polecenia, gdy parametr nie jest określony, lub wyświetla szczegółowe informacje pomocy dotyczące określonego polecenia.<br /><br /> Parametr `faq` wyświetla odpowiedzi na często zadawane pytania.|
|**HeapStat** [**-inclNiezawodowany** &#124; **-iu**]|Wyświetla rozmiary generacji dla każdej sterty i całkowitą ilość wolnego miejsca w każdej generacji na każdym stosie. Jeśli -**inclUnrooted** opcja jest określona, raport zawiera informacje o zarządzanych obiektów z sterty wyrzucania elementów bezużytecznych, który nie jest już zakorzenione.|
|**HistClear (HistClear)**|Zwalnia wszystkie zasoby używane `Hist` przez rodzinę poleceń.<br /><br /> Ogólnie rzecz biorąc nie trzeba jawnie wywoływać, `HistClear`ponieważ każdy `HistInit` czyści poprzednie zasoby.|
|**HistInit ( HistInit )**|Inicjuje struktury SOS z dziennika obciążenia zapisanego w obiekcie debugowanym.|
|**HistObj** * \<obj_address>*|Sprawdza wszystkie rekordy przeniesienia dziennika obciążenia i wyświetla łańcuch przeniesień modułu odśmiecania pamięci, które mogły doprowadzić do adresu przekazanego jako argument.|
|**HistObjZnaj obj_address**  *\<>*|Wyświetla wszystkie wpisy dziennika, które odwołują się do obiektu pod podanym adresem.|
|**>korzenia HistRoot** * \<*|Wyświetla informacje powiązane zarówno z promocjami, jak i przeniesieniami określonego korzenia.<br /><br /> Wartość korzenia może być użyta do śledzenia ruchu obiektu za pomocą modułu odśmiecania pamięci.|
|*Adres kodu* **IP2MD** \<>|Wyświetla `MethodDesc` strukturę pod określonym adresem w kodzie, który został skompilowany przez JIT.|
|`ListNearObj`(`lno` * \<* ) obj_address>|Wyświetla obiekty poprzedzające i następujące po określonym adresie. Polecenie wyszukuje adres w stercie modułu odśmiecania pamięci podobny do prawidłowego początku obiektu zarządzanego (na podstawie prawidłowej metody tabel) i obiektu następującego po adresie argumentu.|
|**MinidumpMode** [**0**] [**1**]|Uniemożliwia uruchamianie poleceń niebezpiecznych podczas używania minizrzutu.<br /><br /> Przekaż **0,** aby wyłączyć tę funkcję lub **1,** aby włączyć tę funkcję. Domyślnie wartość **MinidumpMode** jest ustawiona na **0**.<br /><br /> Minidumps utworzone za pomocą polecenia **.dump /m** lub polecenia **.dump** mają ograniczone dane specyficzne dla programu CLR i umożliwiają poprawne uruchamianie tylko podzbioru poleceń SOS. Niektóre polecenia mogą zakończyć się nieoczekiwanym błędem, ponieważ wymagane obszary pamięci nie są mapowane lub są tylko częściowo mapowane. Ta opcja chroni przed uruchamianiem poleceń niebezpiecznych w stosunku do minizrzutów.|
|Nazwa *modułu*> \< **Name2EE** \<*typ lub nazwa metody*><br /><br /> — lub —<br /><br /> >Nazwa *modułu* **Name2EE** \<**!** \< *nazwa typu lub metody*>|Wyświetla `MethodTable` strukturę `EEClass` i strukturę dla określonego typu lub metody w określonym module.<br /><br /> Określony moduł musi zostać załadowany w procesie.<br /><br /> Aby uzyskać właściwą nazwę typu, przejrzyj moduł za pomocą [pliku Ildasm.exe (IL Disassembler).](ildasm-exe-il-disassembler.md) Można również `*` przekazać jako parametr nazwy modułu do wyszukiwania wszystkich załadowanych modułów zarządzanych. Parametrem *nazwy modułu* może być również nazwa debugera `mscorlib` `image00400000`dla modułu, takiego jak lub .<br /><br /> To polecenie obsługuje składnię debugera systemu `module` > `!` < `type` Windows <>. Typ musi być w pełni kwalifikowany.|
|**ObjSize** \<[*Adres obiektu*>] &#124; [**-aggregate**] [**-stat**]|Wyświetla rozmiar określonego obiektu. Jeśli nie określisz żadnych parametrów, **ObjSize** polecenie wyświetla rozmiar wszystkich obiektów znalezionych w wątkach zarządzanych, wyświetla wszystkie dojścia modułu zbierającego elementy bezużyteczne w procesie i sumuje rozmiar wszystkich obiektów wskazanych przez te uchwyty. **ObjSize** polecenie zawiera rozmiar wszystkich obiektów podrzędnych oprócz obiektu nadrzędnego.<br /><br /> Opcja **-aggregate** może być używana w połączeniu z argumentem **-stat,** aby uzyskać szczegółowy widok typów, które są nadal zakorzenione. Za pomocą **!dumpheap -stat** i **!objsize -aggregate -stat**, można określić, które obiekty nie są już zakorzenione i zdiagnozować różne problemy z pamięcią.|
|**PrintException** [**-zagnieżdżone**] [**-linie**] [\<Adres obiektu*wyjątku*>]<br /><br /> — lub —<br /><br /> **PE** [**-zagnieżdżone**] [\<Adres obiektu*wyjątku*>]|Wyświetla i formatuje pola dowolnego obiektu <xref:System.Exception> uzyskanego z klasy pod określonym adresem. Jeśli adres nie zostanie określony, polecenie **PrintException** wyświetli ostatni wyjątek zgłoszony w bieżącym wątku.<br /><br /> Opcja **-nested** wyświetla szczegółowe informacje o zagnieżdżonych obiektach wyjątków.<br /><br /> Opcja **-lines** wyświetla informacje o źródle, jeśli są dostępne.<br /><br /> Za pomocą tego polecenia można `_stackTrace` sformatować i wyświetlić pole, które jest tablicą binarną.|
|**ProcInfo** [**-env**] [**-time**] [**-mem**]|Wyświetla zmienne środowiskowe dla procesu, czasu procesora dla jądra i statystyki użycia pamięci.|
|**RCWCleanupList** \< *ADRES RCWCleanupList*>|Wyświetla listę otok wywoływanych w czasie wykonywania pod określonym adresem, które czekają na oczyszczanie.|
|Nazwa*pliku* *podstawowa*> \< **savemodule** \<>|Zapisuje określony obraz, który jest załadowany do pamięci pod podanym adresem, do określonego pliku.|
|**SosFlush (SosFlush)**|Opróżnia wewnętrzną pamięć podręczną SOS.|
|**StopOnException** [**-derived**] [**-create** &#124; \< **-create2**]*Numer pseudojednostu* *wyjątku*> \<>|Powoduje zatrzymanie debugera, gdy określony wyjątek zostanie zgłoszony, ale kontynuuje działanie, gdy zgłaszane są inne wyjątki.<br /><br /> Opcja **pochodna** łapie określony wyjątek i każdy wyjątek, który wynika z określonego wyjątku.|
|**SyncBlk** [**-all** \<&#124; *syncblk numer*>]|Wyświetla określoną `SyncBlock` strukturę lub wszystkie `SyncBlock` struktury.  Jeśli nie przekażesz żadnych argumentów, polecenie `SyncBlock` **SyncBlk** wyświetla strukturę odpowiadającą obiektom, które są własnością wątku.<br /><br /> Struktura `SyncBlock` jest kontenerem dla dodatkowych informacji, które nie muszą być tworzone dla każdego obiektu. Może przechowywać dane międzyoperacyjnego modelu COM, kody skrótów i informacje dotyczące blokowania na potrzeby operacji bezpiecznych wątkowo.|
|**Threadpool**|Wyświetla informacje o puli wątków zarządzanych, w tym liczbę żądań pracy w kolejce, liczbę wątków portu zakończenia i liczbę czasomierzy.|
|Token **tokenu token2EE** \< *nazwa*> \<*modułu*>|Zamienia token określonych metadanych w `MethodTable` określonym `MethodDesc` module w strukturę lub strukturę.<br /><br /> Można przekazać `*` parametru nazwy modułu, aby znaleźć, co ten token mapuje w każdym załadowanym module zarządzanym. Można również przekazać nazwę debugera dla modułu, takiego jak `mscorlib` lub `image00400000`.|
|**Wątki** [**-live**] [**-special**]|Wyświetla wszystkie zarządzane wątki w procesie.<br /><br /> Polecenie **Wątki** wyświetla identyfikator skrócony debugera, identyfikator wątku CLR i identyfikator wątku systemu operacyjnego.  Ponadto polecenie **Wątki** wyświetla kolumnę Domain, która wskazuje domenę aplikacji, w której wykonuje się wątek, kolumnę APT, która wyświetla tryb mieszkania COM, oraz kolumnę Wyjątek, która wyświetla ostatni wyjątek zgłoszony w wątku.<br /><br /> Opcja **-live** wyświetla wątki skojarzone z wątkiem na żywo.<br /><br /> Opcja **-special** wyświetla wszystkie specjalne wątki utworzone przez CLR. Specjalne wątki obejmują wątki wyrzucania elementów bezużytecznych (w równoczesnych i serwera wyrzucania elementów bezużytecznych), debuger wątki pomocnicze, wątki finalizacji, <xref:System.AppDomain> zwalnianie wątków i wątki czasomierza puli wątków.|
|*Pole wartości stanu wątku* ** \< ****>**|Wyświetla stan wątku. Parametr `value` jest wartością `State` pola w danych wyjściowych raportu **Wątki.**<br /><br /> Przykład:<br /><br /> `0:003> !Threads     ThreadCount:      2     UnstartedThread:  0     BackgroundThread: 1     PendingThread:    0     DeadThread:       0     Hosted Runtime:   no                                           PreEmptive   GC Alloc           Lock            ID OSID ThreadOBJ    State     GC       Context       Domain   Count APT Exception        0    1  250 0019b068      a020 Disabled 02349668:02349fe8 0015def0     0 MTA        2    2  944 001a6020      b220 Enabled  00000000:00000000 0015def0     0 MTA (Finalizer)     0:003> !ThreadState b220         Legal to Join         Background         CLR Owns         CoInitialized         In Multi Threaded Apartment`|
|**TraverseHeap** [**-xml**] \< *nazwa pliku*>|Zapisuje informacje dotyczące sterty do określonego pliku w formacie zrozumiałym dla profilera CLR. Opcja **-xml** powoduje, że polecenie **TraverseHeap** formatuje plik jako XML.<br /><br /> Program CLR Profiler można pobrać z [Centrum pobierania Microsoft](https://go.microsoft.com/fwlink/?LinkID=67325).|
|**U** [**-gcinfo**] [**-ehinfo**] [**-n** \< \<] Adres metody *> &#124; * adres *kodu*>|Wyświetla dezespozyt z adnotacjami metody zarządzanej `MethodDesc` określoną przez wskaźnik struktury dla metody lub przez adres kodu w treści metody. Polecenie **U** wyświetla całą metodę od początku do końca, z adnotacjami, które konwertują tokeny metadanych na nazwy.<br /><br /> Opcja **-gcinfo** powoduje, że polecenie `GCInfo` **U** wyświetla strukturę metody.<br /><br /> Opcja **-ehinfo** wyświetla informacje o wyjątkach dla metody. Informacje te można również uzyskać za pomocą polecenia **EHInfo.**<br /><br /> Opcja **-n** wyłącza wyświetlanie nazw plików źródłowych i numerów wierszy. Jeśli opcja debugera SYMOPT_LOAD_LINES jest określona, SOS wyszukuje symbole dla każdej zarządzanej ramki i jeśli wyszukiwanie zakończy się pomyślnie, wyświetla odpowiadającą nazwę pliku źródłowego i numer wiersza. Można określić opcję **-n,** aby wyłączyć to zachowanie.|
|**VerifyHeap (weryfikuj)**|Sprawdza sterty modułu odśmiecania pamięci w poszukiwaniu objawów uszkodzeń i wyświetla znalezione błędy.<br /><br /> Uszkodzenie sterty może być spowodowane przez wywołania platformy, które są konstruowane niepoprawnie.|
|**SprawdźObj** \< *adres obiektu*>|Sprawdza, czy obiekt, który jest przekazywany jako argument posiada oznaki uszkodzenia.|
|**Vmmap**|Przechodzi wirtualną przestrzeń adresową i wyświetla typ ochrony stosowany do każdego regionu.|
|**VMStat (Stan VMStat)**|Dostarcza widok podsumowania wirtualnej przestrzeni adresowej, uporządkowany według typów ochrony stosowanych do pamięci (wolna, zarezerwowana, zatwierdzona, prywatna, mapowana, obrazów). Kolumna TOTAL wyświetla wynik z kolumny AVERAGE pomnożony przez kolumnę BLK COUNT.|

## <a name="remarks"></a>Uwagi

Rozszerzenie debugowania SOS umożliwia wyświetlanie informacji o kodzie, który jest uruchomiony wewnątrz clr. Przykładowo rozszerzenia debugowania SOS można użyć do wyświetlania informacji na temat zarządzanej sterty, wyszukiwania uszkodzeń sterty, wyświetlania typów danych wewnętrznych używanych przez środowisko uruchomieniowe i wyświetlania informacji o całym zarządzanym kodzie działającym wewnątrz środowiska uruchomieniowego.

Aby użyć rozszerzenia debugowania SOS w programie Visual Studio, zainstaluj [zestaw Windows Driver Kit (WDK)](/windows-hardware/drivers/download-the-wdk). Aby uzyskać informacje na temat zintegrowanego środowiska debugowania w programie Visual Studio, zobacz [Debugowanie środowisk](/windows-hardware/drivers/debugger/debuggers-in-the-debugging-tools-for-windows-package).

Rozszerzenie debugowania SOS można również użyć, ładując je do [debugera WinDbg.exe](/windows-hardware/drivers/debugger/debugger-download-tools) i wykonując polecenia w programie WinDbg.exe.

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

Następujące polecenie wyświetla zawartość tablicy pod `00ad28d0`adresem .  Wyświetlanie zaczyna się od drugiego elementu, a następnie wyświetlonych zostaje pięć kolejnych elementów.

```console
!dumparray -start 2 -length 5 -detail 00ad28d0
```

Następujące polecenie wyświetla zawartość zestawu pod `1ca248`adresem .

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

Następujące polecenie wyświetla `MethodDesc` strukturę `902f40`pod adresem .

```console
!dumpmd 902f40
```

Następujące polecenie wyświetla informacje o module `1caa50`pod adresem .

```console
!dumpmodule 1caa50
```

Następujące polecenie wyświetla informacje o obiekcie pod adresem `a79d40`.

```console
!DumpObj a79d40
```

Następujące polecenie wyświetla pola klasy wartości pod `00a79d9c` adresem przy użyciu `0090320c`tabeli metod pod adresem .

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

Następujące polecenie określa domenę aplikacji obiektu pod `00a79d98`adresem .

```console
!findappdomain 00a79d98
```

Następujące polecenie wyświetla wszystkie uchwyty modułu odśmiecania pamięci w bieżącym procesie.

```console
!gcinfo 5b68dbb8
```

Następujące polecenie wyświetla `MethodTable` `EEClass` i struktur `Main` dla metody `MainClass` w klasie `unittest.exe`w module .

```console
!name2ee unittest.exe MainClass.Main
```

Następujące polecenie wyświetla informacje o tokenie `02000003` metadanych `unittest.exe`pod adresem w module .

```console
!token2ee unittest.exe 02000003
```

## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
