---
title: MDbg.exe (Debuger wiersza polecenia w programie .NET Framework)
ms.date: 03/30/2017
helpviewer_keywords:
- command-line debugger [.NET Framework]
- MDbg.exe
ms.assetid: 28a3f509-07e2-4dbe-81df-874c5e969cc4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2861d2364d2c29d15b25911524ef28aa78130913
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50034510"
---
# <a name="mdbgexe-net-framework-command-line-debugger"></a>MDbg.exe (Debuger wiersza polecenia w programie .NET Framework)
Debuger wiersza polecenia programu .NET Framework ułatwia dostawcom narzędzi i deweloperom aplikacji znajdowanie i usuwanie błędów w programach, których platformą docelową jest środowisko uruchomieniowe języka wspólnego programu .NET Framework. To narzędzie używa interfejsu API debugowania środowiska uruchomieniowego w celu dostarczania usług debugowania. Za pomocą programu MDbg.exe można debugować tylko kod zarządzany; debugowanie kodu niezarządzanego jest nieobsługiwane.  
  
To narzędzie jest dostępne za pośrednictwem pakietu NuGet. Aby uzyskać informacje dotyczące instalacji, zobacz [MDbg 0.1.0](https://www.nuget.org/packages/MDbg/0.1.0). Aby uruchomić narzędzie, należy użyć konsoli Menedżera pakietów. Aby uzyskać więcej informacji na temat używania konsoli Menedżera pakietów, zobacz [Konsola Menedżera pakietów](/nuget/tools/package-manager-console) artykułu.
  
W wierszu polecenia Menedżera pakietów wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```  
MDbg [ProgramName[arguments]] [options]  
```  
  
## <a name="commands"></a>Polecenia  
 Jeśli jesteś w debugerze (wskazane przez **mdbg >** wiersz), wpisz jedno z poleceń opisanych w następnej sekcji:  
  
 **polecenie** [*argumenty*]  
  
 W poleceniach programu MDbg.exe jest rozróżniana wielkość liter.  
  
|Polecenie|Opis|  
|-------------|-----------------|  
|**wschodni Region Azji i**[**rocesu**] [*numer*]|Przełącza do innego debugowanego procesu lub drukuje dostępne procesy. Numery nie są rzeczywistymi identyfikatorami procesów (PID), ale numerami liczonymi od zera.|  
|**a**[**Dołącz**] [*pid*]|Dołącza do procesu lub drukuje dostępne procesy.|  
|**b**[**reak**] [*ClassName.Method* &#124; *Nrwiersza*]|Ustawia punkt przerwania w określonej metodzie. Moduły są skanowane sekwencyjnie.<br /><br /> -   **podział** *Nrwiersza* ustawia punkt przerwania w określonej lokalizacji w źródle.<br />-   **podział** *~ numer* ustawia punkt przerwania przy symbolu, który został ostatnio wyświetlony za pomocą **x** polecenia.<br />-   **podział** *modułu! ClassName.Method+IlOffset* ustawia punkt przerwania w pełni kwalifikowanej lokalizacji.|  
|**blok**[**ingObjects**]|Wyświetla blokady monitora, które blokują wątki.|  
|**Urząd certyfikacji**[**hronę**] [*exceptionType*]|Powoduje, że debuger przerywa przy wszystkich wyjątkach, a nie tylko przy nieobsłużonych wyjątkach.|  
|**Cl**[**earException**]|Oznacza bieżący wyjątek jako obsłużony, co umożliwia kontynuowanie wykonywania. Jeśli przyczyna wyjątku nie została usunięta, dany wyjątek może wkrótce zostać zgłoszony ponownie.|  
|**Potwierdzenie**[**ig**] [*wartość opcji*]|Wyświetla wszystkie opcje, które można skonfigurować, i pokazuje sposób wywoływania opcji bez wartości dodatkowych. Jeśli ta opcja jest określona, ustawia `value` jako jej bieżącą opcję. Obecnie dostępne są następujące opcje:<br /><br /> -   `extpath` Ustawia ścieżkę wyszukiwania rozszerzeń po `load` polecenie jest używane.<br />-   `extpath+` dodaje ścieżkę do ładowania rozszerzeń.|  
|**del**[**ete**]|Usuwa punkt przerwania.|  
|**de**[**tach**]|Odłącza od debugowanego procesu.|  
|**d**[**własnych**] [*ramek*]|Przenosi aktywną ramkę stosu w dół.|  
|**Echo**|Wyświetla komunikat na konsoli.|  
|**enableNotif**[**ication**] *typeName* 0&#124;1|Włącza (1) lub wyłącza (0) niestandardowe powiadomienia dla określonego typu.|  
|**ex**[**go**] [*exitcode*]|Kończy działanie powłoki programu MDbg.exe i opcjonalnie określa kod zakończenia procesu.|  
|**FO**[**osiągnąć**] [*Innepolecenie*]|Wykonuje polecenie na wszystkich wątkach. *Innepolecenie* jest prawidłowym poleceniem, który działa w jednym wątku; **foreach** *Innepolecenie* wykonuje to polecenie we wszystkich wątkach.|  
|**f**[**unceval**] [`-ad` *Num*] *functionName* [*argumenty...*  ]|Wykonuje obliczenie funkcji na bieżącym aktywnym wątku, gdzie jest funkcja *functionName*. Nazwa funkcji musi być w pełni kwalifikowana i zawierać przestrzenie nazw.<br /><br /> `-ad` Opcja określa domenę aplikacji do użycia w celu rozpoznania funkcji. Jeśli `-ad` opcja nie zostanie określona, domeny aplikacji do rozpoznawania domyślnie będzie domeną aplikacji, w którym znajduje się wątek, który jest używany do obliczania funkcji.<br /><br /> Jeśli funkcja, która jest szacowana nie jest statyczna, pierwszy przekazywany parametr powinien być `this` wskaźnika. Argumenty potrzebne do wykonania funkcji są wyszukiwane we wszystkich domenach aplikacji.<br /><br /> Aby zażądać wartości z domeny aplikacji, należy poprzedzić zmienną nazwą modułu i nazwą domeny aplikacji; na przykład `funceval -ad 0 System.Object.ToString hello.exe#0!MyClass.g_rootRef`. To polecenie daje w wyniku funkcji `System.Object.ToString` w domenie aplikacji `0`. Ponieważ `ToString` metoda jest funkcją wystąpienia, pierwszy parametr musi być `this` wskaźnika.|  
|**g**[**o**]|Powoduje, że program kontynuuje do czasu napotkania punktu przerwania, zakończenia działania programu lub napotkania zdarzenia (na przykład nieobsłużonego wyjątku) powodującego zatrzymanie programu.|  
|**h**[**elp**] [*polecenia*]<br /><br /> —lub—<br /><br /> **?** [*polecenia*]|Wyświetla opis wszystkich poleceń lub szczegółowy opis określonego polecenia.|  
|**Ig**[**noruj**] [*zdarzeń*]|Powoduje, że debuger zatrzymuje wykonywanie tylko w przypadku nieobsłużonych wyjątków.|  
|**int**[**ercept**] *FrameNumber*|Wycofuje debuger z powrotem do ramki o określonym numerze.<br /><br /> Jeśli debuger napotka wyjątek, za pomocą tego polecenia można wycofać debuger do ramki o określonym numerze. Można zmienić stan programu, używając **ustaw** polecenia i Kontynuuj przy użyciu **Przejdź** polecenia.|  
|**k**[**ill**]|Zatrzymuje aktywny proces.|  
|**l**[**ISTA**] [*modułów* &#124; *domen aplikacji* &#124; *zestawy*]|Wyświetla załadowane moduły, domeny aplikacji lub zestawy.|  
|**Lo**[**ad**] *assemblyName*|Ładuje rozszerzenie w następujący sposób: ładowany jest określony zestaw, a następnie podejmowana jest próba uruchomienia statycznej metody `LoadExtension` z `Microsoft.Tools.Mdbg.Extension.Extension` typu.|  
|**Dziennik** [*Typzdarzenia*]|Ustawia lub wyświetla zdarzenia do zarejestrowania.|  
|**miesiąc**[**de**] [*opcję włączenia/wyłączenia*]|Ustawia różne opcje debugera. Użyj `mode` bez żadnych opcji, aby uzyskać listę trybów debugowania oraz ich bieżących ustawień.|  
|**MON**[**itorInfo**] *monitorReference*|Wyświetla informacje o blokadzie monitora obiektów.|  
|**newo**[**bj**] *typeName* [*argumenty...* ]|Tworzy nowy obiekt typu *typeName*.|  
|**n**[**ext**]|Uruchamia kod i przechodzi do następnego wiersza (nawet jeśli następny wiersz zawiera wiele wywołań funkcji).|  
|**Opendump** *pathToDumpFile*|Otwiera określony plik zrzutu na potrzeby debugowania.|  
|**o**[**ut**]|Przechodzi na koniec bieżącej funkcji.|  
|**Pa**[**th**] [*pathName*]|Wyszukuje pliki źródłowe w określonej ścieżce, jeśli lokalizacja w plikach binarnych jest niedostępna.|  
|**p**[**rukuj**] [*var*] &#124; [`-d`]|Drukuje wszystkie zmienne w zakresie (**drukowanie**), drukuje określoną zmienną (**drukowanie** *var*), lub drukuje zmienne debugera (**drukowanie** `-d`).|  
|**printe**[**wyjątków**] [*- r*]|Drukuje ostatni wyjątek w bieżącym wątku. Użyj `–r` (rekursywnie) opcja przechodzenia `InnerException` właściwości obiektu wyjątku w celu uzyskania informacji o całym łańcuchu wyjątków.|  
|**Pro**[**cessenum**]|Wyświetla aktywne procesy.|  
|**q**[**uit**] [*exitcode*]|Zamyka powłokę programu MDbg.exe i opcjonalnie określa kod zakończenia procesu.|  
|**ponownie**[**sume**] [`*` &#124; [`~`]*Numerwątku*]|Wznawia działanie bieżącego wątku lub wątku określonego przez *Numerwątku* parametru.<br /><br /> Jeśli *Numerwątku* parametr jest określony jako `*` lub jeśli numer wątku rozpoczyna się od `~`, polecenie jest stosowane do wszystkich wątków, z wyjątkiem określony przez *Numerwątku*.<br /><br /> Wznowienie niewstrzymanego wątku nie przynosi żadnych efektów.|  
|**r**[**un**] [`-d`(`ebug`) &#124; -`o`(`ptimize`) &#124; `-enc`] [[*path_to_exe*] [*argumentów _to_exe*]]|Zatrzymuje bieżący proces (jeśli istnieje) i uruchamia nowy. Jeśli żaden argument pliku wykonywalnego jest przekazywany, to polecenie uruchamia program, który wcześniej został wykonany przy użyciu `run` polecenia. Jeśli dostarczono argument pliku wykonywalnego, określony program zostanie uruchomiony z użyciem opcjonalnie dostarczonych argumentów.<br /><br /> Jeśli zdarzenia ładowania klasy, ładowania modułu i uruchamiania wątku są ignorowane (ustawienie domyślne), program zatrzymuje działanie przy pierwszej instrukcji pliku wykonywalnego w wątku głównym.<br /><br /> Można wymusić, aby debuger wykonał kompilację kodu typu JIT (Just-In-Time), używając jednej z następujących trzech flag:<br /><br /> -   `-d` *(* `ebug` *)* wyłącza optymalizacje. Jest to flaga domyślna programu MDbg.exe.<br />-   `-o` *(* `ptimize` *)* wymusza działanie więcej takich, jak jest poza debugerem, ale również utrudnia środowisko debugowania kodu. Jest to flaga domyślna dla użycia poza debugerem.<br />-   `-enc` Włącza funkcję Edytuj i Kontynuuj, ale wiąże się trafień wydajności.|  
|**Ustaw** *zmiennej*=*wartość*|Zmienia wartość dowolnej zmiennej w zakresie.<br /><br /> Można także tworzyć własne zmienne debugera i przypisywać im wartości referencyjne z poziomu aplikacji. Te wartości pełnią funkcję dojść do oryginalnej wartości, nawet jeśli oryginalna wartość znajduje się poza zakresem. Wszystkich zmiennych debugera muszą zaczynać się od `$` (na przykład `$var`). Aby wyczyścić te dojścia, należy ustawić dla nich „nic”, używając następującego polecenia:<br /><br /> `set $var=`|  
|**SetIP** [`-il`] *numer*|Ustawia bieżący wskaźnik instrukcji (IP) w pliku na określonej pozycji. Jeśli określisz `-il` opcji numer reprezentuje język Microsoft intermediate language (MSIL) przesunięcie w metodzie. W przeciwnym wypadku numer reprezentuje numer wiersza źródłowego.|  
|**SH**[**ow**] [*wierszy*]|Określa liczbę wierszy do pokazania.|  
|**s**[**rok**]|Przenosi wykonywanie do następnej funkcji w bieżącym wierszu lub przechodzi do następnego wiersza, jeśli w danym wierszu nie ma funkcji do wykonania.|  
|**su**[**wydatki**] [\* &#124; [~]*Numerwątku*]|Wstrzymuje działanie bieżącego wątku lub wątku określonego przez *Numerwątku* parametru.  Jeśli *Numerwątku* jest określony jako `*`, polecenie jest stosowane do wszystkich wątków. Jeśli numer wątku rozpoczyna się od `~`, polecenie jest stosowane do wszystkich wątków, z wyjątkiem określony przez *Numerwątku*. Wstrzymane wątki są wykluczane z uruchamiania, gdy proces jest uruchamiany przez **Przejdź** lub **kroku** polecenia. Jeśli istnieją wstrzymane wątki w procesie i wykonaniu **Przejdź** polecenia procesu nie będzie kontynuowana. W takim przypadku należy nacisnąć klawisze CTRL-C, aby przerwać działanie procesu.|  
|**sy**[**mbol**] *commandName* [*Wartośćpolecenia*]|Określa jedno z następujących poleceń:<br /><br /> -   `symbol path` [`"``value``"`] — Wyświetla lub ustawia bieżącą ścieżkę symboli.<br />-   `symbol addpath` `"` `value` `"` -Dodaje do bieżącej ścieżki symboli.<br />-   `symbol reload` [`"``module``"`] — Ponownie ładuje wszystkie symbole lub symbole dla określonego modułu.<br />-   `symbol list` [`module`] — Pokazuje aktualnie załadowane symbole dla wszystkich modułów lub określonego modułu.|  
|**t**[**Kasuj**] [*Nowywątek*] [-*nick pseudonim*`]`|Polecenie thread bez parametrów wyświetla wszystkie zarządzane wątki w bieżącym procesie. Wątki są zazwyczaj identyfikowane za pomocą numerów wątków, ale jeśli wątek ma przypisany pseudonim, jest on wyświetlany zamiast numeru. Możesz użyć `-nick` parametru, aby przypisać pseudonim wątku.<br /><br /> -   **Wątek** `-nick` *threadName* przypisuje pseudonim aktualnie uruchomionemu wątkowi.<br /><br /> Pseudonimy nie mogą być liczbami. Jeśli bieżący wątek ma już przypisany pseudonim, stary pseudonim jest zastępowany nowym. Jeśli nowy pseudonim jest ciągiem pustym (""), pseudonim dla bieżącego wątku jest usuwany, ale do wątku nie jest przypisywany nowy pseudonim.|  
|**u**[**p**]|Przenosi aktywną ramkę stosu w górę.|  
|**uwgc**[**obsługi**] [*var*] &#124; [*adres*]|Drukuje zmienną śledzoną przez dojście. Dojście można określić przy użyciu nazwy lub adresu.|  
|**Kiedy**|Wyświetla aktualnie aktywne `when` instrukcji.<br /><br /> **gdy** **usunąć wszystkie** &#124; `num` [`num` [`num` ...]] — usuwa `when` instrukcja określona przez numer lub wszystkie `when` instrukcji Jeśli `all` został określony.<br /><br /> **gdy** `stopReason` [`specific_condition`] **czy** `cmd` [`cmd` [`cmd` ...]] — *Przyczynazatrzymania* parametr może być jedną z następujących czynności:<br /><br /> `StepComplete`, `ProcessExited`, `ThreadCreated`, `BreakpointHit`, `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ControlCTrapped`, `ExceptionThrown`, `UnhandledExceptionThrown`, `AsyncStop`, `AttachComplete`, `UserBreak`, `EvalComplete`, `EvalException`, `RemapOpportunityReached`, `NativeStop`.<br /><br /> *specific_condition* może być jedną z następujących czynności:<br /><br /> -   *Liczba* — `ThreadCreated` i `BreakpointHit`, wyzwala akcję tylko wtedy, gdy jest zatrzymane przez wątek identyfikator/numer punktu przerwania o takiej samej wartości.<br />-[`!`]*nazwa* — `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ExceptionThrown`, i `UnhandledExceptionThrown`, wyzwala akcję tylko wtedy, gdy nazwa jest zgodna z nazwą  *Przyczynazatrzymania*.<br /><br /> *specific_condition* musi być pusta dla innych wartości parametru *Przyczynazatrzymania*.|  
|**w**[**tutaj**] [`-v`] [`-c` *głębokość*] [*threadID*]|Wyświetla informacje debugowania dotyczące ramek stosu.<br /><br /> `-v` Opcja zapewnia pełnych informacji na temat każdej wyświetlanej ramki stosu.<br />— Określając numer dla `depth` ogranicza liczbę ramek są wyświetlane. Użyj **wszystkich** polecenie, aby wyświetlić wszystkie ramki. Wartość domyślna to 100.<br />— W przypadku określenia *threadID* parametru, można kontrolować, który wątek będzie skojarzony ze stosem. Domyślnie jest to bieżący wątek. Użyj **wszystkich** polecenie, aby pobrać wszystkie wątki.|  
|**x** [`-c`*Symboleliczbowe*] [*modułu*[`!`*wzorzec*]]|Wyświetla funkcje pasujące `pattern` dla modułu.<br /><br /> Jeśli *Symboleliczbowe* jest określony, dane wyjściowe są ograniczone do określonej liczby. Jeśli `!` (wskazujący wyrażenie regularne) nie jest określona dla *wzorzec*, są wyświetlane wszystkie funkcje. Jeśli *modułu* nie zostanie podana, są wyświetlane wszystkie załadowane moduły. Symbole (*~#*) może służyć do ustawiania punktów przerwania przy użyciu **podziału** polecenia.|  
  
## <a name="remarks"></a>Uwagi  
 Kompilowanie aplikacji przeznaczonej do debugowania z użyciem flag specyficznych dla kompilatora może spowodować, że kompilator wygeneruje symbole debugowania. Więcej informacji na temat tych flag znajduje się w dokumentacji kompilatora. Może debugować zoptymalizowane aplikacje, ale niektóre informacje debugowania będą niedostępne. Na przykład nie będzie widocznych wiele zmiennych lokalnych, a wiersze źródłowe będą niedokładne.  
  
 Po skompilowaniu aplikacji wpisz **mdbg** w wierszu polecenia można uruchomić sesję debugowania, jak pokazano w poniższym przykładzie.  
  
```  
C:\Program Files\Microsoft Visual Studio 8\VC>mdbg  
MDbg (Managed debugger) v2.0.50727.42 (RTM.050727-4200) started.  
Copyright (C) Microsoft Corporation. All rights reserved.  
  
For information about commands type "help";  
to exit program type "quit".  
mdbg>  
```  
  
 `mdbg>` Wiersz wskazuje, że jesteś w debugerze.  
  
 Po otwarciu debugera można używać poleceń i argumentów opisanych w poprzedniej sekcji.  
  
## <a name="examples"></a>Przykłady  
  
## <a name="see-also"></a>Zobacz też  
 [Narzędzia](../../../docs/framework/tools/index.md)  
 [Wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
