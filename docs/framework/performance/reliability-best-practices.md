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
ms.openlocfilehash: bd51ea1b79ac1dbd89a862f3961cc8508a87f301
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715981"
---
# <a name="reliability-best-practices"></a>Najlepsze rozwiązania dotyczące niezawodności

Następujące reguły niezawodności są ukierunkowane na SQL Server; jednak mają zastosowanie również do dowolnej aplikacji serwerowej opartej na hoście. Niezwykle ważne jest, aby serwery takie jak SQL Server nie wyciekować zasobów i nie zostały przesunięte.  Jednak nie można tego zrobić, pisząc kod zapasowy dla każdej metody, która zmienia stan obiektu.  Celem nie jest zapisanie przez 100 procent niezawodnego kodu zarządzanego, który odzyska się z błędów w każdej lokalizacji z kodem zapasowym.  Jest to zadanie zniechęcające z niewielką szansą sukcesu.  Środowisko uruchomieniowe języka wspólnego (CLR) nie może łatwo zapewnić mocnej wystarczającej ilości gwarancji do kodu zarządzanego, aby możliwe było napisanie doskonałego kodu.  Należy pamiętać, że w przeciwieństwie do ASP.NET, SQL Server używa tylko jednego procesu, którego nie można odtworzyć bez przełączenia bazy danych na nieakceptowalny czas.

Dzięki tym słabszym gwarancjom i działaniu w pojedynczym procesie niezawodność jest oparta na przerywaniu wątków lub odtwarzaniu domen aplikacji w razie potrzeby i podejmując środki ostrożności, aby zapewnić, że zasoby systemu operacyjnego, takie jak uchwyty lub pamięć, nie są wyciekami.  Nawet w przypadku tego prostszego ograniczenia niezawodności wciąż istnieje znacząca wymagana niezawodność:

- Nigdy nie wycieka zasobów systemu operacyjnego.

- Zidentyfikuj wszystkie zarządzane blokady we wszystkich formularzach do środowiska CLR.

- Nigdy nie przerywaj współużytkowanego stanu domeny, co pozwala na bezproblemowe odtwarzanie <xref:System.AppDomain>.

Chociaż jest teoretycznie możliwe, aby napisać kod zarządzany do obsługi wyjątków <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>i <xref:System.OutOfMemoryException>, oczekuje się, że deweloperzy będą pisać takie niezawodne kod w całej aplikacji.  Z tego powodu wyjątki poza pasmem powodują przerwanie wykonywania wątku. a jeśli wątek przerwał edytowanie stanu udostępnionego, który można określić, czy wątek utrzymuje blokadę, <xref:System.AppDomain> zostanie zwolniona.  Gdy metoda, która edytuje stan udostępniony, zostanie zakończona, stan będzie uszkodzony, ponieważ nie jest możliwe zapisanie niezawodnego kodu zapasowego dla aktualizacji stanu udostępnionego.

W .NET Framework w wersji 2,0, jedyny Host wymagający niezawodności jest SQL Server.  Jeśli zestaw zostanie uruchomiony na SQL Server należy wykonać niezawodność dla każdej części tego zestawu, nawet jeśli istnieją konkretne funkcje, które są wyłączone w przypadku uruchamiania w bazie danych programu.  Jest to wymagane, ponieważ aparat analizy kodu analizuje kod na poziomie zestawu i nie może odróżnić wyłączonego kodu. Innym SQL Serverom programowania jest to, że SQL Server uruchamia wszystko w jednym procesie, a odtwarzanie <xref:System.AppDomain> służy do czyszczenia wszystkich zasobów, takich jak pamięć i uchwyty systemu operacyjnego.

Nie można zależeć od finalizatorów lub destruktorów ani `try/finally` bloków dla kodu zapasowego. Mogą być one przerywane lub niewywoływane.

Wyjątki asynchroniczne można zgłaszać w nieoczekiwanych lokalizacjach, prawdopodobnie każda instrukcja maszynowa: <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>i <xref:System.OutOfMemoryException>.

Zarządzane wątki nie są koniecznie wątki Win32 w programie SQL Server; mogą być włókien.

W przypadku domeny o szerokim zasięgu lub aplikacjach przetwarzanych poza aplikacjami jest niezwykle trudne do zmiany i należy je unikać, gdy jest to możliwe.

Warunki braku pamięci nie są rzadkie w SQL Server.

Jeśli biblioteki hostowane w SQL Server nie będą poprawnie aktualizować swojego udostępnionego stanu, istnieje wysokie prawdopodobieństwo, że kod nie zostanie odzyskany, dopóki baza danych nie zostanie ponownie uruchomiona.  Ponadto w niektórych ekstremalnych przypadkach możliwe może być niepowodzenie procesu SQL Server, powodując ponowne uruchomienie bazy danych.  Ponowne uruchomienie bazy danych może spowolnić witrynę sieci Web lub wpłynąć na operacje firmy, co pogarsza dostępność.  Wolne wycieki zasobów systemu operacyjnego, takich jak pamięć lub dojścia, może spowodować, że serwer zakończył się niepowodzeniem przydzielenia dojścia bez możliwości odzyskiwania lub prawdopodobnie serwer może pogorszyć wydajność i zmniejszyć poziom wydajności aplikacji klienta. opóźnienie.  Jasno chcemy unikać tych scenariuszy.

## <a name="best-practice-rules"></a>Reguły najlepszych rozwiązań

Wprowadzenie koncentruje się na tym, co należy sprawdzić w kodzie zarządzanym kodu, który działa na serwerze, aby zwiększyć stabilność i niezawodność platformy. Wszystkie te testy są ogólnie zalecane i bezwzględne na serwerze.

W przypadku ograniczenia zamkniętej blokady lub zasobu, SQL Server przerywa wątek lub spowalnia <xref:System.AppDomain>.  W takim przypadku należy uruchomić tylko kod zapasowy w ograniczonym regionie wykonywania (CER).

### <a name="use-safehandle-to-avoid-resource-leaks"></a>Użyj elementu SafeHandle, aby uniknąć przecieków zasobów

W przypadku <xref:System.AppDomain> Unload nie można zależeć od bloków `finally` lub finalizatorów, dlatego ważne jest, aby przede wszystkim uzyskać dostęp do zasobów systemu operacyjnego za pomocą klasy <xref:System.Runtime.InteropServices.SafeHandle>, a nie <xref:System.IntPtr>, <xref:System.Runtime.InteropServices.HandleRef>lub podobnych klas. Dzięki temu środowisko CLR będzie śledzić i zamykać wykorzystywane przez Ciebie uchwyty nawet w przypadku wyrywania <xref:System.AppDomain>.  <xref:System.Runtime.InteropServices.SafeHandle> będzie używać finalizatora krytycznego, który będzie zawsze uruchamiany przez środowisko CLR.

Dojście systemu operacyjnego jest przechowywane w bezpiecznym obsłudze od momentu jego utworzenia do momentu jego zwolnienia.  Nie ma okna, w którym <xref:System.Threading.ThreadAbortException> może wystąpić przeciek dojścia.  Dodatkowo wywołanie platformy będzie odwoływać się do dojścia, które umożliwia zamknięcie śledzenia okresu istnienia dojścia, uniemożliwiając problem z zabezpieczeniami z sytuacją wyścigu między `Dispose` i metodą, która aktualnie korzysta z dojścia.

Większość klas, które obecnie mają finalizator do zwykłego oczyszczenia dojścia systemu operacyjnego, nie potrzebuje już finalizatora. Zamiast tego finalizator będzie znajdował się w klasie pochodnej <xref:System.Runtime.InteropServices.SafeHandle>.

Należy zauważyć, że <xref:System.Runtime.InteropServices.SafeHandle> nie zastępuje <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>.  Nadal istnieją potencjalne korzyści związane z rywalizacją o zasoby i wydajność w celu jawnego usuwania zasobów systemu operacyjnego.  Wystarczy pamiętać, że bloki `finally`, które jawnie usuwają zasoby, mogą nie zostać wykonane do ukończenia.

<xref:System.Runtime.InteropServices.SafeHandle> umożliwia zaimplementowanie własnej metody <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>, która wykonuje zadania w celu zwolnienia dojścia, na przykład przekazanie stanu do procedury zwalniania obsługi systemu operacyjnego lub zwolnienie zestawu dojść w pętli.  Środowisko CLR gwarantuje, że ta metoda jest uruchamiana.  Jest odpowiedzialny za twórcę implementacji <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>, aby upewnić się, że dojście zostanie wydane we wszystkich okolicznościach. Niewykonanie tej czynności spowoduje przeciek uchwytu, co często skutkuje wyciekiem zasobów natywnych skojarzonych z dojściem. W związku z tym ma kluczowe znaczenie dla struktury <xref:System.Runtime.InteropServices.SafeHandle> klas pochodnych, aby implementacja <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> nie wymagała alokacji żadnych zasobów, które mogą nie być dostępne w czasie wywołania. Należy zauważyć, że dozwolone jest wywoływanie metod, które mogą kończyć się niepowodzeniem w ramach implementacji <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A>, pod warunkiem, że kod może obsłużyć takie błędy i zakończyć kontrakt, aby zwolnić uchwyt macierzysty. Na potrzeby debugowania <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> ma <xref:System.Boolean> wartość zwracana, która może być ustawiona na `false` w przypadku napotkania błędu krytycznego, który uniemożliwia wydanie zasobu. Wykonanie tej czynności spowoduje aktywowanie [releaseHandleFailed](../debug-trace-profile/releasehandlefailed-mda.md) MDA, jeśli jest włączone, aby pomóc w zidentyfikowaniu problemu. Nie ma to wpływu na środowisko uruchomieniowe w żaden inny sposób; <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> nie zostanie ponownie wywołana dla tego samego zasobu i w związku z tym dojście zostanie ujawnione.

<xref:System.Runtime.InteropServices.SafeHandle> nie są odpowiednie w niektórych kontekstach.  Ponieważ metoda <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle%2A> może być uruchamiana w wątku <xref:System.GC> finalizatora, wszelkie dojścia, które są wymagane do zwolnienia w określonym wątku, nie powinny być opakowane w <xref:System.Runtime.InteropServices.SafeHandle>.

Wywoływane otoki środowiska uruchomieniowego (RCW) mogą być czyszczone przez środowisko CLR bez dodatkowego kodu.  Dla kodu, który używa wywołania platformy i traktuje obiekt COM jako `IUnknown*` lub <xref:System.IntPtr>, należy ponownie napisać kod, aby użyć otoki RCW.  <xref:System.Runtime.InteropServices.SafeHandle> mogą nie być odpowiednie dla tego scenariusza ze względu na możliwość wywołania niezarządzanej metody wydania z powrotem do kodu zarządzanego.

#### <a name="code-analysis-rule"></a>Reguła analizy kodu

Użyj <xref:System.Runtime.InteropServices.SafeHandle> do hermetyzacji zasobów systemu operacyjnego. Nie należy używać <xref:System.Runtime.InteropServices.HandleRef> ani pól typu <xref:System.IntPtr>.

### <a name="ensure-finalizers-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Upewnij się, że nie trzeba uruchamiać finalizatorów, aby zapobiec przeciekom zasobów systemu operacyjnego

Uważnie Przejrzyj finalizatory, aby upewnić się, że nawet jeśli nie są uruchamiane, krytyczny zasób systemu operacyjnego nie jest wycieka.  W przeciwieństwie do normalnego <xref:System.AppDomain> Unload, gdy aplikacja jest wykonywana w stanie stałym lub gdy serwer, taki jak SQL Server, zostanie zamknięty, obiekty nie są finalizowane podczas nieoczekiwanego <xref:System.AppDomain> wyładowania.  Upewnij się, że zasoby nie są wyciekami w przypadku nieoczekiwanej zwolnienia, ponieważ nie można zagwarantować poprawności aplikacji, ale integralność serwera musi być utrzymywana przez nie wycieki zasobów.  Użyj <xref:System.Runtime.InteropServices.SafeHandle>, aby zwolnić wszystkie zasoby systemu operacyjnego.

### <a name="ensure-that-finally-clauses-do-not-have-to-run-to-prevent-leaking-operating-system-resources"></a>Upewnij się, że klauzule finally nie muszą działać, aby zapobiec przeciekom zasobów systemu operacyjnego

klauzule `finally` nie są gwarantowane do uruchomienia poza programem CERs, co wymaga, aby deweloperzy biblioteki nie korzystali z kodu w bloku `finally` do zwolnienia niezarządzanych zasobów.  Zalecanym rozwiązaniem jest użycie <xref:System.Runtime.InteropServices.SafeHandle>.

#### <a name="code-analysis-rule"></a>Reguła analizy kodu

Użyj <xref:System.Runtime.InteropServices.SafeHandle> do czyszczenia zasobów systemu operacyjnego, a nie `Finalize`. Nie należy używać <xref:System.IntPtr>; Użyj <xref:System.Runtime.InteropServices.SafeHandle> do hermetyzacji zasobów. Jeśli klauzula finally musi być uruchomiona, należy ją umieścić w CER.

### <a name="all-locks-should-go-through-existing-managed-locking-code"></a>Wszystkie blokady powinny przechodzić przez istniejący zarządzany kod blokowania

Środowisko CLR musi wiedzieć, gdy kod jest w blokadzie, dzięki czemu będzie wiadomo, że <xref:System.AppDomain>, a nie tylko przerwanie wątku.  Przerywanie wątku może być niebezpieczne, ponieważ dane obsługiwane przez wątek mogą pozostać w niespójnym stanie. W związku z tym cały <xref:System.AppDomain> musi być odtwarzany.  Skutkiem niepowodzenia identyfikacji blokady mogą być zakleszczenia lub nieprawidłowe wyniki. Użyj metod <xref:System.Threading.Thread.BeginCriticalRegion%2A> i <xref:System.Threading.Thread.EndCriticalRegion%2A> do identyfikowania regionów blokady.  Są one metodami statycznymi w klasie <xref:System.Threading.Thread>, które mają zastosowanie tylko do bieżącego wątku, co uniemożliwia jednemu wątkowi edytowanie liczby blokad innego wątku.

<xref:System.Threading.Monitor.Enter%2A> i <xref:System.Threading.Monitor.Exit%2A> mają wbudowane powiadomienie środowiska CLR, dlatego zaleca się ich użycie, a także użycie [instrukcji lock](../../csharp/language-reference/keywords/lock-statement.md), która używa tych metod.

Inne mechanizmy blokowania, takie jak blokady i <xref:System.Threading.AutoResetEvent> muszą wywoływać te metody w celu powiadomienia środowiska CLR o wprowadzeniu sekcji krytycznej.  Te metody nie przyjmują żadnych blokad; informują one CLR, że kod jest wykonywany w sekcji krytycznej, a przerywanie wątku może pozostawiać stan współużytkowany niespójny.  Jeśli zdefiniowano własny typ blokady, taki jak niestandardowa Klasa <xref:System.Threading.ReaderWriterLock>, Użyj tych metod liczby blokad.

#### <a name="code-analysis-rule"></a>Reguła analizy kodu

Oznacz i zidentyfikuj wszystkie blokady przy użyciu <xref:System.Threading.Thread.BeginCriticalRegion%2A> i <xref:System.Threading.Thread.EndCriticalRegion%2A>. W pętli nie należy używać <xref:System.Threading.Interlocked.CompareExchange%2A>, <xref:System.Threading.Interlocked.Increment%2A>i <xref:System.Threading.Interlocked.Decrement%2A>.  Nie wykonuj wywołania platformy dla wariantów Win32 tych metod.  Nie należy używać <xref:System.Threading.Thread.Sleep%2A> w pętli.  Nie używaj pól nietrwałych.

### <a name="cleanup-code-must-be-in-a-finally-or-a-catch-block-not-following-a-catch"></a>Kod czyszczący musi znajdować się w bloku finally lub catch, a nie po przechwyceniu

Kod czyszczący nigdy nie powinien występować w bloku `catch`; powinien znajdować się w `finally` lub w samym bloku `catch`. Powinno to być normalne dobre rozwiązanie. Blok `finally` jest ogólnie preferowany, ponieważ ma ten sam kod zarówno w przypadku zgłoszenia wyjątku, jak i zakończenia ostatniego bloku `try`.  W przypadku zgłaszania nieoczekiwanego wyjątku, na przykład <xref:System.Threading.ThreadAbortException>, kod czyszczący nie zostanie uruchomiony.  Wszystkie niezarządzane zasoby, które można oczyścić w `finally` powinny być w <xref:System.Runtime.InteropServices.SafeHandle> zawinięte, aby zapobiec wyciekom.  Zwróć uwagę C# , że słowo kluczowe `using` może być efektywnie używane do usuwania obiektów, w tym dojścia.

Mimo że <xref:System.AppDomain> recykling może czyścić zasoby w wątku finalizatora, nadal ważne jest, aby w prawidłowym miejscu umieścić kod czyszczący. Należy pamiętać, że jeśli wątek odbiera wyjątek asynchroniczny bez utrzymywania blokady, środowisko CLR próbuje zakończyć wątek bez konieczności odtwarzania <xref:System.AppDomain>.  Zapewnienie, że zasoby są czyszczone wcześniej, a nie w przyszłości, dzięki zwiększeniu liczby dostępnych zasobów i lepszym zarządzaniu okresem istnienia. Jeśli nie zamykasz jawnie dojścia do pliku w pewnej ścieżce kodu błędu, poczekaj, aż <xref:System.Runtime.InteropServices.SafeHandle> finalizator, przy następnym uruchomieniu kodu może się nie powieść, próbując uzyskać dostęp do tego samego pliku, jeśli finalizator nie został jeszcze uruchomiony.  Z tego powodu, aby upewnić się, że kod czyszczący istnieje i działa prawidłowo, zapewni bardziej czyste i szybkie odzyskiwanie po błędach, nawet jeśli nie jest to absolutnie konieczne.

#### <a name="code-analysis-rule"></a>Reguła analizy kodu

Kod czyszczący po `catch` musi znajdować się w bloku `finally`. Umieść wywołania do usunięcia w bloku finally. bloki `catch` powinny kończyć się generowaniem lub wyrzucaniem. Mimo że będą istnieć wyjątki, takie jak kod wykrywający, czy można nawiązać połączenie sieciowe, w przypadku których można uzyskać dowolną liczbę wyjątków, każdy kod wymagający przechwycenia wielu wyjątków w normalnych warunkach powinien dać wskazanie, że kod powinien zostać przetestowany, aby sprawdzić, czy będzie się on kończyć pomyślnie.

### <a name="process-wide-mutable-shared-state-between-application-domains-should-be-eliminated-or-use-a-constrained-execution-region"></a>Niemodyfikowalny współużytkowany stan procesu między domenami aplikacji należy wyeliminować lub użyć ograniczonego regionu wykonywania

Zgodnie z opisem we wprowadzeniu, może być bardzo trudne, aby napisać kod zarządzany, który monitoruje stan współużytkowany w całej domenie aplikacji w niezawodny sposób.  Współużytkowany stan procesu jest dowolnym rodzajem struktury danych współdzielonym między domenami aplikacji, w kodzie Win32, wewnątrz środowiska CLR lub w zarządzanym kodzie przy użyciu komunikacji zdalnej.  Każdy modyfikowalny stan współużytkowany jest bardzo trudny do poprawnego zapisu w kodzie zarządzanym, a wszystkie statyczne Stany udostępnione mogą być wykonywane tylko z dużą ostrożnością.  Jeśli masz współużytkowany stan dla całego procesu lub całego komputera, Znajdź jakiś sposób, aby go wyeliminować lub chronić współużytkowany stan przy użyciu ograniczonego regionu wykonywania (CER).  Należy pamiętać, że każda biblioteka ze stanem udostępnionym, który nie został zidentyfikowany i poprawiona, może spowodować, że host, taki jak SQL Server, wymaga czystego <xref:System.AppDomain> wyładowania do awarii.

Jeśli kod używa obiektu COM, należy unikać udostępniania tego obiektu COM między domenami aplikacji.

### <a name="locks-do-not-work-process-wide-or-between-application-domains"></a>Blokady nie działają dla całego procesu ani między domenami aplikacji.

W przeszłości <xref:System.Threading.Monitor.Enter%2A> i [instrukcja Lock](../../csharp/language-reference/keywords/lock-statement.md) została użyta do utworzenia globalnych blokad procesów.  Na przykład zdarza się to w przypadku blokowania <xref:System.AppDomain> metod agile, takich jak <xref:System.Type> wystąpienia z zestawów nieudostępnionych, <xref:System.Threading.Thread> obiektów, wyciągów z stażystów i niektórych ciągów współużytkowanych przez domeny aplikacji przy użyciu komunikacji zdalnej.  Te blokady nie są już cały proces.  Aby określić obecność blokady domeny międzyaplikacji obejmującej cały proces, ustal, czy kod w ramach blokady używa dowolnego zewnętrznego, utrwalonego zasobu, takiego jak plik na dysku lub prawdopodobnie baza danych.

Należy pamiętać, że po zablokowaniu w <xref:System.AppDomain> mogą powodować problemy, Jeśli chroniony kod używa zasobu zewnętrznego, ponieważ ten kod może działać jednocześnie w wielu domenach aplikacji.  Może to być problem podczas zapisywania do jednego pliku dziennika lub powiązania do gniazda dla całego procesu.  Te zmiany oznaczają, że nie można w prosty sposób korzystać z kodu zarządzanego, aby uzyskać blokadę globalną procesu, inną niż użycie nazwanego <xref:System.Threading.Mutex> lub wystąpienia <xref:System.Threading.Semaphore>.  Utwórz kod, który nie działa jednocześnie w dwóch domenach aplikacji, lub użyj klas <xref:System.Threading.Mutex> lub <xref:System.Threading.Semaphore>.  Jeśli nie można zmienić istniejącego kodu, nie należy używać Win32 o nazwie mutex do osiągnięcia tej synchronizacji, ponieważ działa w trybie Fiber, nie można zagwarantować, że ten sam wątek systemu operacyjnego uzyska i zwolni element mutex.  Należy użyć zarządzanej klasy <xref:System.Threading.Mutex> lub nazwanej <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>lub <xref:System.Threading.Semaphore>, aby zsynchronizować blokadę kodu w sposób, w jaki środowisko CLR ma świadomość zamiast synchronizowania blokady przy użyciu kodu niezarządzanego.

#### <a name="avoid-locktypeofmytype"></a>Unikaj blokady (typeof (MyType))

Prywatne i publiczne obiekty <xref:System.Type> w zestawach współużytkowanych mają tylko jedną kopię kodu współużytkowaną we wszystkich domenach aplikacji.  Dla zestawów współużytkowanych istnieje tylko jedno wystąpienie <xref:System.Type> na proces, co oznacza, że wiele domen aplikacji współużytkuje dokładnie te same <xref:System.Type> wystąpienie.  Zablokowanie wystąpienia <xref:System.Type> ma blokadę, która ma wpływ na cały proces, a nie tylko na <xref:System.AppDomain>.  Jeśli jeden <xref:System.AppDomain> przyjmuje blokadę obiektu <xref:System.Type>, ten wątek zostaje nagle przerwany, nie spowoduje zwolnienia blokady.  Ta blokada może spowodować zakleszczenie innych domen aplikacji.

Dobrym sposobem na wykonywanie blokad w metodach statycznych jest dodanie statycznego obiektu synchronizacji wewnętrznej do kodu.  Ten element może zostać zainicjowany w konstruktorze klasy, jeśli jest obecny, ale jeśli nie można go zainicjować w następujący sposób:

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

Następnie przy zablokowaniu należy użyć właściwości `InternalSyncObject`, aby uzyskać obiekt do zablokowania.  Nie trzeba używać właściwości, jeśli w konstruktorze klasy został zainicjowany obiekt synchronizacji wewnętrznej.  Kod inicjalizacji blokady podwójnej kontroli powinien wyglądać podobnie do tego przykładu:

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

#### <a name="a-note-about-lockthis"></a>Uwaga dotycząca blokady (ta)

Ogólnie akceptowalne jest zablokowanie pojedynczego obiektu, który jest publicznie dostępny.  Jeśli jednak obiekt jest pojedynczym obiektem, który może spowodować zakleszczenie całego podsystemu, rozważ użycie powyższego wzorca projektowego.  Na przykład blokada jednego obiektu <xref:System.Security.SecurityManager> może spowodować zakleszczenie w obrębie <xref:System.AppDomain>, co sprawia, że cały <xref:System.AppDomain> stanie się bezużyteczny. Dobrym sposobem, aby nie korzystać z blokady na publicznie dostępnym obiekcie tego typu.  Jednak blokada pojedynczej kolekcji lub tablicy nie powinna ogólnie stwarzać problemu.

#### <a name="code-analysis-rule"></a>Reguła analizy kodu

Nie należy stosować blokad dla typów, które mogą być używane między domenami aplikacji lub nie mają silnego sensu tożsamości. Nie wywołuj <xref:System.Threading.Monitor.Enter%2A> na <xref:System.Type>, <xref:System.Reflection.MethodInfo>, <xref:System.Reflection.PropertyInfo>, <xref:System.String>, <xref:System.ValueType>, <xref:System.Threading.Thread>lub dowolnego obiektu, który pochodzi z <xref:System.MarshalByRefObject>.

### <a name="remove-gckeepalive-calls"></a>Usuwanie wykazu globalnego. Wywołania utrzymywania aktywności

Znaczna ilość istniejącego kodu nie używa <xref:System.GC.KeepAlive%2A>, gdy powinien lub użyje go, gdy nie jest to odpowiednie.  Po przeprowadzeniu konwersji do <xref:System.Runtime.InteropServices.SafeHandle>, klasy nie muszą wywoływać <xref:System.GC.KeepAlive%2A>, przy założeniu, że nie mają finalizatora, ale polegają na <xref:System.Runtime.InteropServices.SafeHandle> do sfinalizowania dojść systemu operacyjnego.  Chociaż koszt wydajności zachowywania wywołania <xref:System.GC.KeepAlive%2A> może być nieistotny, postrzeganie, że wywołanie <xref:System.GC.KeepAlive%2A> jest niezbędne lub wystarczające, aby rozwiązać problem z okresem istnienia, który może już nie istnieć, utrudnia utrzymywanie kodu.  Jednak w przypadku korzystania z wywoływanych otok (RCW) modelu COM międzyoperacyjności, <xref:System.GC.KeepAlive%2A> jest nadal wymagana przez kod.

#### <a name="code-analysis-rule"></a>Reguła analizy kodu

Usuń <xref:System.GC.KeepAlive%2A>.

### <a name="use-the-hostprotection-attribute"></a>Użyj atrybutu HostProtection

<xref:System.Security.Permissions.HostProtectionAttribute> (HPA) służy do określenia wymagań dotyczących ochrony hosta, co pozwala hostowi zapobiegać wywoływaniu niektórych metod, które są nieodpowiednie dla danego hosta, takie jak <xref:System.Environment.Exit%2A> lub <xref:System.Windows.Forms.MessageBox.Show%2A> SQL Server.

HPA ma wpływ tylko na niezarządzane aplikacje obsługujące środowisko uruchomieniowe języka wspólnego i implementowanie ochrony hosta, takie jak SQL Server. Po zastosowaniu Akcja zabezpieczeń powoduje utworzenie żądania linku opartego na zasobach hosta, które udostępnia Klasa lub metoda. Jeśli kod jest uruchamiany w aplikacji klienckiej lub na serwerze, który nie jest chroniony przez hosta, atrybut "Parowanie"; nie została wykryta i dlatego nie jest stosowana.

> [!IMPORTANT]
> Ten atrybut ma na celu wymuszenie wytycznych dotyczących modelu programowania specyficznych dla hosta, a nie zachowania zabezpieczeń.  Chociaż żądanie linku jest używane do sprawdzania zgodności z wymaganiami modelu programowania, <xref:System.Security.Permissions.HostProtectionAttribute> nie jest uprawnieniem zabezpieczeń.

Jeśli host nie ma wymagań dotyczących modelu programowania, wymagania dotyczące linków nie występują.

Ten atrybut identyfikuje następujące elementy:

- Metody lub klasy, które nie pasują do modelu programowania hosta, ale są niegroźne.

- Metody lub klasy, które nie pasują do modelu programowania hosta i mogą prowadzić do destabilizacji kodu użytkownika zarządzanego przez serwer.

- Metody lub klasy, które nie pasują do modelu programowania hosta i mogą prowadzić do destabilizacji samego procesu serwera.

> [!NOTE]
> W przypadku tworzenia biblioteki klas, która ma być wywoływana przez aplikacje, które mogą być wykonywane w środowisku chronionym hosta, należy zastosować ten atrybut do członków, którzy uwidaczniają <xref:System.Security.Permissions.HostProtectionResource> kategorii zasobów. Członkowie biblioteki klas .NET Framework z tym atrybutem powodują, że tylko bezpośredni obiekt wywołujący zostanie sprawdzony.  Członek biblioteki musi również spowodować sprawdzenie jego bezpośredniego obiektu wywołującego w taki sam sposób.

Więcej informacji na temat HPA można znaleźć w <xref:System.Security.Permissions.HostProtectionAttribute>.

#### <a name="code-analysis-rule"></a>Reguła analizy kodu

W przypadku SQL Server wszystkie metody służące do wprowadzania synchronizacji lub wątkowości muszą być identyfikowane za pomocą HPA. Obejmuje to metody, które udostępniają stan, są synchronizowane lub zarządzają procesami zewnętrznymi. <xref:System.Security.Permissions.HostProtectionResource> wartości mające wpływ SQL Server są <xref:System.Security.Permissions.HostProtectionResource.SharedState>, <xref:System.Security.Permissions.HostProtectionResource.Synchronization>i <xref:System.Security.Permissions.HostProtectionResource.ExternalProcessMgmt>. Jednakże każda metoda, która uwidacznia wszelkie <xref:System.Security.Permissions.HostProtectionResource>, powinna być identyfikowana przez HPA, a nie tylko te, które mają wpływ na SQL.

### <a name="do-not-block-indefinitely-in-unmanaged-code"></a>Nie blokuj na czas nieokreślony w kodzie niezarządzanym

Zablokowanie w kodzie niezarządzanym zamiast w kodzie zarządzanym może spowodować atak typu "odmowa usługi", ponieważ środowisko CLR nie może przerwać wątku.  Zablokowany wątek uniemożliwia programowi CLR zwolnienie <xref:System.AppDomain>, co najmniej bez wykonywania niektórych bardzo niebezpiecznych operacji.  Blokowanie przy użyciu elementu podstawowego synchronizacji systemu Windows to oczywisty przykład niedozwolonego elementu.  Jeśli to możliwe, należy unikać blokowania w wywołaniu `ReadFile` w gnieździe — najlepiej, gdy interfejs API systemu Windows powinien zapewnić mechanizm dla operacji, takich jak to, aby przekroczyć limit czasu.

Wszystkie metody, które wywołuje do natywnego, powinny używać wywołania Win32 z rozsądnym, ograniczonym limitem czasu.  Jeśli użytkownik może określić limit czasu, użytkownik nie powinien być uprawniony do określania nieskończonego limitu czasu bez określonego uprawnienia zabezpieczeń.  Jako wskazówkę, jeśli metoda będzie blokować ponad 10 sekund, należy używać wersji, która obsługuje limity czasu, lub potrzebna jest dodatkowa obsługa środowiska CLR.

Poniżej przedstawiono kilka przykładów problematycznych interfejsów API.  Potoki (anonimowe i nazwane) można utworzyć z limitem czasu; Jednak kod musi upewnić się, że nigdy nie wywołuje `CreateNamedPipe` ani `WaitNamedPipe` z NMPWAIT_WAIT_FOREVER.  Ponadto może wystąpić nieoczekiwane blokowanie nawet w przypadku określenia limitu czasu.  Wywołanie `WriteFile` w potoku anonimowym będzie blokowane do momentu zapisania wszystkich bajtów, co oznacza, że bufor nie odczytał danych, wywołanie `WriteFile` zostanie zablokowane do momentu, gdy czytnik zwolni miejsce w buforze potoku.  Gniazda powinny zawsze używać niektórych interfejsów API, które zapewnią mechanizm przekroczenia limitu czasu.

#### <a name="code-analysis-rule"></a>Reguła analizy kodu

Zablokowanie bez limitu czasu w kodzie niezarządzanym oznacza atak typu "odmowa usługi". Nie wykonuj wywołań wywoływanych przez platformę do `WaitForSingleObject`, `WaitForSingleObjectEx`, `WaitForMultipleObjects`, `MsgWaitForMultipleObjects`i `MsgWaitForMultipleObjectsEx`.  Nie należy używać NMPWAIT_WAIT_FOREVER.

### <a name="identify-any-sta-dependent-features"></a>Identyfikowanie wszelkich funkcji zależnych od STA

Zidentyfikuj każdy kod, który używa apartamentach pojedynczego wątku COM (STAs).  STAs są wyłączone w procesie SQL Server.  Funkcje, które są zależne od `CoInitialize`, takie jak liczniki wydajności lub schowek, muszą być wyłączone w SQL Server.

### <a name="ensure-finalizers-are-free-of-synchronization-problems"></a>Upewnij się, że finalizatory nie mają problemów z synchronizacją

W przyszłych wersjach .NET Framework może istnieć wiele wątków finalizatorów, co oznacza, że finalizatory dla różnych wystąpień tego samego typu są uruchamiane jednocześnie.  Nie muszą być całkowicie bezpieczne wątkowo. Moduł wyrzucania elementów bezużytecznych gwarantuje, że tylko jeden wątek uruchomi finalizator dla danego wystąpienia obiektu.  Jednakże finalizatory muszą być kodowane, aby uniknąć sytuacji wyścigu i zakleszczenii podczas jednoczesnego uruchamiania na wielu różnych wystąpieniach obiektów.  W przypadku korzystania z dowolnego stanu zewnętrznego, takiego jak zapis w pliku dziennika, w finalizatorze należy obsługiwać problemy wątkowości.  Nie należy polegać na finalizowaniu w celu zapewnienia bezpieczeństwa wątków. Nie używaj magazynu lokalnego wątku, zarządzanego lub natywnego, aby przechowywać stan w wątku finalizatora.

#### <a name="code-analysis-rule"></a>Reguła analizy kodu

Finalizatory muszą być pozbawione problemów z synchronizacją. Nie należy używać statycznego stanu mutable w finalizatorze.

### <a name="avoid-unmanaged-memory-if-possible"></a>Unikaj niezarządzanej pamięci, jeśli jest to możliwe

Niezarządzana pamięć może być przeciekiem, podobnie jak dojście systemu operacyjnego. Jeśli to możliwe, spróbuj użyć pamięci na stosie przy użyciu [stackalloc](../../csharp/language-reference/operators/stackalloc.md) lub przypiętego obiektu zarządzanego, takiego jak [instrukcja FIXED](../../csharp/language-reference/keywords/fixed-statement.md) lub <xref:System.Runtime.InteropServices.GCHandle> przy użyciu typu Byte []. <xref:System.GC> ostatecznie czyści te. Jeśli jednak należy przydzielić pamięć niezarządzaną, należy rozważyć użycie klasy, która pochodzi od <xref:System.Runtime.InteropServices.SafeHandle>, aby otoczyć alokację pamięci.

Należy zauważyć, że istnieje co najmniej jeden przypadek, w którym <xref:System.Runtime.InteropServices.SafeHandle> nie jest wystarczający. W przypadku wywołań metod COM, które przydzielą lub zwalniają pamięć, typowe dla jednej biblioteki DLL do przydzielania pamięci za pośrednictwem `CoTaskMemAlloc` następnie inna Biblioteka DLL zwolni tę pamięć z `CoTaskMemFree`.  Użycie <xref:System.Runtime.InteropServices.SafeHandle> w tych miejscach byłoby nieodpowiednie, ponieważ podejmie próbę powiązania okresu istnienia niezarządzanej pamięci z okresem istnienia <xref:System.Runtime.InteropServices.SafeHandle> zamiast zezwalania innej bibliotece DLL na kontrolowanie okresu istnienia pamięci.

### <a name="review-all-uses-of-catchexception"></a>Przejrzyj wszystkie zastosowania catch (Exception)

Bloki catch, które przechwytują wszystkie wyjątki zamiast jednego konkretnego wyjątku, przechwytuje teraz także asynchroniczne wyjątki. Sprawdzaj każdy blok catch (Exception), szukając nieważnego kodu zwolnienia zasobów lub Wycofaj, który może zostać pominięty, a także potencjalnie niepoprawnego zachowania w obrębie bloku catch do obsługi <xref:System.Threading.ThreadAbortException>, <xref:System.StackOverflowException>lub <xref:System.OutOfMemoryException>.  Należy zauważyć, że jest możliwe, że ten kod może być rejestrowany lub założono, że może on tylko widzieć pewne wyjątki, lub że w przypadku wystąpienia wyjątku nie powiodło się z dokładnie jedną z określonych przyczyn.  Te założenia mogą wymagać aktualizacji w celu uwzględnienia <xref:System.Threading.ThreadAbortException>.

Rozważ zmianę wszystkich miejsc, które przechwytują wszystkie wyjątki, aby przechwycić określony typ wyjątku, który będzie oczekiwany, na przykład <xref:System.FormatException> z metod formatowania ciągu.  Zapobiega to uruchamianiu bloku catch w przypadku nieoczekiwanych wyjątków i pomaga upewnić się, że kod nie ukrywa błędów przez przechwycenie nieoczekiwanych wyjątków.  Ponieważ ogólna reguła nigdy nie obsługuje wyjątku w kodzie biblioteki (kod, który wymaga przechwytywania wyjątku może wskazywać na przykład projektu w wywoływanym kodzie).  W niektórych przypadkach może być konieczne przechwycenie wyjątku i zgłoszenie innego typu wyjątku w celu zapewnienia większej ilości danych.  W takim przypadku należy użyć zagnieżdżonych wyjątków, przechowując rzeczywistą przyczynę niepowodzenia niepowodzeń we właściwości <xref:System.Exception.InnerException%2A> nowego wyjątku.

#### <a name="code-analysis-rule"></a>Reguła analizy kodu

Przejrzyj wszystkie bloki catch w zarządzanym kodzie, który przechwytuje wszystkie obiekty lub przechwytuje wszystkie wyjątki.  W C#programie oznacza to Oflagowanie zarówno `catch` {}, jak i `catch(Exception)` {}.  Rozważ, aby typ wyjątku był bardzo specyficzny, lub sprawdź kod, aby upewnić się, że nie działa w sposób niewłaściwy, jeśli przechwytuje nieoczekiwany typ wyjątku.

### <a name="do-not-assume-a-managed-thread-is-a-win32-thread--it-is-a-fiber"></a>Nie przyjmij wątku zarządzanego jako wątku Win32 — jest to włókna

Korzystanie z lokalnego magazynu wątku zarządzanego działa, ale nie można użyć magazynu lokalnego wątku niezarządzanego lub założenia, że kod zostanie uruchomiony ponownie w bieżącym wątku systemu operacyjnego. Nie należy zmieniać ustawień, takich jak ustawienia regionalne wątku. Nie wywołuj `InitializeCriticalSection` ani `CreateMutex` za pośrednictwem wywołania platformy, ponieważ wymagają one wątku systemu operacyjnego, który przechodzi blokadę, również zamyka blokadę. Ponieważ nie będzie to miało znaczenia w przypadku korzystania z włókien, sekcje krytyczne Win32 i muteksy nie mogą być używane bezpośrednio w programie SQL.  Należy zauważyć, że zarządzana Klasa <xref:System.Threading.Mutex> nie obsługuje tych kwestii koligacji wątków.

Można bezpiecznie użyć większości stanu na zarządzanym obiekcie <xref:System.Threading.Thread>, w tym lokalnego magazynu wątku zarządzanego i kultury interfejsu użytkownika bieżącego wątku. Można również użyć <xref:System.ThreadStaticAttribute>, która powoduje, że wartość istniejącej zmiennej statycznej jest dostępna tylko w bieżącym wątku zarządzanym (jest to inny sposób na przeprowadzenie magazynu lokalnego Fiber w środowisku CLR). Ze względu na model programowania nie można zmienić bieżącej kultury wątku w przypadku uruchamiania w programie SQL Server.

#### <a name="code-analysis-rule"></a>Reguła analizy kodu

SQL Server działa w trybie Fiber; nie używaj magazynu lokalnego wątków. Unikaj wywołań wywoływanych przez platformę do `TlsAlloc`, `TlsFree`, `TlsGetValue`i `TlsSetValue.`

### <a name="let-sql-server-handle-impersonation"></a>Zezwól na SQL Server personifikacji

Ponieważ personifikacja działa na poziomie wątku, a SQL może działać w trybie Fiber, kod zarządzany nie powinien personifikować użytkowników i nie powinien wywoływać `RevertToSelf`.

#### <a name="code-analysis-rule"></a>Reguła analizy kodu

Zezwól na SQL Server personifikacji. Nie używaj `RevertToSelf`, `ImpersonateAnonymousToken`, `DdeImpersonateClient`, `ImpersonateDdeClientWindow`, `ImpersonateLoggedOnUser`, `ImpersonateNamedPipeClient`, `ImpersonateSelf`, `RpcImpersonateClient`, `RpcRevertToSelf`, `RpcRevertToSelfEx`lub `SetThreadToken`.

### <a name="do-not-call-threadsuspend"></a>Nie wywołuj wątku:: Suspend

Możliwość zawieszenia wątku może wydawać się prostą operacją, ale może to spowodować zakleszczenie.  Jeśli wątek przechowujący blokadę jest zawieszony przez drugi wątek, a następnie drugi wątek podejmuje tę samą blokadę, wystąpi zakleszczenie.  <xref:System.Threading.Thread.Suspend%2A> może kolidować z zabezpieczeniami, ładowaniem klas, usługami zdalnymi i odbiciem.

#### <a name="code-analysis-rule"></a>Reguła analizy kodu

Nie wywołuj <xref:System.Threading.Thread.Suspend%2A>. Rozważ użycie rzeczywistego elementu podstawowego synchronizacji, takiego jak <xref:System.Threading.Semaphore> lub <xref:System.Threading.ManualResetEvent>.

### <a name="protect-critical-operations-with-constrained-execution-regions-and-reliability-contracts"></a>Ochrona krytycznych operacji przy użyciu ograniczonych regionów wykonywania i kontraktów niezawodności

Podczas wykonywania złożonej operacji, która aktualizuje stan udostępniony lub który musi być deterministyczny w pełni powodzenie lub w pełni niepowodzeniem, należy się upewnić, że jest ona chroniona przez ograniczony region wykonywania (CER). Gwarantuje to, że kod jest uruchamiany w każdym przypadku, nawet Nagłe przerwanie wątku lub nagłe <xref:System.AppDomain> Unload.

CER to określony blok `try/finally` bezpośrednio poprzedzony wywołaniem <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>.

Wykonanie tej czynności powoduje, że kompilator just in Time przygotowuje cały kod w bloku finally przed uruchomieniem bloku `try`. Gwarantuje to, że kod w bloku finally jest zbudowany i będzie działać we wszystkich przypadkach. Nie jest to typowy element CER, aby miał pusty blok `try`. Używanie narzędzia CER chroni przed asynchronicznymi przerwami wątku i wyjątkami braku pamięci. Zapoznaj się <xref:System.Runtime.CompilerServices.RuntimeHelpers.ExecuteCodeWithGuaranteedCleanup%2A> z formularzem CER, który dodatkowo obsługuje przepełnienie stosu przez przekroczenie głębokiego kodu.

## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.ConstrainedExecution>
- [Atrybuty ochrony hosta i programowanie SQL Server](sql-server-programming-and-host-protection-attributes.md)
