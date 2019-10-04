---
title: MDbg.exe (Debuger wiersza polecenia w programie .NET Framework)
ms.date: 03/30/2017
helpviewer_keywords:
- command-line debugger [.NET Framework]
- MDbg.exe
ms.assetid: 28a3f509-07e2-4dbe-81df-874c5e969cc4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e2b8f96e9a042681642225ad4e644c6fd1f001cb
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044432"
---
# <a name="mdbgexe-net-framework-command-line-debugger"></a>MDbg.exe (Debuger wiersza polecenia w programie .NET Framework)
Debuger wiersza polecenia programu .NET Framework ułatwia dostawcom narzędzi i deweloperom aplikacji znajdowanie i usuwanie błędów w programach, których platformą docelową jest środowisko uruchomieniowe języka wspólnego programu .NET Framework. To narzędzie używa interfejsu API debugowania środowiska uruchomieniowego w celu dostarczania usług debugowania. Za pomocą programu MDbg.exe można debugować tylko kod zarządzany; debugowanie kodu niezarządzanego jest nieobsługiwane.  
  
To narzędzie jest dostępne za poorednictwem narzędzia NuGet. Aby uzyskać informacje o instalacji, zobacz [MDbg 0.1.0](https://www.nuget.org/packages/MDbg/0.1.0). Aby uruchomić narzędzie, należy użyć konsoli Menedżera pakietów. Więcej informacji o sposobach korzystania z konsoli Menedżera pakietów znajduje się w artykule dotyczącym [konsoli Menedżera pakietów](/nuget/tools/package-manager-console) .
  
W wierszu polecenia Menedżera pakietów wpisz następujące polecenie:  
  
## <a name="syntax"></a>Składnia  
  
```console  
MDbg [ProgramName[arguments]] [options]  
```  
  
## <a name="commands"></a>Polecenia  
 Gdy jesteś w debugerze (wskazanym przez monit **> MDbg** ), wpisz jedno z poleceń opisanych w następnej sekcji:  
  
 **polecenie** [*argumenty*]  
  
 W poleceniach programu MDbg.exe jest rozróżniana wielkość liter.  
  
|Polecenie|Opis|  
|-------------|-----------------|  
|**punkt dostępu** [**procesu**] [*Number*]|Przełącza do innego debugowanego procesu lub drukuje dostępne procesy. Numery nie są rzeczywistymi identyfikatorami procesów (PID), ale numerami liczonymi od zera.|  
|**a**[**Dołącz**] [*pid*]|Dołącza do procesu lub drukuje dostępne procesy.|  
|**b**[**reak**] [*ClassName.Method* &#124; *FileName:LineNo*]|Ustawia punkt przerwania w określonej metodzie. Moduły są skanowane sekwencyjnie.<br /><br /> -   **Przerwij** *Filename: NrWiersza* ustawia punkt przerwania w lokalizacji źródłowej.<br />-   **Przerwij** *wartość ~ Number* ustawia punkt przerwania w symbolu ostatnio wyświetlanym za pomocą polecenia **x** .<br />-   **Przerwij** *moduł! ClassName. Method + Przesunięcieil* ustawia punkt przerwania w w pełni kwalifikowanej lokalizacji.|  
|**Blokuj** [**ingObjects**]|Wyświetla blokady monitora, które blokują wątki.|  
|**urząd certyfikacji** [**hronę**] [*ExceptionType*]|Powoduje, że debuger przerywa przy wszystkich wyjątkach, a nie tylko przy nieobsłużonych wyjątkach.|  
|**CL** [**earException**]|Oznacza bieżący wyjątek jako obsłużony, co umożliwia kontynuowanie wykonywania. Jeśli przyczyna wyjątku nie została usunięta, dany wyjątek może wkrótce zostać zgłoszony ponownie.|  
|**conf** [**IG**] [*wartość opcji*]|Wyświetla wszystkie opcje, które można skonfigurować, i pokazuje sposób wywoływania opcji bez wartości dodatkowych. Jeśli opcja jest określona, ustawia `value` jako bieżącą opcję. Obecnie dostępne są następujące opcje:<br /><br /> -   `extpath`ustawia ścieżkę do wyszukiwania rozszerzeń, `load` gdy polecenie jest używane.<br />-   `extpath+`Dodaje ścieżkę do ładowania rozszerzeń.|  
|**del** [**suń**]|Usuwa punkt przerwania.|  
|**Usuń** [**dłącz**]|Odłącza od debugowanego procesu.|  
|**d** [**własny**] [*ramki*]|Przenosi aktywną ramkę stosu w dół.|  
|**ECHA**|Wyświetla komunikat na konsoli.|  
|**enableNotif** [**ikacji**] *Nazwa* typu&#124;0 1|Włącza (1) lub wyłącza (0) niestandardowe powiadomienia dla określonego typu.|  
|**np** . [**IT**] [*ExitCode*]|Kończy działanie powłoki programu MDbg.exe i opcjonalnie określa kod zakończenia procesu.|  
|**fo** [**zasięg**] [*OtherCommand*]|Wykonuje polecenie na wszystkich wątkach. *OtherCommand* jest prawidłowym poleceniem, które działa w jednym wątku; instrukcja **foreach** *OtherCommand* wykonuje to samo polecenie we wszystkich wątkach.|  
|**f** [**unceval**] [`-ad` *NUM*] *FunctionName* [*args...* ]|Wykonuje ocenę funkcji w bieżącym aktywnym wątku, gdzie funkcja do oceny jest *funkcją FunctionName*. Nazwa funkcji musi być w pełni kwalifikowana i zawierać przestrzenie nazw.<br /><br /> `-ad` Opcja określa domenę aplikacji, która ma być używana do rozpoznawania funkcji. Jeśli ta `-ad` opcja nie jest określona, domena aplikacji do rozpoznawania zostanie ustawiona domyślnie na domenę aplikacji, w której znajduje się wątek używany do oceny funkcji.<br /><br /> Jeśli Szacowana funkcja nie jest statyczna, pierwszy przeszedł parametr powinien być `this` wskaźnikiem. Argumenty potrzebne do wykonania funkcji są wyszukiwane we wszystkich domenach aplikacji.<br /><br /> Aby zażądać wartości z domeny aplikacji, należy prefiksować zmienną z modułem i nazwą domeny aplikacji; na przykład `funceval -ad 0 System.Object.ToString hello.exe#0!MyClass.g_rootRef`. To polecenie szacuje funkcję `System.Object.ToString` w domenie `0`aplikacji. Ponieważ metoda jest funkcją wystąpienia, pierwszy parametr musi `this` być wskaźnikiem. `ToString`|  
|**g**[**o**]|Powoduje, że program kontynuuje do czasu napotkania punktu przerwania, zakończenia działania programu lub napotkania zdarzenia (na przykład nieobsłużonego wyjątku) powodującego zatrzymanie programu.|  
|**h** [**ELP**] [*polecenie*]<br /><br /> —lub—<br /><br /> **?** [*polecenie*]|Wyświetla opis wszystkich poleceń lub szczegółowy opis określonego polecenia.|  
|**IG** [**noruj**] [*zdarzenie*]|Powoduje, że debuger zatrzymuje wykonywanie tylko w przypadku nieobsłużonych wyjątków.|  
|liczba **całkowita** [**ercept**] *Numerramki*|Wycofuje debuger z powrotem do ramki o określonym numerze.<br /><br /> Jeśli debuger napotka wyjątek, za pomocą tego polecenia można wycofać debuger do ramki o określonym numerze. Można zmienić stan programu przy użyciu polecenia **Set** i kontynuować przy użyciu polecenia **go** .|  
|**k**[**ill**]|Zatrzymuje aktywny proces.|  
|**l** [**ist**] [ *zestawy* *domen aplikacji* &#124; *modułów* &#124; ]|Wyświetla załadowane moduły, domeny aplikacji lub zestawy.|  
|**Lo** [**AD**] *AssemblyName*|Ładuje rozszerzenie w następujący sposób: Określony zestaw jest ładowany i podjęto próbę uruchomienia metody `LoadExtension` statycznej `Microsoft.Tools.Mdbg.Extension.Extension` z typu.|  
|**Dziennik** [*EventType*]|Ustawia lub wyświetla zdarzenia do zarejestrowania.|  
|**mo** [**de**] [*opcja włączona/wyłączona*]|Ustawia różne opcje debugera. Użyj `mode` programu bez opcji, aby uzyskać listę trybów debugowania i ich bieżących ustawień.|  
|**PN** [**itorInfo**] *odwołaniemonitora*|Wyświetla informacje o blokadzie monitora obiektów.|  
|**newo** [**BJ**] *Nazwa* typu [*argumenty...* ]|Tworzy nowy obiekt typu *TypeName*.|  
|**n** [**EXT**]|Uruchamia kod i przechodzi do następnego wiersza (nawet jeśli następny wiersz zawiera wiele wywołań funkcji).|  
|**Opendump** *pathToDumpFile*|Otwiera określony plik zrzutu na potrzeby debugowania.|  
|**o** [**UT**]|Przechodzi na koniec bieżącej funkcji.|  
|**PA** [**th**] [*nazwa_ścieżki*]|Wyszukuje pliki źródłowe w określonej ścieżce, jeśli lokalizacja w plikach binarnych jest niedostępna.|  
|**p** [**rukuj**] [*var*] &#124; [`-d`]|Drukuje wszystkie zmienne w zakresie (**Drukowanie**), drukuje określoną zmienną ( *wariancję* **drukowania** ) lub drukuje zmienne debugera (**drukowania**`-d`).|  
|**Drukuj** [**wyjątków**] [ *-r*]|Drukuje ostatni wyjątek w bieżącym wątku. Użyj opcji `InnerException` (rekursywnie), aby przejść przez właściwość obiektu Exception w celu uzyskania informacji na temat całego łańcucha wyjątków. `–r`|  
|**pakiet Pro** [**cessenum**]|Wyświetla aktywne procesy.|  
|**p** [**UIT**] [*ExitCode*]|Zamyka powłokę programu MDbg.exe i opcjonalnie określa kod zakończenia procesu.|  
|**re** [**sume**] [`*` &#124; []`~`*parametr NumerWątku*]|Wznawia bieżący wątek lub wątek określony przez parametr *parametr NumerWątku* .<br /><br /> Jeśli parametr *parametr NumerWątku* jest określony jako `*` lub, jeśli numer wątku rozpoczyna się od `~`, polecenie ma zastosowanie do wszystkich wątków, z wyjątkiem jednego określonego przez *parametr NumerWątku*.<br /><br /> Wznowienie niewstrzymanego wątku nie przynosi żadnych efektów.|  
|**r**[**un**] [`-d`(`ebug`) &#124; -`o`(`ptimize`) &#124;`-enc`] [[*path_to_exe*] [*args_to_exe*]]|Zatrzymuje bieżący proces (jeśli istnieje) i uruchamia nowy. Jeśli nie przekazano argumentu pliku wykonywalnego, to polecenie uruchamia program, który został wcześniej wykonany `run` przy użyciu polecenia. Jeśli dostarczono argument pliku wykonywalnego, określony program zostanie uruchomiony z użyciem opcjonalnie dostarczonych argumentów.<br /><br /> Jeśli zdarzenia ładowania klasy, ładowania modułu i uruchamiania wątku są ignorowane (ustawienie domyślne), program zatrzymuje działanie przy pierwszej instrukcji pliku wykonywalnego w wątku głównym.<br /><br /> Można wymusić, aby debuger wykonał kompilację kodu typu JIT (Just-In-Time), używając jednej z następujących trzech flag:<br /><br /> -   `-d` (`ebug` *)* wyłącza optymalizacje. Jest to flaga domyślna programu MDbg.exe.<br />-   `-o` (`ptimize` *)* wymusza, aby kod był uruchamiany w taki sposób, że nie jest on debugerem, ale również sprawia, że środowisko debugowania jest trudniejsze. Jest to flaga domyślna dla użycia poza debugerem.<br />-   `-enc`Włącza funkcję Edytuj i Kontynuuj, ale wiąże się z wydajnością.|  
|**Zestaw** *zmienna* = *wartość*|Zmienia wartość dowolnej zmiennej w zakresie.<br /><br /> Można także tworzyć własne zmienne debugera i przypisywać im wartości referencyjne z poziomu aplikacji. Te wartości pełnią funkcję dojść do oryginalnej wartości, nawet jeśli oryginalna wartość znajduje się poza zakresem. Wszystkie zmienne debugera muszą zaczynać `$` się od (na `$var`przykład). Aby wyczyścić te dojścia, należy ustawić dla nich „nic”, używając następującego polecenia:<br /><br /> `set $var=`|  
|**Operacja SetIP** [`-il`] *numer*|Ustawia bieżący wskaźnik instrukcji (IP) w pliku na określonej pozycji. W przypadku określenia `-il` opcji Liczba reprezentuje przesunięcie języka pośredniego firmy Microsoft (MSIL) w metodzie. W przeciwnym wypadku numer reprezentuje numer wiersza źródłowego.|  
|**SH** [**jak**] [*wiersze*]|Określa liczbę wierszy do pokazania.|  
|**s** [**rok**]|Przenosi wykonywanie do następnej funkcji w bieżącym wierszu lub przechodzi do następnego wiersza, jeśli w danym wierszu nie ma funkcji do wykonania.|  
|**Su** [**wydaj**] [\* &#124; [~]*parametr NumerWątku*]|Wstrzymuje bieżący wątek lub wątek określony przez parametr *parametr NumerWątku* .  Jeśli *parametr NumerWątku* jest określony jako `*`, polecenie ma zastosowanie do wszystkich wątków. Jeśli numer wątku rozpoczyna się od `~`, polecenie dotyczy wszystkich wątków, z wyjątkiem tych określonych przez *parametr NumerWątku*. Zawieszone wątki są wyłączone z uruchamiania, gdy proces jest uruchamiany za pomocą polecenia **go** lub **Step** . Jeśli nie ma żadnych niezawieszonych wątków w procesie i zostanie wydać polecenie **go** , proces nie będzie kontynuowany. W takim przypadku należy nacisnąć klawisze CTRL-C, aby przerwać działanie procesu.|  
|**sy** [**mbol**] *poleceniename* [*wartośćpolecenia*]|Określa jedno z następujących poleceń:<br /><br /> -   `symbol path`[`"value"`] — Wyświetla lub ustawia bieżącą ścieżkę symboli.<br />-   `symbol addpath``"value"` -Dodaje do bieżącej ścieżki symboli.<br />-   `symbol reload`[`"module"`] — Ponownie ładuje wszystkie symbole lub symbole dla określonego modułu.<br />-   `symbol list`[`module`] — Pokazuje aktualnie załadowane symbole dla wszystkich modułów lub określonego modułu.|  
|**t** [**hread**] [*newThread*] [-*nick pseudonim*`]`|Polecenie thread bez parametrów wyświetla wszystkie zarządzane wątki w bieżącym procesie. Wątki są zazwyczaj identyfikowane za pomocą numerów wątków, ale jeśli wątek ma przypisany pseudonim, jest on wyświetlany zamiast numeru. Możesz użyć parametru, `-nick` aby przypisać pseudonim do wątku.<br /><br /> -   **wątek** ThreadName przypisuje pseudonim do aktualnie działającego wątku. `-nick`<br /><br /> Pseudonimy nie mogą być liczbami. Jeśli bieżący wątek ma już przypisany pseudonim, stary pseudonim jest zastępowany nowym. Jeśli nowy pseudonim jest ciągiem pustym (""), pseudonim dla bieżącego wątku jest usuwany, ale do wątku nie jest przypisywany nowy pseudonim.|  
|**u**[**p**]|Przenosi aktywną ramkę stosu w górę.|  
|**uwgc** [**dojście**] [*var*] &#124; [*Address*]|Drukuje zmienną śledzoną przez dojście. Dojście można określić przy użyciu nazwy lub adresu.|  
|**czasie**|Wyświetla aktualnie aktywne `when` instrukcje.<br /><br /> **kiedy** **Usuń wszystko** &#124; `when` `all` [[...]] — Usuwa `when` instrukcję określoną przez liczbę lub wszystkie instrukcje, jeśli jest określony.`num` `num` `num`<br /><br /> **kiedy** `stopReason` []do`cmd` [[.`cmd` ..]] — parametr *parametru przyczynaZatrzymania* może mieć jedną z następujących wartości:`cmd` `specific_condition`<br /><br /> `StepComplete`, `ProcessExited`, `ThreadCreated`, `BreakpointHit`, `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ControlCTrapped`, `ExceptionThrown`, `UnhandledExceptionThrown`, `AsyncStop`, `AttachComplete`, `UserBreak`, `EvalComplete`, `EvalException`, `RemapOpportunityReached`, `NativeStop`.<br /><br /> *specific_condition* może być jedną z następujących:<br /><br /> -   *Liczba* -dla `ThreadCreated` i `BreakpointHit`, wyzwala akcję tylko wtedy, gdy jest zatrzymana przez identyfikator wątku/punkt przerwania z tą samą wartością.<br />-[`!`]*Nazwa* `ModuleLoaded`- `ClassLoaded` `AssemblyLoaded` dla,,`ExceptionThrown`,, i`UnhandledExceptionThrown`, wyzwala akcję tylko wtedy, gdy nazwa jest zgodna z nazwą *parametru przyczynaZatrzymania.* `AssemblyUnloaded`<br /><br /> *specific_condition* musi być pusty dla innych wartości *parametru przyczynaZatrzymania*.|  
|**w** [**tutaj**] [`-v`] [`-c` *głębokość*] [*threadID*]|Wyświetla informacje debugowania dotyczące ramek stosu.<br /><br /> `-v` -Opcja zawiera pełne informacje o każdej wyświetlonej ramce stosu.<br />— Określanie liczby w celu `depth` ograniczenia liczby wyświetlanych ramek. Użyj polecenia **wszystkie** , aby wyświetlić wszystkie ramki. Wartość domyślna to 100.<br />— W przypadku określenia parametru *threadID* można kontrolować, który wątek jest skojarzony ze stosem. Domyślnie jest to bieżący wątek. Użyj polecenia **All** , aby pobrać wszystkie wątki.|  
|**x** [`-c`*numSymbols*] [*moduł*[`!`*wzorzec*]]|Wyświetla funkcje, które pasują `pattern` do modułu.<br /><br /> Jeśli *numSymbols* jest określony, dane wyjściowe są ograniczone do podanej liczby. Jeśli `!` (wskazujące wyrażenie regularne) nie jest określony dla *wzorca*, wyświetlane są wszystkie funkcje. Jeśli nie podano *modułu* , zostaną wyświetlone wszystkie załadowane moduły. Symbole ( *~#* ) mogą służyć do ustawiania punktów przerwania za pomocą polecenia **Break** .|  
  
## <a name="remarks"></a>Uwagi  
 Kompilowanie aplikacji przeznaczonej do debugowania z użyciem flag specyficznych dla kompilatora może spowodować, że kompilator wygeneruje symbole debugowania. Więcej informacji na temat tych flag znajduje się w dokumentacji kompilatora. Może debugować zoptymalizowane aplikacje, ale niektóre informacje debugowania będą niedostępne. Na przykład nie będzie widocznych wiele zmiennych lokalnych, a wiersze źródłowe będą niedokładne.  
  
 Po skompilowaniu aplikacji wpisz **MDbg** w wierszu polecenia, aby rozpocząć sesję debugowania, jak pokazano w poniższym przykładzie.  
  
```console  
C:\Program Files\Microsoft Visual Studio 8\VC>mdbg  
MDbg (Managed debugger) v2.0.50727.42 (RTM.050727-4200) started.  
Copyright (C) Microsoft Corporation. All rights reserved.  
  
For information about commands type "help";  
to exit program type "quit".  
mdbg>  
```  
  
 `mdbg>` Monit wskazuje, że jesteś w debugerze.  
  
 Po otwarciu debugera można używać poleceń i argumentów opisanych w poprzedniej sekcji.  
  
## <a name="see-also"></a>Zobacz także

- [Narzędzia](index.md)
- [Wiersze polecenia](developer-command-prompt-for-vs.md)
