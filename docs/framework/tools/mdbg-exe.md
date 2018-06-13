---
title: MDbg.exe (Debuger wiersza polecenia w programie .NET Framework)
ms.date: 03/30/2017
helpviewer_keywords:
- command-line debugger [.NET Framework]
- MDbg.exe
ms.assetid: 28a3f509-07e2-4dbe-81df-874c5e969cc4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be32659a270cd7c6b7e3551594934926eabf0d31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399772"
---
# <a name="mdbgexe-net-framework-command-line-debugger"></a>MDbg.exe (Debuger wiersza polecenia w programie .NET Framework)
Debuger wiersza polecenia programu .NET Framework ułatwia dostawcom narzędzi i deweloperom aplikacji znajdowanie i usuwanie błędów w programach, których platformą docelową jest środowisko uruchomieniowe języka wspólnego programu .NET Framework. To narzędzie używa interfejsu API debugowania środowiska uruchomieniowego w celu dostarczania usług debugowania. Za pomocą programu MDbg.exe można debugować tylko kod zarządzany; debugowanie kodu niezarządzanego jest nieobsługiwane.  
  
 To narzędzie jest dostępna za pośrednictwem pakietu NuGet. Aby uzyskać informacje dotyczące instalacji, zobacz [MDbg 0.1.0](http://www.nuget.org/packages/MDbg/0.1.0). Aby uruchomić narzędzie, użyj konsoli Menedżera pakietów. Aby uzyskać więcej informacji za pomocą konsoli Menedżera pakietów, zobacz [przy użyciu konsoli Menedżera pakietów](http://docs.nuget.org/docs/start-here/Using-the-Package-Manager-Console).  
  
 Wpisz następujące polecenie w wierszu polecenia Menedżera pakietów:  
  
## <a name="syntax"></a>Składnia  
  
```  
MDbg [ProgramName[arguments]] [options]  
```  
  
## <a name="commands"></a>Polecenia  
 Jeśli jesteś w debugerze (wskazywanego przez **mdbg >** wiersza), wpisz jedno z poleceń opisanych w następnej sekcji:  
  
 **polecenie** [*argumenty*]  
  
 W poleceniach programu MDbg.exe jest rozróżniana wielkość liter.  
  
|Polecenie|Opis|  
|-------------|-----------------|  
|**region**[**Przetwarzaj**] [*numer*]|Przełącza do innego debugowanego procesu lub drukuje dostępne procesy. Numery nie są rzeczywistymi identyfikatorami procesów (PID), ale numerami liczonymi od zera.|  
|**a**[**Dołącz**] [*pid*]|Dołącza do procesu lub drukuje dostępne procesy.|  
|**b**[**DZIEL**] [*ClassName.Method* &#124; *FileName:LineNo*]|Ustawia punkt przerwania w określonej metodzie. Moduły są skanowane sekwencyjnie.<br /><br /> -   **podział** *FileName:LineNo* ustawia punkt przerwania w lokalizacji w źródle.<br />-   **podział** *~ numer* ustawia punkt przerwania na symbol ostatnio wyświetlane **x** polecenia.<br />-   **podział** *modułu! ClassName.Method+IlOffset* ustawia w pełni kwalifikowaną lokalizacji punktu przerwania.|  
|**blok**[**ingObjects**]|Wyświetla blokady monitora, które blokują wątki.|  
|**Urząd certyfikacji**[**asuj**] [*exceptionType*]|Powoduje, że debuger przerywa przy wszystkich wyjątkach, a nie tylko przy nieobsłużonych wyjątkach.|  
|**Cl**[**earException**]|Oznacza bieżący wyjątek jako obsłużony, co umożliwia kontynuowanie wykonywania. Jeśli przyczyna wyjątku nie została usunięta, dany wyjątek może wkrótce zostać zgłoszony ponownie.|  
|**conf**[**ig**] [*wartość opcji*]|Wyświetla wszystkie opcje, które można skonfigurować, i pokazuje sposób wywoływania opcji bez wartości dodatkowych. Jeśli opcja jest określona, ustawia `value` jako bieżącą opcją. Obecnie dostępne są następujące opcje:<br /><br /> -   `extpath` Ustawia ścieżkę wyszukiwania dla rozszerzeń po `load` używane jest polecenie.<br />-   `extpath+` dodaje ścieżkę ładowania rozszerzeń.|  
|**del**[**ete**]|Usuwa punkt przerwania.|  
|**Niemcy**[**tach**]|Odłącza od debugowanego procesu.|  
|**d**[**własnych**] [*ramki*]|Przenosi aktywną ramkę stosu w dół.|  
|**Echo**|Wyświetla komunikat na konsoli.|  
|**enableNotif**[**uwierzytelnianie**] *typeName* 0&#124;1|Włącza (1) lub wyłącza (0) niestandardowe powiadomienia dla określonego typu.|  
|**ex**[**on**] [*exitcode*]|Kończy działanie powłoki programu MDbg.exe i opcjonalnie określa kod zakończenia procesu.|  
|**FO**[**osiągnąć**] [*OtherCommand*]|Wykonuje polecenie na wszystkich wątkach. *OtherCommand* jest poprawne polecenie, który działa w jednym wątku; **foreach** *OtherCommand* dokonuje tego samego polecenia wszystkie wątki.|  
|**f**[**unceval**] [`-ad` *Num*] *functionName* [*argumentów...*  ]|Wykonuje obliczania funkcji w bieżącym wątku active w przypadku funkcji w celu oceny *functionName*. Nazwa funkcji musi być w pełni kwalifikowana i zawierać przestrzenie nazw.<br /><br /> `-ad` Opcji określa domenę aplikacji na potrzeby rozpoznać funkcji. Jeśli `-ad` opcji nie zostanie określony, domyślnie domeny aplikacji do rozpoznawania domeny aplikacji, w której znajduje się wątek, który służy do obliczania funkcji.<br /><br /> Jeśli funkcji, które jest oceniane nie jest statyczny, powinien być pierwszy parametr przekazano `this` wskaźnika. Argumenty potrzebne do wykonania funkcji są wyszukiwane we wszystkich domenach aplikacji.<br /><br /> Aby poprosić o wartości z domeny aplikacji, prefiks zmienna o nazwie domeny modułu i aplikacji; na przykład `funceval -ad 0 System.Object.ToString hello.exe#0!MyClass.g_rootRef`. To polecenie ocenia funkcji `System.Object.ToString` w domenie aplikacji `0`. Ponieważ `ToString` metody jest funkcją wystąpienia, musi być pierwszym parametrem `this` wskaźnika.|  
|**g**[**o**]|Powoduje, że program kontynuuje do czasu napotkania punktu przerwania, zakończenia działania programu lub napotkania zdarzenia (na przykład nieobsłużonego wyjątku) powodującego zatrzymanie programu.|  
|**h**[**elp**] [*polecenia*]<br /><br /> —lub—<br /><br /> **?** [*polecenia*]|Wyświetla opis wszystkich poleceń lub szczegółowy opis określonego polecenia.|  
|**Ig**[**noruj**] [*zdarzeń*]|Powoduje, że debuger zatrzymuje wykonywanie tylko w przypadku nieobsłużonych wyjątków.|  
|**int**[**ercept**] *FrameNumber*|Wycofuje debuger z powrotem do ramki o określonym numerze.<br /><br /> Jeśli debuger napotka wyjątek, za pomocą tego polecenia można wycofać debuger do ramki o określonym numerze. Stan programu można zmienić za pomocą **ustawić** polecenia i Kontynuuj przy użyciu **Przejdź** polecenia.|  
|**k**[**dotknięty**]|Zatrzymuje aktywny proces.|  
|**l**[**ist**] [*modułów* &#124; *domen* &#124; *zestawy*]|Wyświetla załadowane moduły, domeny aplikacji lub zestawy.|  
|**Lo**[**ad**] *assemblyName*|Ładuje rozszerzenie w następujący sposób: określony zestaw jest ładowany, a następnie próby uruchomienia metody statycznej `LoadExtension` z `Microsoft.Tools.Mdbg.Extension.Extension` typu.|  
|**Dziennik** [*eventType*]|Ustawia lub wyświetla zdarzenia do zarejestrowania.|  
|**mo**[**de**] [*opcję Włącz/Wyłącz*]|Ustawia różne opcje debugera. Użyj `mode` bez żadnych opcji, aby uzyskać listę trybów debugowania i ich ustawienia.|  
|**MON**[**itorInfo**] *monitorReference*|Wyświetla informacje o blokadzie monitora obiektów.|  
|**newo**[**bj**] *typeName* [*argumenty...* ]|Tworzy nowy obiekt typu *typeName*.|  
|**n**[**ext**]|Uruchamia kod i przechodzi do następnego wiersza (nawet jeśli następny wiersz zawiera wiele wywołań funkcji).|  
|**Opendump** *pathToDumpFile*|Otwiera określony plik zrzutu na potrzeby debugowania.|  
|**o**[**ut**]|Przechodzi na koniec bieżącej funkcji.|  
|**Pa**[**th**] [*pathName*]|Wyszukuje pliki źródłowe w określonej ścieżce, jeśli lokalizacja w plikach binarnych jest niedostępna.|  
|**p**[**drukowanie**] [*var*] &#124; [`-d`]|Wyświetla wszystkie zmienne w zakresie (**drukowanie**), drukuje określonej zmiennej (**drukowanie** *var*), lub zmiennych debugera (**drukowanie** `-d`).|  
|**printe**[**Włącz**] [*- r*]|Drukuje ostatni wyjątek w bieżącym wątku. Użyj `–r` opcję (rekursywnie), aby przechodzić między nimi `InnerException` właściwości w obiekcie wyjątek, aby uzyskać informacje dotyczące całego łańcucha wyjątków.|  
|**Pro**[**cessenum**]|Wyświetla aktywne procesy.|  
|**q**[**uit**] [*exitcode*]|Zamyka powłokę programu MDbg.exe i opcjonalnie określa kod zakończenia procesu.|  
|**re**[**Wznów**] [`*` &#124; [`~`]*threadNumber*]|Wznawia bieżącego wątku lub określony przez wątek *threadNumber* parametru.<br /><br /> Jeśli *threadNumber* parametr jest określony jako `*` lub jeśli rozpoczyna się od liczby wątków `~`, polecenie dotyczy wszystkich wątków, z wyjątkiem jednej, określonej przez *threadNumber*.<br /><br /> Wznowienie niewstrzymanego wątku nie przynosi żadnych efektów.|  
|**r**[**un**] [`-d`(`ebug`) &#124; -`o`(`ptimize`) &#124; `-enc`] [[*path_to_exe*] [*argumentów _to_exe*]]|Zatrzymuje bieżący proces (jeśli istnieje) i uruchamia nowy. Jeżeli nie przekazano żadnego argumentu dla pliku wykonywalnego, to polecenie uruchamia program, który wcześniej wykonano `run` polecenia. Jeśli dostarczono argument pliku wykonywalnego, określony program zostanie uruchomiony z użyciem opcjonalnie dostarczonych argumentów.<br /><br /> Jeśli zdarzenia ładowania klasy, ładowania modułu i uruchamiania wątku są ignorowane (ustawienie domyślne), program zatrzymuje działanie przy pierwszej instrukcji pliku wykonywalnego w wątku głównym.<br /><br /> Można wymusić, aby debuger wykonał kompilację kodu typu JIT (Just-In-Time), używając jednej z następujących trzech flag:<br /><br /> -   `-d` *(* `ebug` *)* wyłącza optymalizacje. Jest to flaga domyślna programu MDbg.exe.<br />-   `-o` *(* `ptimize` *)* wymusza kod, aby uruchomić więcej takich jak jest poza debugerem, ale również utrudnia działanie debugowania. Jest to flaga domyślna dla użycia poza debugerem.<br />-   `-enc` Włącza funkcję Edytuj i Kontynuuj, ale ponosi trafień wydajności.|  
|**Ustaw** *zmiennej*=*wartości*|Zmienia wartość dowolnej zmiennej w zakresie.<br /><br /> Można także tworzyć własne zmienne debugera i przypisywać im wartości referencyjne z poziomu aplikacji. Te wartości pełnią funkcję dojść do oryginalnej wartości, nawet jeśli oryginalna wartość znajduje się poza zakresem. Wszystkie zmienne debuger musi rozpoczynać się od `$` (na przykład `$var`). Aby wyczyścić te dojścia, należy ustawić dla nich „nic”, używając następującego polecenia:<br /><br /> `set $var=`|  
|**Operacja SetIP** [`-il`] *numer*|Ustawia bieżący wskaźnik instrukcji (IP) w pliku na określonej pozycji. Jeśli określisz `-il` opcji numer reprezentuje język pośredni firmy Microsoft (MSIL) przesunięcie w metodzie. W przeciwnym wypadku numer reprezentuje numer wiersza źródłowego.|  
|**ud**[**onowne**] [*wierszy*]|Określa liczbę wierszy do pokazania.|  
|**s**[**rok**]|Przenosi wykonywanie do następnej funkcji w bieżącym wierszu lub przechodzi do następnego wiersza, jeśli w danym wierszu nie ma funkcji do wykonania.|  
|**su**[**spędzają**] [\* &#124; [~]*threadNumber*]|Wstrzymuje bieżącego wątku lub określony przez wątek *threadNumber* parametru.  Jeśli *threadNumber* jest określony jako `*`, polecenie dotyczy wszystkich wątków. Jeśli liczba wątków rozpoczyna się od `~`, polecenie dotyczy wszystkich wątków, z wyjątkiem jednej, określonej przez *threadNumber*. Wstrzymane wątki są wykluczone z uruchomiona po uruchomieniu procesu przez **Przejdź** lub **krok** polecenia. Jeśli istnieją nie-zawieszone wątków w procesie i wystawiane **Przejdź** polecenia, proces nie będzie kontynuowana. W takim przypadku należy nacisnąć klawisze CTRL-C, aby przerwać działanie procesu.|  
|**sy**[**mbol**] *commandName* [*commandValue*]|Określa jedno z następujących poleceń:<br /><br /> -   `symbol path` [`"``value``"`]-Wyświetla lub ustawia bieżącej ścieżki symboli.<br />-   `symbol addpath` `"` `value` `"` -Dodaje do bieżącej ścieżki symboli.<br />-   `symbol reload` [`"``module``"`]-Ponownie ładuje wszystkie symbole lub symbole dla określonego modułu.<br />-   `symbol list` [`module`]-Pokazuje aktualnie załadowanych symboli dla wszystkich modułów lub określony moduł.|  
|**t**[**Kasuj**] [*newThread*] [-*nick pseudonim*`]`|Polecenie thread bez parametrów wyświetla wszystkie zarządzane wątki w bieżącym procesie. Wątki są zazwyczaj identyfikowane za pomocą numerów wątków, ale jeśli wątek ma przypisany pseudonim, jest on wyświetlany zamiast numeru. Można użyć `-nick` parametr, aby przypisać pseudonim do wątku.<br /><br /> -   **Wątek** `-nick` *threadName* przypisuje pseudonim aktualnie uruchomiony.<br /><br /> Pseudonimy nie mogą być liczbami. Jeśli bieżący wątek ma już przypisany pseudonim, stary pseudonim jest zastępowany nowym. Jeśli nowy pseudonim jest ciągiem pustym (""), pseudonim dla bieżącego wątku jest usuwany, ale do wątku nie jest przypisywany nowy pseudonim.|  
|**u**[**p**]|Przenosi aktywną ramkę stosu w górę.|  
|**uwgc**[**obsługi**] [*var*] &#124; [*adres*]|Drukuje zmienną śledzoną przez dojście. Dojście można określić przy użyciu nazwy lub adresu.|  
|**Kiedy**|Wyświetla aktualnie aktywny `when` instrukcje.<br /><br /> **gdy** **usunięcie wszystkich** &#124; `num` [`num` [`num` ...]] — usuwa `when` instrukcja określona przez liczbę lub wszystkich `when` instrukcje Jeśli `all` został określony.<br /><br /> **gdy** `stopReason` [`specific_condition`] **czy** `cmd` [`cmd` [`cmd` ...]] — *stopReason* parametr może być jedną z następujących czynności:<br /><br /> `StepComplete`, `ProcessExited`, `ThreadCreated`, `BreakpointHit`, `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ControlCTrapped`, `ExceptionThrown`, `UnhandledExceptionThrown`, `AsyncStop`, `AttachComplete`, `UserBreak`, `EvalComplete`, `EvalException`, `RemapOpportunityReached`, `NativeStop`.<br /><br /> *specific_condition* może być jedną z następujących czynności:<br /><br /> -   *numer* — `ThreadCreated` i `BreakpointHit`, wyzwala akcji tylko wtedy, gdy zatrzymana przez wątek identyfikator/przerwania numer tę samą wartość.<br />— [`!`]*nazwa* — `ModuleLoaded`, `ClassLoaded`, `AssemblyLoaded`, `AssemblyUnloaded`, `ExceptionThrown`, i `UnhandledExceptionThrown`, wyzwala akcji tylko wtedy, gdy nazwa odpowiada nazwie  *stopReason*.<br /><br /> *specific_condition* może być pusta dla innych wartości *stopReason*.|  
|**w**[**tutaj**] [`-v`] [`-c` *głębokość*] [*threadID*]|Wyświetla informacje debugowania dotyczące ramek stosu.<br /><br /> - `-v` Opcja zapewnia pełne informacje o każdej ramce stosu wyświetlane.<br />-Określenie liczbową `depth` ogranicza liczbę ramek są wyświetlane. Użyj **wszystkie** polecenie, aby wyświetlić wszystkie ramki. Wartość domyślna to 100.<br />— Jeśli określisz *threadID* parametru, można kontrolować, które wątku jest skojarzony z stosu. Domyślnie jest to bieżący wątek. Użyj **wszystkie** polecenie, aby pobrać wszystkie wątki.|  
|**x** [`-c`*numSymbols*] [*modułu*[`!`*wzorzec*]]|Wyświetla funkcje, które odpowiadają `pattern` dla modułu.<br /><br /> Jeśli *numSymbols* jest określony, dane wyjściowe są ograniczone do określonej liczby. Jeśli `!` (co oznacza wyrażenie regularne) nie jest określony dla *wzorzec*, wyświetlane są wszystkie funkcje. Jeśli *modułu* nie zostanie podany, wyświetlane są wszystkie moduły załadowane. Symbole (*~#*) można ustawić punktów przerwania za pomocą **podziału** polecenia.|  
  
## <a name="remarks"></a>Uwagi  
 Kompilowanie aplikacji przeznaczonej do debugowania z użyciem flag specyficznych dla kompilatora może spowodować, że kompilator wygeneruje symbole debugowania. Więcej informacji na temat tych flag znajduje się w dokumentacji kompilatora. Może debugować zoptymalizowane aplikacje, ale niektóre informacje debugowania będą niedostępne. Na przykład nie będzie widocznych wiele zmiennych lokalnych, a wiersze źródłowe będą niedokładne.  
  
 Po skompilowaniu aplikacji wpisz **mdbg** w wierszu polecenia, aby rozpocząć sesję debugowania, jak pokazano w poniższym przykładzie.  
  
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
