---
title: MDbg.exe (Debuger wiersza polecenia w programie .NET Framework)
ms.date: 03/30/2017
helpviewer_keywords:
- command-line debugger [.NET Framework]
- MDbg.exe
ms.assetid: 28a3f509-07e2-4dbe-81df-874c5e969cc4
ms.openlocfilehash: 58502626fed6c9cee52acb673ae34f6024f78b9b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715754"
---
# <a name="mdbgexe-net-framework-command-line-debugger"></a>MDbg.exe (Debuger wiersza polecenia w programie .NET Framework)
Debuger wiersza polecenia programu .NET Framework ułatwia dostawcom narzędzi i deweloperom aplikacji znajdowanie i usuwanie błędów w programach, których platformą docelową jest środowisko uruchomieniowe języka wspólnego programu .NET Framework. To narzędzie używa interfejsu API debugowania środowiska uruchomieniowego w celu dostarczania usług debugowania. Za pomocą programu MDbg.exe można debugować tylko kod zarządzany; debugowanie kodu niezarządzanego jest nieobsługiwane.  
  
To narzędzie jest dostępne za pośrednictwem NuGet. Aby uzyskać informacje o instalacji, zobacz [MDbg 0.1.0](https://www.nuget.org/packages/MDbg/0.1.0). Aby uruchomić narzędzie, użyj konsoli Menedżera pakietów. Aby uzyskać więcej informacji na temat korzystania z konsoli Menedżera pakietów, zobacz artykuł [Konsoli Menedżera pakietów.](/nuget/tools/package-manager-console)
  
W wierszu Menedżera pakietów wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
MDbg [ProgramName[arguments]] [options]  
```  
  
## <a name="commands"></a>Polecenia  
 Gdy znajdujesz się w debugerze (zgodnie z monitem **mdbg>),** wpisz jedno z poleceń opisanych w następnej sekcji:  
  
 **polecenie** [*argumenty*]  
  
 W poleceniach programu MDbg.exe jest rozróżniana wielkość liter.  
  
|Polecenie|Opis|  
|-------------|-----------------|  
|**ap**[**rocess**] [*liczba*]|Przełącza do innego debugowanego procesu lub drukuje dostępne procesy. Numery nie są rzeczywistymi identyfikatorami procesów (PID), ale numerami liczonymi od zera.|  
|**a**[**ttach**] [*pid*]|Dołącza do procesu lub drukuje dostępne procesy.|  
|**b**[**reak**] [*ClassName.Method* &#124; *Nazwa pliku:LineNo*]|Ustawia punkt przerwania w określonej metodzie. Moduły są skanowane sekwencyjnie.<br /><br /> -   **break** *FileName:LineNo* ustawia punkt przerwania w lokalizacji w źródle.<br />-   **break** *~number* ustawia punkt przerwania na symbolu ostatnio wyświetlanym za pomocą polecenia **x.**<br />-   **break** *moduł przerwy! ClassName.Method+IlOffset* ustawia punkt przerwania w pełni kwalifikowanej lokalizacji.|  
|**blok**[**ingObjects**]|Wyświetla blokady monitora, które blokują wątki.|  
|**ca**[**tch**] [*exceptionType*]|Powoduje, że debuger przerywa przy wszystkich wyjątkach, a nie tylko przy nieobsłużonych wyjątkach.|  
|**cl**[**earException**]|Oznacza bieżący wyjątek jako obsłużony, co umożliwia kontynuowanie wykonywania. Jeśli przyczyna wyjątku nie została usunięta, dany wyjątek może wkrótce zostać zgłoszony ponownie.|  
|**conf**[**ig**] [*wartość opcji*]|Wyświetla wszystkie opcje, które można skonfigurować, i pokazuje sposób wywoływania opcji bez wartości dodatkowych. Jeśli opcja jest określona, ustawia `value` jako bieżącą opcję. Obecnie dostępne są następujące opcje:<br /><br /> -   `extpath`ustawia ścieżkę wyszukiwania rozszerzeń, `load` gdy polecenie jest używane.<br />-   `extpath+`dodaje ścieżkę do ładowania rozszerzeń.|  
|**del**[**ete**]|Usuwa punkt przerwania.|  
|**de**[**tach**]|Odłącza od debugowanego procesu.|  
|**d**[**własne**] [*ramki*]|Przenosi aktywną ramkę stosu w dół.|  
|**echo**|Wyświetla komunikat na konsoli.|  
|**enableNotif**[**ication**] *typeName* 0&#124;1|Włącza (1) lub wyłącza (0) niestandardowe powiadomienia dla określonego typu.|  
|**ex**[**it**] [*exitcode*]|Kończy działanie powłoki programu MDbg.exe i opcjonalnie określa kod zakończenia procesu.|  
|**fo**[**zasięg**] [*OtherCommand*]|Wykonuje polecenie na wszystkich wątkach. *OtherCommand* jest prawidłowym poleceniem, które działa na jednym wątku; **foreach** *OtherCommand* wykonuje to samo polecenie na wszystkich wątkach.|  
|**f**[**unceval**]`-ad` [ *Num*] *functionName* [*args ...* ]|Wykonuje ocenę funkcji w bieżącym aktywnym wątku, gdzie funkcją do oceny jest *functionName*. Nazwa funkcji musi być w pełni kwalifikowana i zawierać przestrzenie nazw.<br /><br /> Opcja `-ad` określa domenę aplikacji, której należy użyć do rozwiązania tej funkcji. Jeśli `-ad` opcja nie jest określona, domena aplikacji dla rozpoznawania domyślnie domeny aplikacji, gdzie znajduje się wątek, który jest używany do oceny funkcji.<br /><br /> Jeśli funkcja, która jest oceniana nie jest statyczna, `this` pierwszy parametr przekazany w powinien być wskaźnikiem. Argumenty potrzebne do wykonania funkcji są wyszukiwane we wszystkich domenach aplikacji.<br /><br /> Aby zażądać wartości z domeny aplikacji, przedrostek zmiennej z nazwą domeny modułu i aplikacji; na przykład `funceval -ad 0 System.Object.ToString hello.exe#0!MyClass.g_rootRef`. To polecenie ocenia `System.Object.ToString` funkcję w `0`domenie aplikacji . Ponieważ `ToString` metoda jest funkcją wystąpienia, pierwszy `this` parametr musi być wskaźnikiem.|  
|**g**[**o**]|Powoduje, że program kontynuuje do czasu napotkania punktu przerwania, zakończenia działania programu lub napotkania zdarzenia (na przykład nieobsłużonego wyjątku) powodującego zatrzymanie programu.|  
|**h**[**elp**] [*polecenie*]<br /><br /> — lub —<br /><br /> **?** [*polecenie*]|Wyświetla opis wszystkich poleceń lub szczegółowy opis określonego polecenia.|  
|**ig**[**nore**] [*zdarzenie*]|Powoduje, że debuger zatrzymuje wykonywanie tylko w przypadku nieobsłużonych wyjątków.|  
|**int**[**ercept**] *FrameNumber*|Wycofuje debuger z powrotem do ramki o określonym numerze.<br /><br /> Jeśli debuger napotka wyjątek, za pomocą tego polecenia można wycofać debuger do ramki o określonym numerze. Stan programu można zmienić za pomocą polecenia **set** i kontynuować za pomocą polecenia **go.**|  
|**k**[**chory**]|Zatrzymuje aktywny proces.|  
|**l**[**ist**] [*moduły* &#124; *appdomains* &#124; *zespołów*]|Wyświetla załadowane moduły, domeny aplikacji lub zestawy.|  
|**lo**[**ad**] *assemblyName*|Ładuje rozszerzenie w następujący sposób: Określony zestaw jest ładowany i następnie `LoadExtension` podejmowana `Microsoft.Tools.Mdbg.Extension.Extension` jest próba uruchomienia metody statycznej z typu.|  
|**dziennik** [*eventType*]|Ustawia lub wyświetla zdarzenia do zarejestrowania.|  
|**mo**[**de**] [*opcja wł./wył.*]|Ustawia różne opcje debugera. Użyj `mode` bez opcji, aby uzyskać listę trybów debugowania i ich bieżące ustawienia.|  
|**mon**[**itorInfo**] *monitorReference*|Wyświetla informacje o blokadzie monitora obiektów.|  
|**newo**[**bj**] *typeName* [*argumenty...*]|Tworzy nowy obiekt *typu TypeName*.|  
|**n**[**wew]**|Uruchamia kod i przechodzi do następnego wiersza (nawet jeśli następny wiersz zawiera wiele wywołań funkcji).|  
|**Opendump** *pathToDumpFile*|Otwiera określony plik zrzutu na potrzeby debugowania.|  
|**o**[**ut**]|Przechodzi na koniec bieżącej funkcji.|  
|**pa**[**th**] [*pathName*]|Wyszukuje pliki źródłowe w określonej ścieżce, jeśli lokalizacja w plikach binarnych jest niedostępna.|  
|**p**[**rint**] [*var*] &#124; [`-d`]|Drukuje wszystkie zmienne w zakresie **(drukowanie),** drukuje określoną zmienną **(print** *var)* lub drukuje zmienne debugera **(drukowanie).**`-d`|  
|**printe**[**xception**] [*-r*]|Drukuje ostatni wyjątek w bieżącym wątku. Użyj `–r` opcji (cykliczne), aby przejść `InnerException` przez właściwość na obiekt wyjątku, aby uzyskać informacje o całym łańcuchu wyjątków.|  
|**pro**[**cessenum**]|Wyświetla aktywne procesy.|  
|**q**[**uit**] [*kod wyjścia*]|Zamyka powłokę programu MDbg.exe i opcjonalnie określa kod zakończenia procesu.|  
|**re**[**sume**]`*` [`~`&#124; [ ]*threadNumber*]|Wznawia bieżący wątek lub wątek określony przez *parametr threadNumber.*<br /><br /> Jeśli parametr *threadNumber* jest `*` określony w taki sposób, lub jeśli numer wątku zaczyna się od `~`, polecenie ma zastosowanie do wszystkich wątków z wyjątkiem wątku określonego przez *threadNumber*.<br /><br /> Wznowienie niewstrzymanego wątku nie przynosi żadnych efektów.|  
|**r****un**[ un`-d``ebug`] [ (`o`)`ptimize`&#124; - `-enc`( ) &#124;]*[path_to_exe*] [*args_to_exe*]]|Zatrzymuje bieżący proces (jeśli istnieje) i uruchamia nowy. Jeśli nie zostanie przekazany żaden argument wykonywalny, `run` to polecenie uruchamia program, który został wcześniej wykonany za pomocą polecenia. Jeśli dostarczono argument pliku wykonywalnego, określony program zostanie uruchomiony z użyciem opcjonalnie dostarczonych argumentów.<br /><br /> Jeśli zdarzenia ładowania klasy, ładowania modułu i uruchamiania wątku są ignorowane (ustawienie domyślne), program zatrzymuje działanie przy pierwszej instrukcji pliku wykonywalnego w wątku głównym.<br /><br /> Można wymusić, aby debuger wykonał kompilację kodu typu JIT (Just-In-Time), używając jednej z następujących trzech flag:<br /><br /> -   `-d`*(* `ebug` *)* wyłącza optymalizacje. Jest to flaga domyślna programu MDbg.exe.<br />-   `-o`*(* `ptimize` *)* wymusza kod do uruchomienia bardziej jak to robi poza debugerem, ale również sprawia, że debugowanie doświadczenie trudniejsze. Jest to flaga domyślna dla użycia poza debugerem.<br />-   `-enc`włącza funkcję Edycja i Kontynuuj, ale ponosi trafienie wydajności.|  
|**Ustawianie** *wartości* *zmiennej*=|Zmienia wartość dowolnej zmiennej w zakresie.<br /><br /> Można także tworzyć własne zmienne debugera i przypisywać im wartości referencyjne z poziomu aplikacji. Te wartości pełnią funkcję dojść do oryginalnej wartości, nawet jeśli oryginalna wartość znajduje się poza zakresem. Wszystkie zmienne debugera `$` muszą zaczynać się od (na przykład `$var`). Aby wyczyścić te dojścia, należy ustawić dla nich „nic”, używając następującego polecenia:<br /><br /> `set $var=`|  
|**Setip** `-il`[ ] *numer*|Ustawia bieżący wskaźnik instrukcji (IP) w pliku na określonej pozycji. Jeśli zostanie `-il` określona opcja, liczba reprezentuje przesunięcie języka pośredniego firmy Microsoft (MSIL) w metodzie. W przeciwnym wypadku numer reprezentuje numer wiersza źródłowego.|  
|**sh**[**ow**] [*linie*]|Określa liczbę wierszy do pokazania.|  
|**s**[**tep**]|Przenosi wykonywanie do następnej funkcji w bieżącym wierszu lub przechodzi do następnego wiersza, jeśli w danym wierszu nie ma funkcji do wykonania.|  
|**su****spend**[ spend\* ] [ &#124; [~]*threadNumber*]|Zawiesza bieżący wątek lub wątek określony przez *parametr threadNumber.*  Jeśli *threadNumber* jest `*`określony jako , polecenie stosuje się do wszystkich wątków. Jeśli numer wątku `~`zaczyna się od , polecenie ma zastosowanie do wszystkich wątków z wyjątkiem tego określonego przez *threadNumber*. Zawieszone wątki są wykluczone z uruchamiania, gdy proces jest uruchamiany przez **polecenie go** lub **step.** Jeśli w procesie nie ma żadnych nierozwieszanych wątków i wydasz polecenie **go,** proces nie będzie kontynuowany. W takim przypadku należy nacisnąć klawisze CTRL-C, aby przerwać działanie procesu.|  
|**sy**[**mbol**] *commandName* [*commandValue*]|Określa jedno z następujących poleceń:<br /><br /> -   `symbol path`[`"value"`] - Wyświetla lub ustawia bieżącą ścieżkę symbolu.<br />-   `symbol addpath``"value"` - Dodaje do bieżącej ścieżki symbolu.<br />-   `symbol reload`[`"module"`] - Przeładowuje wszystkie symbole lub symbole dla określonego modułu.<br />-   `symbol list`[`module`] - Pokazuje aktualnie załadowane symbole dla wszystkich modułów lub określonego modułu.|  
|**t**[**hread**] [*newThread*] [-*nick nick*`]`|Polecenie thread bez parametrów wyświetla wszystkie zarządzane wątki w bieżącym procesie. Wątki są zazwyczaj identyfikowane za pomocą numerów wątków, ale jeśli wątek ma przypisany pseudonim, jest on wyświetlany zamiast numeru. Za pomocą `-nick` parametru można przypisać pseudonim do wątku.<br /><br /> -   **thread** `-nick` *threadName* przypisuje pseudonim do aktualnie uruchomionego wątku.<br /><br /> Pseudonimy nie mogą być liczbami. Jeśli bieżący wątek ma już przypisany pseudonim, stary pseudonim jest zastępowany nowym. Jeśli nowy pseudonim jest ciągiem pustym (""), pseudonim dla bieżącego wątku jest usuwany, ale do wątku nie jest przypisywany nowy pseudonim.|  
|**u**[**p**]|Przenosi aktywną ramkę stosu w górę.|  
|**uwgc**[**uchwyt**] [*var*] &#124; [*adres*]|Drukuje zmienną śledzoną przez dojście. Dojście można określić przy użyciu nazwy lub adresu.|  
|**Kiedy**|Wyświetla aktualnie `when` aktywne instrukcje.<br /><br /> **po** **usunięciu wszystkich** &#124; `num` `num` [`num` [ ...]] `when` - Usuwa instrukcję określoną przez liczbę lub wszystkie `when` instrukcje, jeśli `all` jest określony.<br /><br /> **kiedy** `stopReason` `specific_condition`[ ]`cmd` `cmd` **do** `cmd` [ [ ...] ] - Parametr *stopReason* może być jedną z następujących czynności:<br /><br /> `StepComplete`, `ProcessExited`, `ThreadCreated`, `BreakpointHit`, `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ControlCTrapped`, `ExceptionThrown`, `UnhandledExceptionThrown`, `AsyncStop`, `AttachComplete`, `UserBreak`, `EvalComplete`, `EvalException`, `RemapOpportunityReached`, `NativeStop`.<br /><br /> *specific_condition* może być jedną z następujących czynności:<br /><br /> -   *liczba* - `ThreadCreated` `BreakpointHit`Dla i , wyzwala akcję tylko wtedy, gdy zostanie zatrzymana przez numer identyfikatora wątku/punktu przerwania o tej samej wartości.<br />-`!`[ ]*name* `AssemblyLoaded`- `AssemblyUnloaded` `ExceptionThrown`For `ModuleLoaded` `UnhandledExceptionThrown`, `ClassLoaded`, , , , , i , wyzwala akcję tylko wtedy, gdy nazwa pasuje do nazwy *stopReason*.<br /><br /> *specific_condition* musi być pusta dla innych wartości *stopReason*.|  
|**w****here**[ tutaj`-v`]`-c` [ ] [ *głębokość*] [*threadID*]|Wyświetla informacje debugowania dotyczące ramek stosu.<br /><br /> - `-v` Opcja zawiera pełne informacje o każdej wyświetlanej ramce stosu.<br />- Określanie liczby `depth` limitów, ile ramek jest wyświetlanych. Użyj **polecenia all,** aby wyświetlić wszystkie klatki. Wartość domyślna to 100.<br />- Jeśli określisz *threadID* parametr, można kontrolować, który wątek jest skojarzony ze stosem. Domyślnie jest to bieżący wątek. Użyj **polecenia all,** aby uzyskać wszystkie wątki.|  
|**x** `-c`[*numSymbols*]`!`[*moduł*[*wzór*]]|Wyświetla funkcje, `pattern` które pasują do modułu.<br /><br /> Jeśli *numSymbols* jest określony, dane wyjściowe są ograniczone do określonej liczby. Jeśli `!` (wskazując wyrażenie regularne) nie jest określony dla *wzorca,* wszystkie funkcje są wyświetlane. Jeśli *moduł* nie jest dostarczany, wyświetlane są wszystkie załadowane moduły. Symbole*~#*( ) mogą być używane do ustawiania punktów przerwania za pomocą polecenia **break.**|  
  
## <a name="remarks"></a>Uwagi  
 Kompilowanie aplikacji przeznaczonej do debugowania z użyciem flag specyficznych dla kompilatora może spowodować, że kompilator wygeneruje symbole debugowania. Więcej informacji na temat tych flag znajduje się w dokumentacji kompilatora. Może debugować zoptymalizowane aplikacje, ale niektóre informacje debugowania będą niedostępne. Na przykład nie będzie widocznych wiele zmiennych lokalnych, a wiersze źródłowe będą niedokładne.  
  
 Po skompilowaniu aplikacji wpisz **mdbg** w wierszu polecenia, aby rozpocząć sesję debugowania, jak pokazano w poniższym przykładzie.  
  
```console  
C:\Program Files\Microsoft Visual Studio 8\VC>mdbg  
MDbg (Managed debugger) v2.0.50727.42 (RTM.050727-4200) started.  
Copyright (C) Microsoft Corporation. All rights reserved.  
  
For information about commands type "help";  
to exit program type "quit".  
mdbg>  
```  
  
 Monit `mdbg>` wskazuje, że znajdujesz się w debugerze.  
  
 Po otwarciu debugera można używać poleceń i argumentów opisanych w poprzedniej sekcji.  
  
## <a name="see-also"></a>Zobacz też

- [narzędzia](index.md)
- [Wiersz polecenia](developer-command-prompt-for-vs.md)
