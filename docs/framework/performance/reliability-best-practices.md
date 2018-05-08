---
title: Najlepsze rozwiązania dotyczące niezawodności
ms.date: 03/30/2017
helpviewer_keywords:
- marking locks
- rebooting databases
- denial of service attacks
- back-out code
- SQL Server [.NET Framework], reliability
- synchronization, reliability
- single-threaded COM components
- slow leaks
- suspending threads
- asynchronous exception handling
- leaked resources [.NET Framework]
- unmanaged memory
- memory, reliability
- threading [.NET Framework], reliability
- process-wide domain shared states
- shared states
- SafeHandle class, reliability
- reliability contracts [.NET Framework]
- cleanup operations
- constrained execution regions
- CERs
- finalizers, reliability
- reliability [.NET Framework]
- blocks, reliability
- finally clauses
- cross-application domain shared states
- catch blocks
- identifying locks
- writing reliable code
- impersonation
- GC.KeepAlive method
- managed threading
- locks, reliability
- STA-dependent features
- fibers
ms.assetid: cf624c1f-c160-46a1-bb2b-213587688da7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d6f29d15297fc7faff6bb3bb07ee535647c2bb7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="reliability-best-practices"></a>Najlepsze rozwiązania dotyczące niezawodności
Następujące reguły niezawodności są ukierunkowane do programu SQL Server; jednak mają one również zastosowanie do aplikacji opartej na hoście serwera. Jest bardzo ważne, że serwery, takich jak SQL Server nie nastąpił przeciek zasobów i nie można przełączyć w dół.  Jednak, że nie można wykonać pisząc kod wycofujący się dla każdej metody, która zmienia stan obiektu.  Celem jest nie do pisania 100 procent niezawodnej zarządzanego kodu, który będzie odzyskanie wszystkich błędów w każdej lokalizacji kod wycofujący się.  Który będzie stanowić nie lada wyzwanie z małego prawdopodobieństwo pomyślnego.  Środowisko uruchomieniowe języka wspólnego (CLR) nie można łatwo udostępnić wystarczająco silne gwarancje z kodem zarządzanym aby pisanie kodu doskonałe możliwe.  Należy pamiętać, że w przeciwieństwie do programu ASP.NET, program SQL Server używa tylko jednego procesu, który nie może zostać odtworzona bez konieczności przełączania bazy danych w dół przez zbyt długi czas.  
  
 Te słabszych gwarancji i uruchomiony w ramach jednego procesu niezawodności jest oparta na przerywanie wątków lub odtwarzania domen aplikacji, gdy nie przedostają niezbędne oraz zdolności do przyjmowania środki ostrożności, aby zasoby systemu operacyjnego, takie jak dojść lub pamięci.  Nawet w przypadku tego ograniczenia niezawodność prostszy jest nadal wymagane znaczących niezawodności:  
  
-   Nigdy nie nastąpił przeciek zasoby systemu operacyjnego.  
  
-   Zidentyfikuj wszystkich zarządzanych blokad w wszystkich formularzy do środowiska CLR.  
  
-   Nigdy nie międzyaplikacyjnej podziału domeny udostępniony stan, dzięki czemu <xref:System.AppDomain> odtwarzania sprawnego funkcjonowania.  
  
 Chociaż teoretycznie można zapisać kodu zarządzanego do obsługi <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, i <xref:System.OutOfMemoryException> wyjątki, oczekiwano deweloperom zapisać takie niezawodny kod w całej aplikacji jest wysokie.  Z tego powodu wyjątki poza pasmem powoduje wykonywania wątku przerywane; i przerwał wątek został edycji stanu udostępnionego, której można ustalić przy czy wątek utrzymuje blokadę, a następnie <xref:System.AppDomain> zostanie zwolniona.  Jeżeli metodę, która jest edytowanie stanu udostępnionego zostanie zakończona, stan będzie uszkodzony, ponieważ nie jest możliwe do zapisu niezawodnej kod wycofujący aktualizacji stanu udostępnionego.  
  
 W programie .NET Framework w wersji 2.0 tylko hosta, który wymaga niezawodności jest program SQL Server.  Jeśli używanemu zestawowi zostanie uruchomiony na serwerze SQL dla każdej części tego zestawu, należy wykonać pracy niezawodności nawet w przypadku określonych funkcji, które są wyłączone podczas uruchamiania w bazie danych.  Jest to wymagane, ponieważ aparat analizy kodu sprawdza kod na poziomie zestawu i nie rozróżnianie wyłączone kodu. Inny serwer SQL programowania to, że program SQL Server działa wszystko w jednym procesie i <xref:System.AppDomain> odtwarzania służy do oczyszczania wszystkie zasoby, takie jak uchwyty pamięci i systemu operacyjnego.  
  
 Nie może zależeć od finalizatory i destruktory lub `try/finally` bloków dla kod wycofujący. Może być przerwane lub nie jest wywoływana.  
  
 Może zostać wygenerowany asynchroniczne wyjątków w nieoczekiwanych lokalizacjach, prawdopodobnie co instrukcji maszyny: <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, i <xref:System.OutOfMemoryException>.  
  
 Zarządzanych wątków niekoniecznie Win32 wątków w usłudze SQL; mogą one włókien.  
  
 Modyfikowalne stan udostępnionego dla procesu lub międzyaplikacyjnej domeny jest bardzo trudne do zmiany bezpiecznie i w miarę możliwości należy unikać.  
  
 Warunki braku pamięci nie są rzadko w programie SQL Server.  
  
 Biblioteki hostowanego w programie SQL Server nie poprawnie zaktualizować ich stanu udostępnionego, istnieje wysokie prawdopodobieństwo, że kod nie zostanie odzyskana do czasu ponownego uruchomienia bazy danych.  Ponadto w niektórych przypadkach extreme jest możliwe, może to spowodować procesu programu SQL Server nie powiedzie się, powodując bazy danych o ponownym uruchomieniu.  Ponowne uruchomienie bazy danych można wyłączyć witryny sieci Web lub wpływających na funkcjonowanie firmy przejąć dostępności.  Powolne przecieków zasobów systemu operacyjnego, np. pamięci lub uchwytów może spowodować serwera po pewnym czasie niepowodzenie przydzielania uchwytów o możliwości odzyskiwania lub potencjalnie serwer powoli spowodować spadek wydajności i zmniejsza aplikacji klienta dostępność.  Wyraźnie chcemy uniknąć tych scenariuszy.  
  
## <a name="best-practice-rules"></a>Regułami najlepszych rozwiązań  
 Wprowadzenie koncentruje się na Przegląd kodu dla zarządzanego kodu, który jest uruchamiany na serwerze byłyby do wychwytywania w celu zwiększenia stabilności i niezawodnością platformy. Kontrole te są dobrym rozwiązaniem, ogólnie rzecz biorąc, i musi bezwzględnej na serwerze.  
  
 W wypadku braku ograniczenia blokady lub zasób, SQL Server będzie przerwać wątek lub zerwanie <xref:System.AppDomain>.  W takim przypadku tylko wycofujący kodu w regionie ograniczonego wykonania (CER) jest gwarantowana do uruchomienia.  
  
### <a name="use-safehandle-to-avoid-resource-leaks"></a>Używaj klasy SafeHandle w celu uniknięcia przecieków zasobów  
 W przypadku liczby <xref:System.AppDomain> zwolniony, nie może zależeć od `finally` bloków lub finalizatory wykonywana, dlatego ważne jest, aby abstrakcyjnej wszystkich dostęp do zasobów systemu operacyjnego za pomocą <xref:System.Runtime.InteropServices.SafeHandle> klasy zamiast <xref:System.IntPtr>, <xref:System.Runtime.InteropServices.HandleRef>, lub podobne klasy. Dzięki temu CLR do śledzenia i zamknąć dojścia używasz nawet w <xref:System.AppDomain> przypadku zakończenia.  <xref:System.Runtime.InteropServices.SafeHandle> będzie używać krytyczne finalizator CLR zawsze będzie działał.  
  
 Dojście systemu operacyjnego są przechowywane w bezpieczne dojście od chwili utworzenia aż do momentu jego zwolnienia.  Brak żadnego okna, podczas którego <xref:System.Threading.ThreadAbortException> może wystąpić zostały publicznie dojścia.  Ponadto wywołanie liczebności referencyjnej zostanie uchwytu, dzięki czemu Zamknij śledzenia ważności uchwytu uniemożliwia problem zabezpieczeń z wyścigu między platformy `Dispose` i metody, które jest aktualnie używane dojście.  
  
 Większość klas, które obecnie ma finalizator po prostu oczyszczania systemu operacyjnego obsługi nie będą już potrzebne finalizatora. Zamiast tego będzie finalizator na <xref:System.Runtime.InteropServices.SafeHandle> klasy.  
  
 Należy pamiętać, że <xref:System.Runtime.InteropServices.SafeHandle> nie zastępuje ona dla <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>.  Ma nadal potencjalnych zasobów rywalizacji i wydajności zalet jawnie usunąć zasoby systemu operacyjnego.  Po prostu należy pamiętać, że `finally` bloków, które jawnie usuwa zasoby mogą być wykonywane do zakończenia.  
  
 <xref:System.Runtime.InteropServices.SafeHandle> Umożliwia wdrożenie własne <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metodę, która wykonuje pracę, aby zwolnić dojścia, takich jak przekazywanie stanu do dojścia systemu operacyjnego zwalnianie procedury lub zwalnianie zestaw uchwytów w pętli.  Środowisko CLR gwarantuje, że ta metoda jest uruchomione.  Jest odpowiedzialny za Autor <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> implementacji, aby upewnić się, jest zwolnienie uchwytu we wszystkich okolicznościach. Błąd w tym celu spowoduje, że dojście do przedostawać, który często powoduje wyciek natywne zasoby skojarzone z dojścia. W związku z tym jest krytyczny do struktury <xref:System.Runtime.InteropServices.SafeHandle> klas pochodnych tak, aby <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> implementacji nie wymaga Alokacja wszystkie zasoby, które mogą być niedostępne w momencie wywołania. Zauważ, że dozwolone wywołania metody, które może zakończyć się niepowodzeniem w ramach wdrożenia <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> pod warunkiem, że swój kod obsługi tych błędów i ukończyć kontraktu, aby zwolnić uchwyt macierzysty. Na potrzeby debugowania, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> ma <xref:System.Boolean> zwrócić wartość, która może być ustawiony na `false` po napotkaniu błędu krytycznego, co uniemożliwia wersji zasobu. Dzięki temu będzie uaktywniać [releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md) MDA, jeśli jest włączona, które pomogą zidentyfikować problem. Nie ma wpływu na środowisko uruchomieniowe w inny sposób; <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> nie zostanie ponownie wywołany dla tego samego zasobu i w związku z tym przecieku dojścia.  
  
 <xref:System.Runtime.InteropServices.SafeHandle> nie jest odpowiednia w niektórych kontekstach.  Ponieważ <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metoda może być uruchamiane w <xref:System.GC> wątku finalizatora żadnych dojścia, które są wymagane do zwolniona, w szczególności wątku nie musi być ujęte w <xref:System.Runtime.InteropServices.SafeHandle>.  
  
 Wywoływane otoki środowiska uruchomieniowego (RCWs) mogą być czyszczone przez środowisko CLR bez dodatkowego kodu.  Dla kodu korzystającego z platformy wywołania i traktuje obiektu modelu COM jako `IUnknown*` lub <xref:System.IntPtr>, kod powinien ulegną do użycia otoki RCW.  <xref:System.Runtime.InteropServices.SafeHandle> może nie być odpowiednie dla tego scenariusza z powodu możliwości wersji niezarządzanej metody wywołań zwrotnych do kodu zarządzanego.  
  
#### <a name="code-analysis-rule"></a>Reguł analizy kodu  
 Użyj <xref:System.Runtime.InteropServices.SafeHandle> celu hermetyzacji zasobów systemu operacyjnego. Nie używaj <xref:System.Runtime.InteropServices.HandleRef> lub pól typu <xref:System.IntPtr>.  
  
### <a name="ensure-finalizers-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Upewnij się, że finalizatory nie ma potrzeby wykonywania, aby zapobiec przeciekom zasoby systemu operacyjnego  
 Zapoznaj się z finalizatory dokładnie, aby upewnić się, że nawet jeśli nie można uruchamiać, zasobu krytycznego systemu operacyjnego jest nie przedostają.  W odróżnieniu od zwykłym <xref:System.AppDomain> zwolniony, gdy aplikacja jest wykonywany w stanie stabilności lub serwera, takie jak program SQL Server wyłącza, obiekty, zostały zakończone podczas niespodziewane <xref:System.AppDomain> zwolnienia.  Upewnij się, że zasoby nie przedostają w przypadku nagłego zwolniony, ponieważ nie można zagwarantować poprawność aplikacji, ale integralność serwera muszą być obsługiwane za nie przeciek zasobów.  Użyj <xref:System.Runtime.InteropServices.SafeHandle> zwolnić wszystkie zasoby systemu operacyjnego.  
  
### <a name="ensure-that-finally-clauses-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Oznacza koniec upewnij się, klauzule nie ma potrzeby uruchom, aby zapobiec przeciekom zasoby systemu operacyjnego  
 `finally` klauzule nie ma gwarancji uruchomiony poza CERs, wymagających deweloperom biblioteki nie zależą od kodu w ramach `finally` bloku do zwalniania niezarządzanych zasobów.  Przy użyciu <xref:System.Runtime.InteropServices.SafeHandle> jest zalecanym rozwiązaniem.  
  
#### <a name="code-analysis-rule"></a>Reguł analizy kodu  
 Użyj <xref:System.Runtime.InteropServices.SafeHandle> oczyszczania zasoby systemu operacyjnego zamiast `Finalize`. Nie używaj <xref:System.IntPtr>; użyj <xref:System.Runtime.InteropServices.SafeHandle> celu hermetyzacji zasobów. Jeśli koniec klauzuli musi uruchomić, umieść go w CER.  
  
### <a name="all-locks-should-go-through-existing-managed-locking-code"></a>Wszystkie blokady powinien przejść przez istniejące zarządzanego kodu blokowania  
 Środowisko CLR muszą znać, jeśli kod jest w blokady tak, aby wiedzieli, aby usunąć <xref:System.AppDomain> zamiast właśnie Trwa przerywanie wątku.  Trwa przerywanie wątku może być niebezpieczne, jak dane zasilaniu przez wątek może pozostać w niespójnym stanie. W związku z tym całą <xref:System.AppDomain> musi zostać odtworzona.  Konsekwencje można zidentyfikować blokady może być zakleszczenie lub niepoprawne wyniki. Użyj metody <xref:System.Threading.Thread.BeginCriticalRegion%2A> i <xref:System.Threading.Thread.EndCriticalRegion%2A> do identyfikowania regionów blokady.  Są one metody statyczne <xref:System.Threading.Thread> klasy, które mają zastosowanie tylko do bieżącego wątku, pomaga w zapobieganiu jeden wątek Edycja liczbę blokad inny wątek.  
  
 <xref:System.Threading.Monitor.Enter%2A> i <xref:System.Threading.Monitor.Exit%2A> ma to powiadomienie CLR wbudowane, dlatego zaleca się ich użycia oraz stosowania [lock — instrukcja](~/docs/csharp/language-reference/keywords/lock-statement.md), który używa tych metod.  
  
 Innych mechanizmów blokowania, takich jak pokrętła blokad i <xref:System.Threading.AutoResetEvent> należy wywołać tych metod, aby powiadomić CLR jest wprowadzane sekcja krytyczna.  Tych metod nie wykonuj żadnych blokad; informują wykonywanego kodu w sekcji krytycznej środowiska CLR i przerywanie wątku można pozostawić niespójne udostępniania stanu.  Jeśli zdefiniowano własne typu blokady, na przykład niestandardowy <xref:System.Threading.ReaderWriterLock> klasy, należy użyć tych metod licznik blokady.  
  
#### <a name="code-analysis-rule"></a>Reguł analizy kodu  
 Oznacz i Znajdź wszystkie blokady przy użyciu <xref:System.Threading.Thread.BeginCriticalRegion%2A> i <xref:System.Threading.Thread.EndCriticalRegion%2A>. Nie używaj <xref:System.Threading.Interlocked.CompareExchange%2A>, <xref:System.Threading.Interlocked.Increment%2A>, i <xref:System.Threading.Interlocked.Decrement%2A> w pętli.  Czy platforma wywołania wariantów Win32 tych metod.  Nie używaj <xref:System.Threading.Thread.Sleep%2A> w pętli.  Nie należy używać pola nietrwałego.  
  
### <a name="cleanup-code-must-be-in-a-finally-or-a-catch-block-not-following-a-catch"></a>Oczyszczanie kodu musi być w finally lub catch bloku nie następujących instrukcji catch  
 Oczyszczanie kodu nigdy nie należy stosować `catch` Blokuj; powinna być w `finally` lub `catch` się zablokować.  Powinno to być normalna dobrym rozwiązaniem.  A `finally` bloku jest zazwyczaj preferowana, ponieważ uruchomieniu tego samego kodu, zarówno w przypadku jest zwracany wyjątek, jak i podczas koniec `try` zwykle napotkano bloku.  W przypadku wystąpił nieoczekiwany wyjątek został zgłoszony, na przykład <xref:System.Threading.ThreadAbortException>, czyszczenie kodu nie zostaną uruchomione.  Wszelkie niezarządzane zasoby, które może wyczyścić w `finally` najlepiej musi być ujęte w <xref:System.Runtime.InteropServices.SafeHandle> do zapobieganie wyciekom.  Należy pamiętać, C# `using` — słowo kluczowe można skutecznie usuwanie obiektów, w tym uchwytów.  
  
 Mimo że <xref:System.AppDomain> odtwarzania można wyczyścić zasobów w wątku finalizatora, jest nadal należy umieścić oczyszczanie kodu w odpowiednie miejsce.  Należy pamiętać, że jeśli wątek odebrał wyjątek asynchroniczny bez blokada, CLR próbuje zakończyć wątku bez konieczności Odtwórz <xref:System.AppDomain>.  Zapewnienie, że zasoby są czyszczone wcześniej zamiast nowsze pomaga udostępniając więcej zasobów, a także lepsze zarządzanie przez czas ich istnienia.  Jeśli nie zamykaj jawnie dojście do pliku w ścieżce kodu błędu, niektóre poczekaj <xref:System.Runtime.InteropServices.SafeHandle> finalizatorów, aby wyczyścić go, przy następnym kodzie uruchamia go może zakończyć się niepowodzeniem próby uzyskania dostępu dokładnie tego samego pliku, jeśli finalizator nie został już uruchomiony.  Z tego powodu zagwarantowaniu, że oczyszczanie kodu istnieje i że działa ona prawidłowo może pomóc skutków błędów więcej prawidłowo i szybko, mimo że nie jest to bezwzględnie konieczne.  
  
#### <a name="code-analysis-rule"></a>Reguł analizy kodu  
 Oczyszczanie kodu po `catch` musi być w `finally` bloku. Wywołania do usunięcia w bloku finally.  `catch` bloki powinien kończyć się throw albo ponownie Zgłoś.  Gdy będzie istnieć wyjątki, takie jak kod wykrywania, czy można nawiązać połączenia sieciowego gdzie może przyczynić się do żadnego z dużą liczbę wyjątków, kodu, który wymaga Przechwytywanie liczba wyjątków w normalnych okolicznościach nadać Wskazuje, że kod powinien być testowane, jeśli powiedzie.  
  
### <a name="process-wide-mutable-shared-state-between-application-domains-should-be-eliminated-or-use-a-constrained-execution-region"></a>Modyfikowalne stanu udostępnionego całego procesu między domenami aplikacji powinny zostać usunięte lub użyj Region ograniczonego wykonania  
 Zgodnie z opisem we wprowadzeniu, może być bardzo trudne do pisania kodu zarządzanego, który monitoruje stan udostępnionego całego procesu między domenami aplikacji w sposób niezawodny.  Udostępniony stan całego procesu jest dowolny rodzaj struktury danych udostępnionych między domenami aplikacji w kodzie Win32, wewnątrz środowiska CLR lub w kodzie zarządzanym przy użyciu usług zdalnych.  Dowolny modyfikowalną udostępniony stan jest bardzo trudne do poprawnie zapisać w kodzie zarządzanym i wszelkie statyczny udostępnionego stanu może być wykonywana tylko ze szczególną uwagę na to.  Jeśli masz całego procesu lub dla komputera stanu udostępnionego, Znajdź sposobem jej wyeliminowania lub ochrony stanu udostępnionego, przy użyciu region ograniczonego wykonania (CER).  Wszystkie biblioteki z stanu udostępnionego, który nie jest zidentyfikowała i poprawiła powodować hosta, takich jak SQL Server, wymaga czystej <xref:System.AppDomain> zwalnianie awarię.  
  
 Jeśli kod używa obiektu COM, należy unikać udostępniania tego obiektu COM między domenami aplikacji.  
  
### <a name="locks-do-not-work-process-wide-or-between-application-domains"></a>Blokady nie działają całego procesu lub między domenami aplikacji.  
 W przeszłości <xref:System.Threading.Monitor.Enter%2A> i [lock — instrukcja](~/docs/csharp/language-reference/keywords/lock-statement.md) zostały już użyte do utworzenia procesu globalnego blokad.  Na przykład ten błąd występuje podczas blokowania na <xref:System.AppDomain> agile klas, takich jak <xref:System.Type> wystąpień z nieudostępnione zestawy <xref:System.Threading.Thread> obiektów, interned ciągów i niektórych ciągów udostępniane między domenami aplikacji przy użyciu usług zdalnych.  Te blokad nie są już dla procesu.  Aby zidentyfikować obecności blokady całego procesu interapplication domeny, należy określić, czy kod w blokady korzysta wszystkich zasobów zewnętrznych, utrwalonych takich jak plik na dysku lub bazy danych.  
  
 Należy pamiętać, biorąc blokady w <xref:System.AppDomain> może spowodować problemy w przypadku chronionych kodu wykorzystuje zasób zewnętrzny, ponieważ ten kod może działać jednocześnie w wielu domenach aplikacji.  Może to stanowić problem podczas zapisywania do powiązania z gniazdem dla całego procesu lub jeden plik dziennika.  Te zmiany oznaczają nie istnieje łatwy sposób, przy użyciu kodu zarządzanego na uzyskanie blokady globalne procesu w innych niż z użyciem nazwane <xref:System.Threading.Mutex> lub <xref:System.Threading.Semaphore> wystąpienia.  Tworzenie kodu, który nie działać jednocześnie w dwóch domen aplikacji, lub użyj <xref:System.Threading.Mutex> lub <xref:System.Threading.Semaphore> klasy.  Jeśli nie można zmienić istniejący kod, nie należy używać Win32 nazwanego obiektu mutex do osiągnięcia tej synchronizacji, ponieważ uruchomiony w trybie włókien oznacza, że nie może zagwarantować tego samego wątku systemu operacyjnego zostanie nabywania i zwolnić obiektu mutex.  Należy użyć zarządzanej <xref:System.Threading.Mutex> klasy lub nazwanym <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, lub <xref:System.Threading.Semaphore> do synchronizowania blokady kodu w sposób świadomość zamiast synchronizacji blokady przy użyciu kodu niezarządzanego CLR.  
  
#### <a name="avoid-locktypeofmytype"></a>Unikaj lock(typeof(MyType))  
 Prywatne i publiczne <xref:System.Type> obiektów w zestawy udostępnione z tylko jedną kopię kodu udostępnionych we wszystkich domenach aplikacji stanowi również problemy.  Dla udostępnionych zestawów jest tylko jedno wystąpienie <xref:System.Type> na proces, co oznacza, że wiele domen aplikacji udostępniać dokładnie takie same <xref:System.Type> wystąpienia.  Biorąc blokady <xref:System.Type> blokady, który ma wpływ na cały proces nie ma wystąpienia właśnie <xref:System.AppDomain>.  Jeśli <xref:System.AppDomain> przejmuje blokady <xref:System.Type> następnie obiekt, że wątek pobiera nagle przerwane, nie będzie nie zwalnia blokadę.  Ta blokada może spowodować innych domen aplikacji do zakleszczenia.  
  
 Dobrym sposobem wykonuj blokad w statycznej metody obejmuje dodawanie obiektu statyczne wewnętrzne synchronizacji z kodu.  Można jej zainicjować w konstruktorze klasy jest dostępny, ale nie mogą być inicjowane następująco:  
  
```  
private static Object s_InternalSyncObject;  
private static Object InternalSyncObject   
{  
    get   
    {  
        if (s_InternalSyncObject == null)   
        {  
            Object o = new Object();  
            Interlocked.CompareExchange(  
                ref s_InternalSyncObject, o, null);  
        }  
        return s_InternalSyncObject;  
    }  
}  
```  
  
 Następnie podejmując blokady, użyj `InternalSyncObject` właściwości, aby uzyskać obiekt ma być blokowany na.  Nie trzeba używać właściwości, jeśli w Twojej konstruktora klasy mają zainicjować obiektu wewnętrznego synchronizacji.  Podwójne sprawdzanie, czy kod inicjujący blokady powinna wyglądać w tym przykładzie:  
  
```  
public static MyClass SingletonProperty   
{  
    get   
    {  
        if (s_SingletonProperty == null)   
        {  
            lock(InternalSyncObject)   
            {  
                // Do not use lock(typeof(MyClass))   
                if (s_SingletonProperty == null)   
                {  
                    MyClass tmp = new MyClass(…);     
                    // Do all initialization before publishing  
                    s_SingletonProperty = tmp;  
                }  
            }  
        }  
        return s_SingletonProperty;  
    }  
}  
```  
  
#### <a name="a-note-about-lockthis"></a>Uwagi dotyczące Lock(this)  
 Na ogół dopuszczalne jest podjęcie blokady wybranego obiektu, który jest dostępny publicznie.  Jednak jeśli obiekt pojedynczego obiektu, który może spowodować, że cały podsystemu do zakleszczenia, należy rozważyć użycie również powyżej wzorzec projektowy.  Na przykład blokady na ten <xref:System.Security.SecurityManager> obiektu może spowodować zakleszczenie w <xref:System.AppDomain> wprowadzania całą <xref:System.AppDomain> korzystanie z niej. Jest dobrym rozwiązaniem, które nie zostały blokady na publicznie dostępny obiekt tego typu.  Jednak blokady na poszczególnych kolekcji lub tablicy, należy zwykle stanowi problem.  
  
#### <a name="code-analysis-rule"></a>Reguł analizy kodu  
 Nie wykonuj blokad na typy, które mogą być używane między domenami aplikacji lub nie ma w pewnym sensie silnej tożsamości. Nie wywołuj <xref:System.Threading.Monitor.Enter%2A> na <xref:System.Type>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.PropertyInfo>, <xref:System.String>, <xref:System.ValueType>, <xref:System.Threading.Thread>, lub dowolnego obiektu, która jest pochodną <xref:System.MarshalByRefObject>.  
  
### <a name="remove-gckeepalive-calls"></a>Usuń GC. Wywołania utrzymywania aktywności  
 Albo nie używa znaczną ilość istniejący kod <xref:System.GC.KeepAlive%2A> gdy powinna lub korzysta, gdy nie jest odpowiedni.  Po skonwertowaniu na <xref:System.Runtime.InteropServices.SafeHandle>, nie trzeba wywołać klasy <xref:System.GC.KeepAlive%2A>, zakładając, że nie ma finalizator, ale korzystają z <xref:System.Runtime.InteropServices.SafeHandle> celu sfinalizowania system operacyjny obsługuje.  Podczas koszt wydajności utrzymania wywołanie <xref:System.GC.KeepAlive%2A> może być niewielka, z punktu widzenia użytkownika który wywołanie <xref:System.GC.KeepAlive%2A> jest konieczne lub wystarczające, aby rozwiązać problem, który już nie istnieje sprawia, że kod jest bardziej trudne w utrzymaniu okres istnienia.  Jednak, w przypadku korzystania z międzyoperacyjnego CLR wywoływane otoki COM (RCWs), <xref:System.GC.KeepAlive%2A> nadal jest wymagane przez kod.  
  
#### <a name="code-analysis-rule"></a>Reguł analizy kodu  
 Usuń <xref:System.GC.KeepAlive%2A>.  
  
### <a name="use-the-host-protection-attribute"></a>Użyj atrybutu ochrony hosta  
 <xref:System.Security.Permissions.HostProtectionAttribute> (HPA) umożliwia korzystanie z akcji zabezpieczenia deklaratywne ustalenie wymagań dotyczących ochrony hosta, co hosta zapobiec wywoływania niektórych metod, które nie mają zastosowania do danego hosta, takich jak nawetcałkowiciezaufanegokodu<xref:System.Environment.Exit%2A>lub <xref:System.Windows.Forms.MessageBox.Show%2A> dla programu SQL Server.  
  
 HPA dotyczy tylko niezarządzanych aplikacji obsługujących wspólnego języka środowiska uruchomieniowego i wdrożenie hosta ochrony, takie jak SQL Server. Po zastosowaniu, wyniki akcji zabezpieczeń podczas tworzenia żądania łącza na podstawie zasobów hosta ujawnia klasa lub metoda. Jeśli kod jest uruchamiana w aplikacji klienckiej lub na serwerze, który nie jest chroniony przez hosta, atrybut "evaporates"; nie jest wykrywane i w związku z tym nie zastosować.  
  
> [!IMPORTANT]
>  Ten atrybut ma na celu wymuszenia specyficzne dla hosta wytycznych programowania modelu, nie działanie zabezpieczeń.  Mimo że żądanie łącza jest używany do sprawdzania zgodności do wymagania modelu programowania <xref:System.Security.Permissions.HostProtectionAttribute> nie jest uprawnienia zabezpieczeń.  
  
 Jeśli host nie ma wymagań modelu programowania, nie występują żądania łączy.  
  
 Ten atrybut określa następujące czynności:  
  
-   Metod lub klas, które nie pasują do hosta programowania modelu, ale są w przeciwnym razie niegroźne.  
  
-   Metod lub klas, które nie pasują do jej modelu programowania hosta i może prowadzić do destabilizing kod zarządzany serwer użytkownika.  
  
-   Metod lub klas, które nie pasują do hosta programowania modelu i może prowadzić do destabilizacji sam proces serwera.  
  
> [!NOTE]
>  W przypadku tworzenia biblioteki klas, który ma być wywoływany przez aplikacje, które mogą być wykonywane w środowisku hosta chronione elementy członkowskie, które udostępniają należy zastosować atrybut <xref:System.Security.Permissions.HostProtectionResource> kategorie zasobów. Elementy członkowskie biblioteki klas .NET Framework z tym atrybutem spowodować tylko bezpośredniego obiektu wywołującego ma być sprawdzany.  Biblioteka elementów członkowskich musi powodować kontrolę jego bezpośredniego obiektu wywołującego w taki sam sposób.  
  
 Znajdziesz więcej informacji na temat HPA w <xref:System.Security.Permissions.HostProtectionAttribute>.  
  
#### <a name="code-analysis-rule"></a>Reguł analizy kodu  
 Dla programu SQL Server wszystkie metody używane do wprowadzania synchronizacji lub wątkowość musi oznaczone symbolem HPA. Dotyczy to również metody udostępniania stanu, są zsynchronizowane lub zarządzać procesów zewnętrznych. <xref:System.Security.Permissions.HostProtectionResource> Wartości, które mają wpływ na program SQL Server są <xref:System.Security.Permissions.HostProtectionResource.SharedState>, <xref:System.Security.Permissions.HostProtectionResource.Synchronization>, i <xref:System.Security.Permissions.HostProtectionResource.ExternalProcessMgmt>. Jednak wszystkie metody, która udostępnia żadnego <xref:System.Security.Permissions.HostProtectionResource> powinny zostać zidentyfikowane na podstawie HPA, nie tylko te, które korzysta z zasobów mających wpływ na SQL.  
  
### <a name="do-not-block-indefinitely-in-unmanaged-code"></a>Nie należy blokować nieskończoność za pomocą kodu niezarządzanego  
 Blokowanie za pomocą kodu niezarządzanego, a nie w kodzie zarządzanym może spowodować odmowę usługi, ponieważ CLR nie jest w stanie przerwać wątek.  Zablokowane wątku uniemożliwia zwalnianie CLR <xref:System.AppDomain>, co najmniej nie robiąc niektóre operacje bardzo niebezpieczne.  Blokowanie przy użyciu Win32 prymitywu synchronizacji jest wyczyść przykładem coś, co nie może dopuścić do nas.  Blokowanie w wywołaniu `ReadFile` na gnieździe należy unikać Jeśli to możliwe — najlepiej Win32 API powinien mechanizm operacji podobny do tego limitu czasu.  
  
 Dowolnej metody, która wywołuje w trybie macierzystym w idealnym przypadku należy używać wywołania Win32 uzasadnione, ograniczone limitu czasu.  Jeśli użytkownik może określić limit czasu, użytkownik nie powinien być dozwolony, aby określić nieskończony limit czasu bez pewnych uprawnień zabezpieczeń.  Przyjąć Jeśli metoda będzie blokować przez więcej niż ~ 10 sekund, należy korzystać z wersji, który obsługuje limity czasu lub potrzebujesz dodatkowej pomocy CLR.  
  
 Oto kilka przykładów problematyczne interfejsu API.  Potoki (anonimowe i nazwane) można tworzyć z limitem czasu; Jednak kod należy upewnić się, że nigdy nie wywołuje `CreateNamedPipe` ani `WaitNamedPipe` z NMPWAIT_WAIT_FOREVER.  Ponadto może istnieć nieoczekiwany, blokowanie, nawet jeśli jest określony limit czasu.  Wywoływanie `WriteFile` na anonimowe potoku zablokuje dopóki nie zostaną zapisane wszystkie bajty, co oznacza, jeśli bufor składa się z nieprzeczytana danych w ramach tego `WriteFile` wywołania zablokuje dopóki czytnik został zwolniony miejsca w buforze potoku.  Gniazda zawsze należy używać niektórych interfejs API, który będzie honorować mechanizm limitu czasu.  
  
#### <a name="code-analysis-rule"></a>Reguł analizy kodu  
 Blokowanie bez limitu czasu za pomocą kodu niezarządzanego jest typu "odmowa usługi". Nie wykonuj platformy wywołania wywołania `WaitForSingleObject`, `WaitForSingleObjectEx`, `WaitForMultipleObjects`, `MsgWaitForMultipleObjects`, i `MsgWaitForMultipleObjectsEx`.  Nie należy używać NMPWAIT_WAIT_FOREVER.  
  
### <a name="identify-any-sta-dependent-features"></a>Zidentyfikuj wszystkie funkcje zależne od STA.  
 Zidentyfikuj kodu, który używa apartamentach jednowątkowe COM (STAs).  STAs są wyłączone w procesie programu SQL Server.  Funkcje, które są zależne od `CoInitialize`, takie jak liczników wydajności lub Schowka, musi zostać wyłączone w programie SQL Server.  
  
### <a name="ensure-finalizers-are-free-of-synchronization-problems"></a>Upewnij się, że finalizatory bez problemów z synchronizacją  
 Wiele wątków finalizator może istnieć w przyszłych wersji systemu .NET Framework, co oznacza finalizatory dla różnych wystąpień tego samego typu działać jednocześnie.  Nie mają być całkowicie wielowątkowość; Moduł zbierający elementy bezużyteczne gwarantuje, że tylko jeden wątek uruchomi finalizatora dla wystąpienia danego obiektu.  Jednak finalizatory musi być kodowane w celu uniknięcia wyścigu i zakleszczenie podczas uruchamiania jednocześnie na wielu różnych obiektów.  Gdy przy użyciu dowolnego stanu zewnętrznych, takich jak zapisywania do pliku dziennika w finalizator, problemy wielowątkowości musi być obsługiwane.  Nie należy polegać na finalizację w celu zapewnienia bezpieczeństwa wątków. Lokalny magazyn wątków, zarządzanym lub macierzystym, nie należy używać do przechowywania stanu w wątku finalizatora.  
  
#### <a name="code-analysis-rule"></a>Reguł analizy kodu  
 Finalizatory musi zawierać problemów z synchronizacją. Nie należy używać statycznego modyfikowalną stanie finalizator.  
  
### <a name="avoid-unmanaged-memory-if-possible"></a>Unikaj niezarządzanej pamięci, jeśli to możliwe  
 Niezarządzanej pamięci mogą przedostawać, podobnie jak dojścia systemu operacyjnego.  Jeśli to możliwe, spróbuj użyć pamięci przy użyciu stosu [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md) lub przypiętych obiektu zarządzanego, takich jak [stałej instrukcji](~/docs/csharp/language-reference/keywords/fixed-statement.md) lub <xref:System.Runtime.InteropServices.GCHandle> przy użyciu typu byte [].  <xref:System.GC> Ostatecznie czyści je.  Jednak jeśli należy przydzielić niezarządzanej pamięci, należy rozważyć użycie klasy, która jest pochodną <xref:System.Runtime.InteropServices.SafeHandle> opakowywać alokacji pamięci.  
  
 Należy pamiętać, że istnieje co najmniej jeden przypadek gdzie <xref:System.Runtime.InteropServices.SafeHandle> jest nieodpowiedni.  Dla wywołań metod modelu COM, których alokacji lub zwolnić pamięć, jest typowe dla jednej biblioteki DLL można przydzielić pamięci za pomocą `CoTaskMemAlloc` , a następnie innej bibliotece DLL zwalnia pamięci z `CoTaskMemFree`.  Przy użyciu <xref:System.Runtime.InteropServices.SafeHandle> w tych miejscach będzie nieodpowiednie ponieważ podejmie próbę powiązanie okres istnienia pamięci niezarządzane przez cały czas trwania <xref:System.Runtime.InteropServices.SafeHandle> zamiast zezwalać inny formant DLL okres istnienia pamięci.  
  
### <a name="review-all-uses-of-catchexception"></a>Przejrzyj wszystkie użycia Catch(Exception)  
 Bloki czy catch wszystkie wyjątki zamiast co określony wyjątek zostanie teraz catch również asynchroniczne wyjątki catch.  Sprawdź każdy blok catch(Exception), wyszukiwanie nie zasobów ważne zwalniania lub Wycofaj kod, który mogły zostać pominięte, a także potencjalnie nieprawidłowe zachowanie w bloku catch do obsługi <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, lub <xref:System.OutOfMemoryException>.  Należy pamiętać, że jest możliwe, ten kod może być rejestrowania lub niektóre założenie, że jej może zobaczyć tylko pewne wyjątki, lub że zawsze, gdy wyjątek sytuacji go nie powiodło się dla dokładnie jednej przyczyny.  Zaktualizowano w celu uwzględnienia tych założeń może wymagać <xref:System.Threading.ThreadAbortException>.  
  
 Rozważ zmianę wszystkich miejsc tego catch Przechwytywanie określony typ wyjątku, który będzie wszystkie wyjątki zostaną zgłoszone, takich jak <xref:System.FormatException> z ciągu metod formatowania.  Uniemożliwia uruchomiony na wyjątki nieoczekiwany blok catch i może pomóc upewnić się, że kod nie ukrywa przez przechwytywanie wyjątków w nieoczekiwanych błędów.  Zasadniczo nigdy nie obsługi wyjątku w kodzie biblioteki (kod, który wymaga catch wyjątku może wskazywać projektowania luka w kodzie wywołujesz).  W niektórych przypadkach można przechwytywać wyjątku i zgłosić innego typu wyjątku w celu zapewnienia większej ilości danych.  W takim przypadku użycia wyjątków zagnieżdżonych przechowywania rzeczywistych przyczynę awarii w <xref:System.Exception.InnerException%2A> właściwości nowej wyjątek.  
  
#### <a name="code-analysis-rule"></a>Reguł analizy kodu  
 Przejrzyj wszystkie bloki catch w kodzie zarządzanym tej catch wszystkich obiektów lub catch wszystkie wyjątki.  W języku C#, oznacza to, zarówno Flagowanie `catch` {} i `catch(Exception)` {}.  Należy rozważyć zmianę bardzo określonego typu wyjątku lub przejrzyj kod, aby upewnić się, że jej nie działa w nieprawidłowy sposób, jeśli jego przechwytuje nieoczekiwany wyjątek typu.  
  
### <a name="do-not-assume-a-managed-thread-is-a-win32-thread--it-is-a-fiber"></a>Zakłada się zarządzanego wątku jest wątku Win32 — włókien  
 Użycie zarządzanych wątków lokalnych magazynu działa, ale nie możesz użyć magazynu lokalnego wątku niezarządzanego lub przyjęto założenie, że kod zostaną ponownie uruchomione w bieżącym wątku systemu operacyjnego.  Nie należy zmieniać ustawienia, takie jak ustawienia regionalne wątku.  Nie wywołuj `InitializeCriticalSection` lub `CreateMutex` za pośrednictwem platformy wywołania, ponieważ wymagają one wątku systemu operacyjnego, który przechodzi blokady również zakończyć blokady.  Ponieważ to nie będzie w przypadku gdy przy użyciu włókien, sekcje krytyczne Win32 i muteksy nie można używać w języku SQL bezpośrednio.  Należy pamiętać, że zarządzanej <xref:System.Threading.Mutex> klasa nie obsługuje te problemy koligacji wątku.  
  
 Można bezpiecznie użyć większości stanu na zarządzanego <xref:System.Threading.Thread> obiektu, w tym lokalny magazyn wątków zarządzanych i wątku bieżącej kultury interfejsu użytkownika.  Można również użyć <xref:System.ThreadStaticAttribute>, która sprawia, że wartość istniejącej zmiennej statycznych dostępne tylko przez bieżący wątek zarządzanych (jest to inny sposób realizacji włókien magazynu lokalnego w środowisku CLR).  Programowania powodów modelu, nie można zmienić bieżącej kultury wątku podczas uruchamiania w języku SQL.  
  
#### <a name="code-analysis-rule"></a>Reguł analizy kodu  
 SQL Server jest uruchomiony w trybie włókien; nie należy używać magazynu lokalnego wątku. Unikaj platformy wywołania wywołania `TlsAlloc`, `TlsFree`, `TlsGetValue`, i `TlsSetValue.`  
  
### <a name="let-sql-server-handle-impersonation"></a>Let personifikacji dojście do serwera SQL  
 Ponieważ personifikacji operuje na poziomie wątku i SQL można uruchomić w trybie włókien, kodu zarządzanego nie ma personifikować użytkowników i nie powinny wywoływać `RevertToSelf`.  
  
#### <a name="code-analysis-rule"></a>Reguł analizy kodu  
 Pozwolić, aby obsłużyć personifikacji programu SQL Server. Nie używaj `RevertToSelf`, `ImpersonateAnonymousToken`, `DdeImpersonateClient`, `ImpersonateDdeClientWindow`, `ImpersonateLoggedOnUser`, `ImpersonateNamedPipeClient`, `ImpersonateSelf`, `RpcImpersonateClient`, `RpcRevertToSelf`, `RpcRevertToSelfEx`, lub `SetThreadToken`.  
  
### <a name="do-not-call-threadsuspend"></a>Nie wywołuj Thread::Suspend  
 Możliwość wstrzymywania wątku mogą wydawać się prostą operacją, ale może spowodować zakleszczenie.  Jeśli wątek posiadająca blokady pobiera zawieszony przez drugi wątek, a następnie drugiego wątku spróbuje, biorąc tego samego blokady, zakleszczenie występuje.  <xref:System.Threading.Thread.Suspend%2A> może zakłócać zabezpieczeń, podczas ładowania klasy usług zdalnych i odbicie obecnie.  
  
#### <a name="code-analysis-rule"></a>Reguł analizy kodu  
 Nie wywołuj <xref:System.Threading.Thread.Suspend%2A>. Należy rozważyć użycie rzeczywistych synchronizacji pierwotne, takie jak <xref:System.Threading.Semaphore> lub <xref:System.Threading.ManualResetEvent> .  
  
### <a name="protect-critical-operations-with-constrained-execution-regions-and-reliability-contracts"></a>Chroń ważne operacje z ograniczone regiony wykonania i kontrakty niezawodności  
 Podczas wykonywania operacji złożonych, że aktualizacje stanu udostępnionego lub który musi być w sposób niejednoznaczny albo pełni powiedzie się lub pełni zakończyć się niepowodzeniem, należy się upewnić, że jest chroniony przez region ograniczonego wykonania (CER). Gwarantuje to, że kod jest uruchomiony w każdym przypadku nawet przerwania niespodziewane wątku lub nagłego <xref:System.AppDomain> zwolnienia.  
  
 CER jest określonego `try/finally` bloku natychmiast poprzedzony przez wywołanie <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>.  
  
 Wykonanie tej tak instruuje kompilator just in time, aby przygotować cały kod w bloku finally przed uruchomieniem `try` bloku. Gwarantuje to, że kod w koniec bloku jest wbudowana i będzie działać we wszystkich przypadkach. Nie jest rzadko w CER ma pustą `try` bloku. Przy użyciu CER chroni przed przerwanie asynchronicznego wątku i wyjątki o braku pamięci. Zobacz <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> formularza CER, które dodatkowo przepełnienie stosu uchwytów nadmiernie dokładnego kodu.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.ConstrainedExecution>  
 [Atrybuty ochrony hosta i programowanie SQL Server](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)
