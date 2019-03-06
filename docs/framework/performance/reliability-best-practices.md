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
ms.openlocfilehash: 37e6b995a84a54dfcb52460d11e9843a933a5684
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353078"
---
# <a name="reliability-best-practices"></a>Najlepsze rozwiązania dotyczące niezawodności

Następujące reguły dotyczące niezawodności są ukierunkowane do programu SQL Server; Jednakże są też stosowane do dowolnej aplikacji opartej na hoście serwera. Bardzo ważne jest, serwerów, takich jak SQL Server nie nastąpił przeciek zasobów i nie można przełączyć w dół.  Jednakże, nie można wykonać, pisząc kod wycofujący dla każdej metody, która zmienia stan obiektu.  Celem jest nie do 100 procent niezawodne kodu zarządzanego, który zostanie przywrócona do działania z wszystkich błędów w każdej lokalizacji za pomocą kod wycofujący zapisu.  Który będzie stanowić nie lada z niewielkie prawdopodobieństwo powodzenia.  Środowisko uruchomieniowe języka wspólnego (CLR) nie można łatwo udostępnić wystarczająco silne gwarancje do zarządzanego kodu umożliwiają pisanie kodu doskonałe, jest to możliwe.  Należy pamiętać, że w przeciwieństwie do programu ASP.NET, czy program SQL Server, używa tylko jeden proces, który nie może zostać przetworzony ponownie bez konieczności wyłączania bazy danych dla bardzo dużo czasu.

Za pomocą tych gwarancji słabszy i uruchomiona w ramach jednego procesu niezawodność opiera się na przerywanie wątków lub odtwarzania domen aplikacji, gdy nie przedostają niezbędne i zdolności do przyjmowania środki ostrożności, aby zasoby systemu operacyjnego, takich jak pamięci lub uchwytów.  Nawet w przypadku tego prostsze ograniczenia niezawodności jest nadal wymagane znacznie wyższą niezawodność:

- Nigdy nie przecieku zasobów systemu operacyjnego.

- Identyfikowanie Blokada wszystkich zarządzanych w wszystkie formularze do środowiska CLR.

- Nigdy nie takie domenie międzyaplikacyjnej podziału, udostępniony stan, dzięki czemu <xref:System.AppDomain> odtwarzania sprawnego funkcjonowania.

Chociaż teoretycznie do pisania kodu zarządzanego, aby obsłużyć <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, i <xref:System.OutOfMemoryException> wyjątki, oczekiwano programistom pisanie nierozsądne jest takie niezawodny kod w całej aplikacji.  Z tego powodu out-of-band wyjątków powoduje, iż wątek wykonujący przerywane; i przerwał wątek został edycji udostępnionego stanu, które można określić, czy wątek nałoży blokadę, a następnie <xref:System.AppDomain> jest zwalniana.  Gdy metoda, która jest edytowany udostępnionego stanu jest zakończone, stan będzie uszkodzony, ponieważ nie jest możliwe do zapisu niezawodny kod wycofujący aktualizacji udostępnionego stanu.

W .NET Framework w wersji 2.0, jedyny host, który wymaga programu SQL Server jest niezawodność.  Jeżeli zestaw będzie uruchamiany na serwerze SQL, należy wykonać pracę niezawodność dla każdej części tego zestawu, nawet w przypadku określonych funkcji, które są wyłączone podczas uruchamiania w bazie danych.  Jest to wymagane, ponieważ aparat analizy kodu sprawdza, czy kod na poziomie zestawu i nie można odróżnić wyłączone kodu. Inny program SQL Server programowania kwestią jest, że program SQL Server działa wszystko w jednym procesie i <xref:System.AppDomain> odtwarzania jest używany do czyszczenia wszystkie zasoby, takie jak pamięć i system operacyjny obsługuje.

Nie może zależeć od finalizatory i destruktory lub `try/finally` bloków dla kod wycofujący. Może być przerwana lub nie jest wywoływana.

Wyjątki asynchroniczne mogą być generowane w nieoczekiwanych lokalizacjach, prawdopodobnie każdy instrukcji maszyny: <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, i <xref:System.OutOfMemoryException>.

Zarządzane wątki, niekoniecznie są wątków Win32 w języku SQL; mogą one włókien.

Modyfikowalny stan udostępnione całego procesu lub aplikacji dla wielu domen, jest bardzo trudno zmienić bezpieczne i w miarę możliwości należy unikać.

Warunki braku pamięci nie są rzadkie w programie SQL Server.

Jeśli poprawnie biblioteki hostowanego w programie SQL Server nie są uaktualniane ich udostępnionego stanu, istnieje wysokie prawdopodobieństwo, że kod nie zostanie przywrócona do działania do momentu ponownego uruchomienia bazy danych.  Ponadto w skrajnych przypadkach jest to możliwe, może to spowodować procesu programu SQL Server zakończyć się niepowodzeniem, co powoduje bazy danych o ponownym uruchomieniu.  Ponowne uruchamianie bazy danych można walce z witryny sieci Web lub wpływających na funkcjonowanie firmie przejąć dostępności.  Powolne przecieku zasobów systemu operacyjnego, takich jak pamięci lub uchwytów może spowodować, że serwer po pewnym czasie niepowodzenie przydzielania uchwyty o braku możliwości odzyskiwania lub potencjalnie powoli spowodować spadek wydajności serwera i zmniejsza aplikacji klienta dostępność.  Wyraźnie chcemy uniknąć tych scenariuszy.

## <a name="best-practice-rules"></a>Regułami najlepszych rozwiązań

Wprowadzenie koncentruje się na Przegląd kodu dla kodu zarządzanego, który jest uruchamiany na serwerze musiałby zostać przechwycony w celu zwiększenia stabilności i niezawodności Framework. Te sprawdzenia są dobrym rozwiązaniem, ogólnie rzecz biorąc, więc bezwzględnym musi na serwerze.

W przypadku braku ograniczenia blokady lub zasób, SQL Server spowoduje przerwanie wątku lub zatrzymywania <xref:System.AppDomain>.  W takiej sytuacji kod tylko wycofujący w regionie ograniczonego wykonania (CER) jest gwarantowane do uruchomienia.

### <a name="use-safehandle-to-avoid-resource-leaks"></a>Używaj klasy SafeHandle w celu uniknięcia przeciekom zasobów

W przypadku właściwości <xref:System.AppDomain> unload, nie może zależeć od `finally` bloków lub finalizatory wykonywana, dlatego ważne jest, aby abstrakcji wszystkich dostęp do zasobów systemu operacyjnego za pośrednictwem <xref:System.Runtime.InteropServices.SafeHandle> klasy zamiast <xref:System.IntPtr>, <xref:System.Runtime.InteropServices.HandleRef>, lub podobne klasy. Dzięki temu CLR do śledzenia i zamknąć dojścia używasz nawet w <xref:System.AppDomain> przypadku zakończenia.  <xref:System.Runtime.InteropServices.SafeHandle> będzie używać finalizator krytyczny, który zawsze działa, środowisko CLR.

Dojście systemu operacyjnego są przechowywane w bezpiecznego dojścia, od chwili utworzenia do chwili, w których jest on zwalniany.  Brak żadnego okna, w którym <xref:System.Threading.ThreadAbortException> może wystąpić na uchwyt przecieki pamięci.  Ponadto wywołanie licznik odwołań zostanie uchwyt, która umożliwia zamknięcie śledzenia okresu istnienia uchwytu zapobieganie problem zabezpieczeń za pomocą wyścigu między platformy `Dispose` i metody, która jest obecnie za pomocą uchwytu.

Większość klas, które aktualnie mają finalizatory po prostu oczyszczania systemu operacyjnego obsługi nie będą już potrzebne finalizatora. Zamiast tego będzie finalizator w <xref:System.Runtime.InteropServices.SafeHandle> klasy pochodnej.

Należy pamiętać, że <xref:System.Runtime.InteropServices.SafeHandle> nie jest zamiennikiem <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>.  Ma nadal potencjalnych zasobów rywalizacji o zasoby i wydajność zalet jawnie Usuń zasoby systemu operacyjnego.  Po prostu należy pamiętać, że `finally` bloki, które jawnie usuwania zasobów nie może być wykonywane do zakończenia.

<xref:System.Runtime.InteropServices.SafeHandle> pozwala na implementowanie własnych <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metodę, która wykonuje pracę z bezpłatnymi uchwyt, takie jak przekazywanie stanie obsługiwać system operacyjny, zwalniając procedury lub zwalnianie zestaw uchwytów w pętli.  Środowisko CLR gwarantuje, że ta metoda jest uruchamiany.  Jest odpowiedzialny za autora <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> implementacji, aby upewnić się, że uchwyt jest publikowany w każdych okolicznościach. Niewykonanie tej czynności spowoduje, że uchwyt, aby mogą zostać ujawnione, co skutkuje często wyciekom natywne zasoby skojarzone z uchwytu. W związku z tym jest krytyczny do struktury <xref:System.Runtime.InteropServices.SafeHandle> klasy pochodne tak, aby <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> implementacji nie wymaga alokacji zasobów, które mogą być niedostępne w momencie wywołania. Pamiętaj, że jest dopuszczalne do metod wywołania, które może zakończyć się niepowodzeniem w ramach wdrożenia <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> pod warunkiem, że Twój kod może obsłużyć takie błędy i ukończyć kontraktu na zwolnienie uchwytu natywnych. Dla celów debugowania, <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> ma <xref:System.Boolean> zwracają wartość, która może być ustawiona na `false` po napotkaniu błędu krytycznego, co uniemożliwia wersję zasobu. To uaktywni [releaseHandleFailed](../../../docs/framework/debug-trace-profile/releasehandlefailed-mda.md) MDA, jeśli włączone, aby ułatwić zidentyfikowanie problemu. Nie ma wpływu na środowisko uruchomieniowe w inny sposób: <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> nie zostanie ponownie wywołany dla tego samego zasobu i w związku z tym będzie przeciek uchwytu.

<xref:System.Runtime.InteropServices.SafeHandle> nie jest odpowiednie w określonych kontekstach.  Ponieważ <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> metody mogą być uruchamiane na <xref:System.GC> wątek finalizatora wszystkie dojścia, które muszą zostać uwolniona w określonym wątku nie musi być ujęte w <xref:System.Runtime.InteropServices.SafeHandle>.

Wywoływanych otok środowiska uruchomieniowego (RCW) mogą być czyszczone przez środowisko CLR bez dodatkowego kodu.  Kod, który używa platformy wywołania i traktuje obiektu COM jako `IUnknown*` lub <xref:System.IntPtr>, kod powinien zostać przepisany używać RCW.  <xref:System.Runtime.InteropServices.SafeHandle> może nie być odpowiednie dla tego scenariusza, ze względu na możliwość niezarządzanej wersji metody wywołań zwrotnych do kodu zarządzanego.

#### <a name="code-analysis-rule"></a>Reguł analizy kodu

Użyj <xref:System.Runtime.InteropServices.SafeHandle> celu hermetyzacji zasobów systemu operacyjnego. Nie używaj <xref:System.Runtime.InteropServices.HandleRef> lub pola typu <xref:System.IntPtr>.

### <a name="ensure-finalizers-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Upewnij się, że do uruchomienia, aby uniknąć przecieku zasobów systemu operacyjnego nie mają finalizatory

Przejrzyj swoje finalizatorów, aby upewnić się, że nawet wtedy, gdy nie działają, zasób krytycznych systemu operacyjnego nie następuje przeciek.  W przeciwieństwie do normalnego <xref:System.AppDomain> zwolnienie podczas wykonywania aplikacji w stanie stabilnym lub serwera, takie jak SQL Server jest wyłączany, obiekty, zostały zakończone podczas nagłego <xref:System.AppDomain> zwolnienia.  Upewnij się, że nie wyciek zasobów w przypadku nagłego unload, ponieważ nie można zagwarantować poprawność aplikacji, ale integralność serwera musi być utrzymywana przez nie wyciek zasobów.  Użyj <xref:System.Runtime.InteropServices.SafeHandle> zwolnić wszystkie zasoby systemu operacyjnego.

### <a name="ensure-that-finally-clauses-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Oznacza koniec upewnij się klauzule nie jest konieczne uruchomienie, aby zapobiec wyciek zasobów systemu operacyjnego

`finally` klauzule nie ma gwarancji, uruchamiać poza CERs, wymagających deweloperom biblioteki nie zależą od kodu w ramach `finally` blok umożliwiający zwolnienie niezarządzanych zasobów.  Za pomocą <xref:System.Runtime.InteropServices.SafeHandle> jest zalecanym rozwiązaniem.

#### <a name="code-analysis-rule"></a>Reguł analizy kodu

Użyj <xref:System.Runtime.InteropServices.SafeHandle> wyczyścić zasoby systemu operacyjnego zamiast `Finalize`. Nie używaj <xref:System.IntPtr>; użyj <xref:System.Runtime.InteropServices.SafeHandle> celu hermetyzacji zasobów. Jeśli na końcu klauzuli należy uruchomić, umieść go w CER.

### <a name="all-locks-should-go-through-existing-managed-locking-code"></a>Wszystkie blokady powinny przechodzić przez istniejący kod do blokowania zarządzanych

Środowisko CLR musi znać, jeśli kod jest w blokadę, dzięki czemu będzie wiadomo, aby usunąć <xref:System.AppDomain> zamiast po prostu zostanie przerwany wątek.  Trwa przerywanie wątku może być niebezpieczne, ponieważ dane przetwarzane przez wątek może pozostać w stanie niespójnym. W związku z tym, całą <xref:System.AppDomain> ma zostać odzyskany.  Konsekwencje kończy się niepowodzeniem zidentyfikować blokady może być zakleszczenia lub niepoprawne wyniki. Użyj metod <xref:System.Threading.Thread.BeginCriticalRegion%2A> i <xref:System.Threading.Thread.EndCriticalRegion%2A> do identyfikowania regionów blokady.  Są one metody statyczne <xref:System.Threading.Thread> klasy, które mają zastosowanie tylko do bieżącego wątku, zapobiegając jeden wątek edytują liczbę blokad inny wątek.

<xref:System.Threading.Monitor.Enter%2A> i <xref:System.Threading.Monitor.Exit%2A> ma to powiadomienie CLR wbudowane, w związku z czym zaleca się ich użycia oraz korzystanie z [lock — instrukcja](~/docs/csharp/language-reference/keywords/lock-statement.md), który używa tych metod.

Inne blokowania mechanizmów, takich jak pokrętła blokad i <xref:System.Threading.AutoResetEvent> musi wywoływać te metody, aby powiadomić środowiska CLR jest wprowadzanych sekcję krytyczną.  Te metody nie przyjmują żadnych blokad; informują środowisko CLR, że kod jest wykonywany w sekcję krytyczną, i zostanie przerwany wątek może pozostawić niespójne udostępnionego stanu.  Jeśli zdefiniowano swój własny typ blokady, takie jak niestandardowe <xref:System.Threading.ReaderWriterLock> klasy, należy użyć następujących metod licznik blokady.

#### <a name="code-analysis-rule"></a>Reguł analizy kodu

Oznacz i zidentyfikować wszystkie blokady przy użyciu <xref:System.Threading.Thread.BeginCriticalRegion%2A> i <xref:System.Threading.Thread.EndCriticalRegion%2A>. Nie używaj <xref:System.Threading.Interlocked.CompareExchange%2A>, <xref:System.Threading.Interlocked.Increment%2A>, i <xref:System.Threading.Interlocked.Decrement%2A> w pętli.  Nie wykonuj platformę wywołania wariantów Win32 tych metod.  Nie używaj <xref:System.Threading.Thread.Sleep%2A> w pętli.  Nie należy używać pola nietrwałego.

### <a name="cleanup-code-must-be-in-a-finally-or-a-catch-block-not-following-a-catch"></a>Oczyszczanie kodu musi znajdować się w na końcu lub bloku catch bloku, nie następujących instrukcji catch

Kod porządkujący nigdy nie należy stosować `catch` Blokuj; powinien znajdować się w `finally` lub `catch` block sam.  Powinna to być normalne, dobrym rozwiązaniem.  A `finally` blok jest ogólnie metoda preferowana, ponieważ działa ten sam kod i gdy wyjątek jest zgłaszany po końcu `try` bloku normalnie zostanie osiągnięty.  W przypadku nieoczekiwanych rzuceniem wyjątku, na przykład <xref:System.Threading.ThreadAbortException>, czyszczenie kodu nie zostaną uruchomione.  Dowolne niezarządzanych zasobów, które może wyczyścić w `finally` najlepiej musi być ujęte w <xref:System.Runtime.InteropServices.SafeHandle> aby zapobiec przeciekom.  Uwaga C# `using` — słowo kluczowe można efektywnie używać do usuwania obiektów, w tym uchwyty.

Mimo że <xref:System.AppDomain> odtwarzanie można wyczyścić zasobów w wątku finalizatora, są nadal ważne umieścić kod porządkujący w odpowiednim miejscu.  Należy pamiętać, że jeśli wątek otrzyma wyjątku asynchronicznego bez blokady, środowisko CLR próbuje zakończyć wątek bez konieczności odtwarzanie <xref:System.AppDomain>.  Zapewnienie, że zasoby są czyszczone wcześniej zamiast nowsze pomaga udostępnienia większej ilości zasobów i lepsze zarządzanie okresem istnienia.  Jeśli nie zamykaj jawnie dojście do pliku w ścieżce kodu niektórych błędów Zaczekaj, aż <xref:System.Runtime.InteropServices.SafeHandle> finalizator oczyścić je, przy następnym kod jest wykonywany może zakończyć się niepowodzeniem próby uzyskania dostępu dokładnie tego samego pliku, jeśli finalizator nie został już uruchomiony.  Z tego powodu, może pomóc zagwarantowanie, że kod porządkujący istnieje i czy działa poprawnie odzyskiwanie po niepowodzeniach bardziej i szybko, mimo że nie jest bezwzględnie konieczne.

#### <a name="code-analysis-rule"></a>Reguł analizy kodu

Kod porządkujący po `catch` musi być zapisana w `finally` bloku. Wywołania do usuwania w bloku finally.  `catch` bloki powinien kończyć się throw lub Zgłoś ponownie.  Podczas, gdy będzie istnieć wyjątki, takie jak kod wykrywanie, czy można nawiązać połączenia sieciowego może skąd znajdujących się w dużej liczby wyjątków, wszelki kod, który wymaga Przechwytywanie liczba wyjątków w normalnych warunkach powinien zapewnić wskazanie, że kod powinien być przetestowane, jeśli powiedzie.

### <a name="process-wide-mutable-shared-state-between-application-domains-should-be-eliminated-or-use-a-constrained-execution-region"></a>Modyfikowalne udostępnionego stanu całego procesu między domenami aplikacji powinny zostać usunięte, lub użyj Region ograniczonego wykonania

Zgodnie z opisem we wstępie, może być bardzo trudne do pisania kodu zarządzanego, który monitoruje stan udostępnione całego procesu między domenami aplikacji w sposób niezawodny.  Stan udostępnione całego procesu jest dowolny rodzaj struktury danych współużytkowane między domenami aplikacji, albo w kodzie Win32, wewnątrz środowiska CLR lub w kodzie zarządzanym przy użyciu komunikacji zdalnej.  Dowolny modyfikowalny stan udostępnionych jest bardzo trudno jest poprawnie zapisać w kodzie zarządzanym i wszystkie statyczne udostępnionego stanu może odbywać się tylko w przypadku szczególną uwagę.  Jeśli masz całego procesu lub dla komputera udostępnionego stanu, Znajdź jakiś sposób, aby wyeliminować go lub chronić udostępnionego stanu przy użyciu region ograniczonego wykonania (CER).  Wszystkie biblioteki, za pomocą udostępnionego stanu, który nie jest zidentyfikowała i poprawiła powodować hosta, takie jak SQL Server, wymaga czyszczenie <xref:System.AppDomain> zwalnianie ulega awarii.

Jeśli kod używa obiektu COM, Unikaj udostępniania tego obiektu COM między domenami aplikacji.

### <a name="locks-do-not-work-process-wide-or-between-application-domains"></a>Blokady nie działają całego procesu lub między domenami aplikacji.

W przeszłości <xref:System.Threading.Monitor.Enter%2A> i [lock — instrukcja](~/docs/csharp/language-reference/keywords/lock-statement.md) zostały użyte w celu tworzenia procesu globalnego blokad.  Na przykład ten błąd występuje podczas blokowania na <xref:System.AppDomain> klasy agile, takich jak <xref:System.Type> wystąpień z zestawów nieudostępnione, <xref:System.Threading.Thread> obiektów, interned ciągów i niektóre parametry współużytkowane w różnych domenach aplikacji przy użyciu komunikacji zdalnej.  Te blokady nie są już całego procesu.  Aby zidentyfikować obecności blokady domeny interapplication całego procesu, należy określić, czy kod w blokady korzysta dowolnych zasobów zewnętrznych, utrwalonych takiego jak plik na dysku, lub ewentualnie bazy danych.

Należy pamiętać, biorąc blokady w ramach <xref:System.AppDomain> może spowodować problemy, jeśli chroniony kod używa zewnętrznego zasobu, ponieważ ten kod może jednocześnie działać w wielu domenach aplikacji.  Może to być problem podczas zapisywania jeden plik dziennika lub powiązania z gniazdem dla całego procesu.  Te zmiany oznaczają, nie istnieje łatwy sposób, przy użyciu kodu zarządzanego, można uzyskać blokady globalnego procesu, na innych niż z użyciem nazwane <xref:System.Threading.Mutex> lub <xref:System.Threading.Semaphore> wystąpienia.  Tworzenie kodu, które nie jednoczesnego uruchamiania w dwóch domenach aplikacji, lub użyj <xref:System.Threading.Mutex> lub <xref:System.Threading.Semaphore> klasy.  Nie można zmienić istniejący kod, nie używać Win32, w nazwie obiektu mutex do osiągnięcia tej synchronizacji, ponieważ uruchomiony w trybie włókien oznacza, że nie może zagwarantować, tym samym wątku systemu operacyjnego zostanie nabywania i wersji elementu mutex.  Należy użyć zarządzanego <xref:System.Threading.Mutex> klasy lub nazwane <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, lub <xref:System.Threading.Semaphore> do synchronizowania blokady kodu w sposób, że środowisko CLR jest świadomy zamiast synchronizowanie blokady przy użyciu kodu niezarządzanego.

#### <a name="avoid-locktypeofmytype"></a>Należy unikać lock(typeof(MyType))

Prywatne i publiczne <xref:System.Type> obiektów w zestawów współużytkowanych z tylko jedną kopię kodu współużytkowane przez wszystkie domeny aplikacji również stwarzać problemy.  Dla zestawów współużytkowanych istnieje tylko jedno wystąpienie <xref:System.Type> poszczególnym procesom, co oznacza, że wiele domen aplikacji udostępniać dokładnie takie same <xref:System.Type> wystąpienia.  Biorąc blokadę <xref:System.Type> wystąpienia ma blokadę, który nie ma wpływ na cały proces, po prostu z <xref:System.AppDomain>.  Jeśli taki <xref:System.AppDomain> zdobywa blokadę <xref:System.Type> następnie obiektu, że wątek pobiera nagle przerwany, nie zwolni blokadę.  Ta blokada może spowodować innych domenach aplikacji zakleszczenie.

Dobrym sposobem zająć blokad metody statyczne obejmuje dodanie obiektu statyczne wewnętrzne synchronizacji do kodu.  Można jej zainicjować w konstruktorze klasy są dostępne, ale nie mogą być inicjowane następująco:

```csharp
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

Następnie robiąc blokadę, użyj `InternalSyncObject` właściwości do uzyskiwania obiektu do blokowania na.  Nie trzeba użyć właściwości, jeśli obiekt wewnętrzny synchronizacji zainicjują w konstruktora klasy.  Podwójne sprawdzanie, czy kod inicjujący blokady powinien wyglądać następująco:

```csharp
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

#### <a name="a-note-about-lockthis"></a>Uwaga dotycząca Lock(this)

Na ogół dopuszczalne jest podjęcie blokadę wybranego obiektu, który jest publicznie dostępny.  Jednak jeśli obiekt jest pojedynczego obiektu, który może spowodować, że cały podsystemu do zakleszczenia, należy wziąć pod uwagę przy użyciu powyższych wzorca projektowego także.  Na przykład blokadę na architekturze <xref:System.Security.SecurityManager> obiektu może spowodować zakleszczenie w ramach <xref:System.AppDomain> wprowadzania całą <xref:System.AppDomain> uniemożliwiającym jego używanie. Jest dobrą praktyką, aby nie stosuje blokadę publicznie obiektu tego typu.  Jednak blokadę poszczególnych kolekcji lub tablicy, powinien ogólnie nieobecne problem.

#### <a name="code-analysis-rule"></a>Reguł analizy kodu

Nie przyjmują blokady na typy, które mogą być używane w różnych domenach aplikacji, lub nie ma silnej poczucie tożsamości. Nie wywołuj <xref:System.Threading.Monitor.Enter%2A> na <xref:System.Type>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.PropertyInfo>, <xref:System.String>, <xref:System.ValueType>, <xref:System.Threading.Thread>, lub dowolnego obiektu, który pochodzi od klasy <xref:System.MarshalByRefObject>.

### <a name="remove-gckeepalive-calls"></a>Usuń wykaz Globalny. Wywołania utrzymywania aktywności

Znacząca ilość kodu istniejących albo nie używa <xref:System.GC.KeepAlive%2A> po powinny lub używa ich, gdy nie jest właściwe.  Po przekonwertowaniu do <xref:System.Runtime.InteropServices.SafeHandle>, nie trzeba wywołać klasy <xref:System.GC.KeepAlive%2A>, zakładając, że nie ma finalizatora, ale korzystają z <xref:System.Runtime.InteropServices.SafeHandle> Aby sfinalizować system operacyjny obsługuje.  While spadek wydajności przy zachowaniu wywołanie <xref:System.GC.KeepAlive%2A> może być nieznaczny, wrażenie, wywołanie <xref:System.GC.KeepAlive%2A> jest konieczne lub wystarczające, aby rozwiązać problem, który już nie istnieje sprawia, że kod jest bardziej trudne w utrzymaniu okres istnienia.  Jednakże, w przypadku korzystania z międzyoperacyjnego CLR wywoływanych otok COM (RCW) <xref:System.GC.KeepAlive%2A> jest nadal wymagana przez kod.

#### <a name="code-analysis-rule"></a>Reguł analizy kodu

Usuń <xref:System.GC.KeepAlive%2A>.

### <a name="use-the-host-protection-attribute"></a>Użyj atrybutu ochrony hosta

<xref:System.Security.Permissions.HostProtectionAttribute> (HPA) umożliwia korzystanie z akcji zabezpieczenia deklaratywne określenie wymagań dotyczących ochrony hosta, co hosta uniemożliwić wywoływania niektórych metod, które nie mają zastosowania do danego hosta, takie jak jeszczecałkowiciezaufanegokodu<xref:System.Environment.Exit%2A>lub <xref:System.Windows.Forms.MessageBox.Show%2A> dla programu SQL Server.

HPA dotyczy tylko niezarządzanych aplikacji obsługujących wspólnego języka środowiska uruchomieniowego i wdrożenie hosta ochrony, takie jak SQL Server. Po zastosowaniu, wyniki akcji zabezpieczeń, w przypadku tworzenia zapotrzebowania na łącza na podstawie zasobów hosta ujawnia klasy lub metody. Jeśli kod jest uruchamiany w aplikacji klienckiej lub na serwerze, który nie jest chroniony host, atrybut "evaporates"; Nie wykryto i w związku z tym nie zastosować.

> [!IMPORTANT]
> Ten atrybut ma na celu wymuszania specyficzne dla hosta wytycznych programowania modelu, nie działanie zabezpieczeń.  Mimo że zapotrzebowania na łącza służy pod kątem zgodności, wymagań modelu programowania <xref:System.Security.Permissions.HostProtectionAttribute> nie jest uprawnienia zabezpieczeń.

Jeśli host nie ma wymagań modelu programowania, nie występują zapotrzebowania na łącza.

Ten atrybut określa następujące czynności:

- Metod lub klas, które nie pasują do hostów programowania modelu, ale są one w przeciwnym razie niegroźne.

- Metod lub klas, które nie mieszczą się model programowania hosta i może prowadzić do destabilizujące kod zarządzany serwer użytkownika.

- Metod lub klas, które nie pasują do hostów programowania modelu i może prowadzić do destabilizacji sam proces serwera.

> [!NOTE]
> Jeśli tworzysz bibliotekę klas, który ma być wywoływany przez aplikacje, które może być wykonywane w środowisku hosta chronionego, należy zastosować ten atrybut do elementów członkowskich, które uwidaczniają <xref:System.Security.Permissions.HostProtectionResource> kategorie zasobów. Elementy członkowskie biblioteki klas .NET Framework z tym atrybutem spowodować, że tylko bezpośredniego wywołującego do sprawdzenia.  Biblioteka elementów członkowskich również mogą powodować sprawdzenie jego bezpośredniego obiektu wywołującego w taki sam sposób.

Można znaleźć więcej informacji na temat HPA w <xref:System.Security.Permissions.HostProtectionAttribute>.

#### <a name="code-analysis-rule"></a>Reguł analizy kodu

Dla programu SQL Server wszystkie metody używane do wprowadzania synchronizacji lub wątkowości musi oznaczone symbolem hPa pakietu. Obejmuje to metody, które udostępnianie stanu są synchronizowane i zarządzać procesami zewnętrznych. <xref:System.Security.Permissions.HostProtectionResource> Wartości, które mają wpływ na program SQL Server są <xref:System.Security.Permissions.HostProtectionResource.SharedState>, <xref:System.Security.Permissions.HostProtectionResource.Synchronization>, i <xref:System.Security.Permissions.HostProtectionResource.ExternalProcessMgmt>. Jednak dowolnej metody, która udostępnia żadnego <xref:System.Security.Permissions.HostProtectionResource> byli definiowani przez HPA, nie tylko te, które korzysta z zasobów mających wpływ na SQL.

### <a name="do-not-block-indefinitely-in-unmanaged-code"></a>W kodzie niezarządzanym nie blokują przez czas nieokreślony

Blokowanie w programie kodu niezarządzanego, zamiast w kodzie zarządzanym może spowodować "odmowa usługi", ponieważ środowisko CLR nie jest w stanie przerwania wątku.  Zablokowany wątek zapobiega CLR zwalnianie <xref:System.AppDomain>, co najmniej bez wykonania tej czynności kilka bardzo niebezpieczny operacji.  Blokuje, za pomocą systemu Win32 synchronizacji jest wyczyść przykładem coś, co firma Microsoft nie może dopuścić.  Blokowanie w wywołaniu `ReadFile` na gniazdo należy unikać, jeśli jest to możliwe — najlepiej Win32 API należy zapewnić mechanizm operacji, takiej jak to przekroczenie limitu czasu.

Dowolną metodę, która wywołuje native najlepiej należy używać wywołanie Win32 z rozsądne, ograniczone Przekroczono limit czasu.  Jeśli użytkownik może określić limit czasu, użytkownik nie powinien określić nieskończony limit czasu bez pewnych uprawnień zabezpieczeń.  Zaleca się, jeśli metoda zablokuje się przez więcej niż ~ 10 sekund, należy korzystać z wersji, który obsługuje limity czasu lub potrzebujesz dodatkowej pomocy CLR.

Poniżej przedstawiono kilka przykładów problematyczne interfejsów API.  Potoki (anonimowych i nazwanych) można tworzyć z limitem czasu; Jednakże, kod musi upewnić się, że nigdy nie wywołania `CreateNamedPipe` ani `WaitNamedPipe` z NMPWAIT_WAIT_FOREVER.  Ponadto może wystąpić nieoczekiwany, blokowanie, nawet jeśli jest określony limit czasu.  Wywoływanie `WriteFile` na potoku anonimowego blokuje, dopóki nie zostaną zapisane wszystkie bajty, co oznacza, jeśli bufor składa się z nieprzeczytane dane, `WriteFile` blokuje wywołania do momentu czytnik ma zwolnienie miejsca w buforze potoku.  Gniazda zawsze należy używać niektórych interfejsu API, który honoruje mechanizmu limitu czasu.

#### <a name="code-analysis-rule"></a>Reguł analizy kodu

Blokowanie bez limitu czasu w kodzie niezarządzanym jest typu "odmowa usługi". Nie wykonuj platformy wywołania do `WaitForSingleObject`, `WaitForSingleObjectEx`, `WaitForMultipleObjects`, `MsgWaitForMultipleObjects`, i `MsgWaitForMultipleObjectsEx`.  Nie należy używać NMPWAIT_WAIT_FOREVER.

### <a name="identify-any-sta-dependent-features"></a>Zidentyfikuj wszystkie funkcje zależne od STA.

Zidentyfikuj wszelki kod, który korzysta z modelu COM jednowątkowe apartamentach (STAs).  STAs są wyłączone w procesie programu SQL Server.  Funkcje, które są zależne od `CoInitialize`, takie jak liczniki wydajności lub Schowka, musi być wyłączone w programie SQL Server.

### <a name="ensure-finalizers-are-free-of-synchronization-problems"></a>Upewnij się, że finalizatory są wolne od problemów z synchronizacją

Wiele wątki finalizatorów, wątki może istnieć w przyszłych wersjach programu .NET Framework, co oznacza finalizatorów, dotyczy to różnych wystąpień tego samego typu, które są uruchomione jednocześnie.  Nie muszą być całkowicie bezpieczny wątkowo; Moduł zbierający elementy bezużyteczne gwarantuje, że tylko jeden wątek uruchomi finalizatora dla wystąpienia danego obiektu.  Jednak finalizatory muszą być kodowane, aby uniknąć wyścigu i zakleszczenie podczas uruchamiania jednocześnie na wielu wystąpień innego obiektu.  Korzystając z dowolny stan zewnętrzne, takie jak zapisywanie do pliku dziennika w finalizatora, problemy wielowątkowości dotyczące muszą być obsługiwane.  Nie należy polegać na finalizacji zapewnienie bezpieczeństwa wątków. Lokalny magazyn wątków, zarządzane lub natywne, nie należy używać do przechowywania stanu w wątku finalizatora.

#### <a name="code-analysis-rule"></a>Reguł analizy kodu

Finalizatory nie mogą być problemy z synchronizacją. Nie należy używać statycznych modyfikowalnego stanu w finalizatora.

### <a name="avoid-unmanaged-memory-if-possible"></a>Należy unikać niezarządzanej pamięci, jeśli jest to możliwe

Niezarządzanej pamięci mogą przedostawać, podobnie jak dojście systemu operacyjnego.  Jeśli to możliwe, spróbuj użyć pamięci na stosie przy użyciu [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md) lub przypiętych obiektu zarządzanego, takie jak [fixed Statement](~/docs/csharp/language-reference/keywords/fixed-statement.md) lub <xref:System.Runtime.InteropServices.GCHandle> przy użyciu byte [].  <xref:System.GC> Po pewnym czasie, które utraciły one.  Jednak jeśli należy przydzielić niezarządzanej pamięci, należy wziąć pod uwagę przy użyciu klasy, która pochodzi od klasy <xref:System.Runtime.InteropServices.SafeHandle> opakowywać alokacji pamięci.

Należy pamiętać, że istnieje co najmniej jeden przypadek gdzie <xref:System.Runtime.InteropServices.SafeHandle> jest niewystarczające.  Dla modelu COM wywołań metod, które przydzielenia lub zwolnienia pamięci jest typowe dla jednej biblioteki DLL, można przydzielić pamięci za pomocą `CoTaskMemAlloc` , a następnie innej biblioteki DLL powoduje zwolnienie pamięci za pomocą `CoTaskMemFree`.  Za pomocą <xref:System.Runtime.InteropServices.SafeHandle> w tych miejscach będzie niewłaściwe ponieważ spróbuje ona powiązanie okres istnienia niezarządzanej pamięci z okresem istnienia <xref:System.Runtime.InteropServices.SafeHandle> zamiast zezwalać innym kontrolującym DLL okresu istnienia pamięci.

### <a name="review-all-uses-of-catchexception"></a>Przejrzyj wszystkie przypadki użycia Catch(Exception)

CATCH bloków, catch, wszystkie wyjątki, zamiast jednego określonego wyjątku teraz będzie przechwytywać wyjątki asynchroniczne.  Sprawdź każdy blok catch(Exception), wyszukiwanie nie zasobów ważne przy zwalnianiu lub Wycofaj kod, który mogły zostać pominięte, a także potencjalnie nieprawidłowe zachowanie w bloku catch obsługi <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>, lub <xref:System.OutOfMemoryException>.  Należy pamiętać, że jest to możliwe, ten kod może się zalogować lub niektóre założenie, że go może być widoczna tylko niektóre wyjątki lub który zawsze wtedy, gdy ma miejsce wyjątek go nie powiodła się dla dokładnie jednej określonej przyczyny.  Może być konieczne zaktualizowano w celu uwzględnienia tych założeń <xref:System.Threading.ThreadAbortException>.

Należy wziąć pod uwagę wszystkie zmiany umieszcza tego catch, zostanie zgłoszony, wszystkie wyjątki przechwytywanie wyjątku, który powinien być określonego typu, takie jak <xref:System.FormatException> z parametrów metod formatowania.  Zapobiega uruchamianiu na nieoczekiwane wyjątki przez blok catch i może pomóc upewnić się, że kod nie ukrywa przez przechwytywanie wyjątków w nieoczekiwanych błędów.  Zgodnie z ogólną zasadą nigdy nie obsłużyć wyjątek w kodzie biblioteki (kod, który wymaga przechwytywać wyjątek, może oznaczać wad projektowych w kodzie, którą wywołujesz).  W niektórych przypadkach można przechwytywać wyjątek i zgłosić innego typu wyjątku zapewnienie większej ilości danych.  Użyj wyjątków zagnieżdżonych w tym przypadku przechowywanie rzeczywistych przyczynę niepowodzenia w <xref:System.Exception.InnerException%2A> właściwość nowy wyjątek.

#### <a name="code-analysis-rule"></a>Reguł analizy kodu

Przejrzyj wszystkie bloki catch w kodzie zarządzanym tego catch, wszystkie obiekty lub catch, wszystkie wyjątki.  W C#, oznacza to, że oba Oflagowanie `catch` {} i `catch(Exception)` {}.  Rozważ przekształcenie bardzo specyficzny typ wyjątku, lub przejrzyj kod, aby upewnić się, że nie działa w nieprawidłowy sposób Jeżeli przechwyci kontrolę typu nieoczekiwany wyjątek.

### <a name="do-not-assume-a-managed-thread-is-a-win32-thread--it-is-a-fiber"></a>Nie należy zakładać, wątek jest wątek Win32 — Fiber

Za pomocą programu managed wątku lokalnego magazynu działa, ale nie możesz użyć pamięci lokalnej wątku niezarządzanym lub przyjęto założenie, że kod zostaną ponownie uruchomione w bieżącym wątku systemu operacyjnego.  Nie należy zmieniać ustawienia, takie jak ustawienia regionalne dla wątku.  Nie wywołuj `InitializeCriticalSection` lub `CreateMutex` za pośrednictwem platformy wywołania, ponieważ wymagają one wątku systemu operacyjnego, który wprowadzi blokadę zakończyć działanie blokady.  Ponieważ nie będzie to wymagane podczas korzystania z włókien, sekcje krytyczne Win32 i muteksy nie można użyć w języku SQL bezpośrednio.  Należy pamiętać, że zarządzany <xref:System.Threading.Mutex> klasa nie obsługuje te rozważania koligacji wątku.

Można bezpiecznie korzystać z większości stanu na zarządzanej <xref:System.Threading.Thread> obiektu, łącznie z lokalnego magazynu zarządzanych wątków i bieżącej kultury interfejsu użytkownika dla wątku.  Można również użyć <xref:System.ThreadStaticAttribute>, co sprawia, że wartość istniejącej zmiennej statycznej dostępna tylko przez bieżący wątek zarządzanych (jest to magazyn lokalny włókien w CLR w inny sposób).  Podczas programowania modelu przyczyny, nie można zmienić bieżącej kultury wątku podczas uruchamiania w języku SQL.

#### <a name="code-analysis-rule"></a>Reguł analizy kodu

SQL Server jest uruchomiony w trybie włókien; nie należy używać pamięci lokalnej wątku. Należy unikać platformy wywołania do `TlsAlloc`, `TlsFree`, `TlsGetValue`, i `TlsSetValue.`

### <a name="let-sql-server-handle-impersonation"></a>Pozwól personifikacji dojście do serwera SQL

Ponieważ personifikacji działa na poziomie wątku, a SQL można uruchomić w trybie włókien kodu zarządzanego nie powinien personifikować użytkowników i nie powinien wywoływać `RevertToSelf`.

#### <a name="code-analysis-rule"></a>Reguł analizy kodu

Pozwalają obsłużyć personifikacji w programie SQL Server. Nie używaj `RevertToSelf`, `ImpersonateAnonymousToken`, `DdeImpersonateClient`, `ImpersonateDdeClientWindow`, `ImpersonateLoggedOnUser`, `ImpersonateNamedPipeClient`, `ImpersonateSelf`, `RpcImpersonateClient`, `RpcRevertToSelf`, `RpcRevertToSelfEx`, lub `SetThreadToken`.

### <a name="do-not-call-threadsuspend"></a>Nie wywołuj Thread::Suspend

Możliwość wstrzymywania wątek może pojawić się prostą operacją, ale może to spowodować zakleszczenia.  Jeśli wątek, używane do przechowywania blokady zostanie zawieszone przez drugi wątek, a następnie drugi wątek spróbuje wykonanie tych samych blokady, występuje zakleszczenia.  <xref:System.Threading.Thread.Suspend%2A> może zakłócać zabezpieczeń, ładowania klasy, komunikacji zdalnej i odbicia obecnie.

#### <a name="code-analysis-rule"></a>Reguł analizy kodu

Nie wywołuj <xref:System.Threading.Thread.Suspend%2A>. Należy wziąć pod uwagę przy użyciu rzeczywistego synchronizacji pierwotnych zamiast tego, takie jak <xref:System.Threading.Semaphore> lub <xref:System.Threading.ManualResetEvent> .

### <a name="protect-critical-operations-with-constrained-execution-regions-and-reliability-contracts"></a>Chroń krytyczne operacje ograniczone regiony wykonania i kontrakty niezawodności

Podczas wykonywania złożonych operacji, które aktualizuje stan udostępnionego lub wymagający w sposób deterministyczny albo w pełni powiedzie się lub w pełni zakończyć się niepowodzeniem, pamiętaj, że jest chroniony przez region ograniczonego wykonania (CER). Gwarantuje to, że kod działa w każdym przypadku, nawet wątku nagłego przerwania lub nagłego <xref:System.AppDomain> zwolnienia.

CER jest konkretny `try/finally` bloku natychmiast poprzedzony przez wywołanie <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>.

Spowoduje to więc nakazuje kompilatorowi just-in-time przygotowanie cały kod w bloku finally przed uruchomieniem `try` bloku. Gwarantuje to, że kod na końcu bloku jest wbudowana i będzie działać we wszystkich przypadkach. Nie jest nietypowy w CER ma pustą `try` bloku. Za pomocą CER chroni przed przerwanie asynchronicznego wątku i wyjątki o braku pamięci. Zobacz <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> formularza CER, który dodatkowo przepełnienie stosu obsługi dla nadmiernie szczegółowe kodu.

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.ConstrainedExecution>
- [Atrybuty ochrony hosta i programowanie SQL Server](../../../docs/framework/performance/sql-server-programming-and-host-protection-attributes.md)
