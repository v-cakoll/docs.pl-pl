---
title: Zarządzana wątkowość — najlepsze rozwiązania
ms.date: 11/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f95fb3ccab7362021a7a195ea199a1370e003dd2
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46562375"
---
# <a name="managed-threading-best-practices"></a>Zarządzana wątkowość — najlepsze rozwiązania
Wielowątkowość wymaga starannego programowania. W przypadku większości zadań mogą zmniejszyć złożoność przez kolejkowanie żądania do wykonania, wątków z puli wątków. Ten temat dotyczy trudniejsze sytuacjach, takich jak koordynowanie pracy wielu wątków i obsługi wątki tego bloku.  
  
> [!NOTE]
> Począwszy od programu .NET Framework 4 w bibliotece równoległych zadań i PLINQ zapewniają interfejsy API, zmniejszyć niektóre złożoność i ryzyko programowanie wielowątkowe. Aby uzyskać więcej informacji, zobacz [programowania równoległego w .NET](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="deadlocks-and-race-conditions"></a>Zakleszczeń i sytuacje wyścigu  
 Wielowątkowość rozwiązuje problemy z przepływności i czasu odpowiedzi, ale w ten sposób wprowadza nowe problemy: zakleszczeń i sytuacje wyścigu.  
  
### <a name="deadlocks"></a>Zakleszczenia  
 Zakleszczenie występuje, gdy każda z dwoma wątkami próbuje zablokować zasobu, do którego innych został już zablokowany. Żadna wątku można wprowadzać żadnych dalszych postępów.  
  
 Wiele metod klas wątków zarządzanych zapewniają limity czasu, aby ułatwić wykrywanie zakleszczenia. Na przykład, poniższy kod próbuje uzyskać blokadę obiektu o nazwie `lockObject`. Jeśli blokada nie zostanie uzyskana w milisekundach 300 <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> zwraca `false`.  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a>Warunki wyścigu  
 Sytuacja wyścigu jest błąd, który występuje, gdy wynikiem programu zależy od określonego bloku kodu, którym dwa lub więcej wątków osiągnie najpierw. Uruchamianie programu wiele razy daje różne wyniki, a wynik dowolnym danym przebiegiem nie można przewidzieć.  
  
 Prosty przykład sytuacja wyścigu jest zwiększenie pola. Załóżmy, że klasa ma prywatnej **statyczne** pola (**Shared** w języku Visual Basic), jest zwiększana za każdym razem, gdy tworzone jest wystąpienie klasy, takie jak przy użyciu kodu `objCt++;` (C#) lub `objCt += 1` ( Visual Basic). Ta operacja wymaga ładowania wartość `objCt` do rejestru, zwiększenie wartości i zapisuje ją w `objCt`.  
  
 W aplikacji wielowątkowych wątek, który został załadowany i zwiększana wartość może być wywłaszczony przez inny wątek, który wykonuje wszystkie trzy kroki; Po pierwszym wątkiem wznawia wykonanie i przechowuje wartość, zastępuje `objCt` nie biorąc pod uwagę fakt, że wartość została zmieniona w międzyczasie.  
  
 Sytuacja wyścigu określonego unika się łatwo za pomocą metody <xref:System.Threading.Interlocked> klasy, takie jak <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>. Aby przeczytać o innych technik do synchronizowania danych między wieloma wątkami, zobacz [synchronizowanie danych dla wielowątkowość](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).  
  
 Warunki wyścigu może również wystąpić podczas synchronizowania działania wielu wątków. Zawsze, gdy pisania choćby wiersza kodu, należy rozważyć, co może się zdarzyć, jeśli wątek były przerywane, przed wykonaniem wiersza (lub przed każdą instrukcji poszczególnych maszyn, które składają się na wiersz), a inny wątek podbili go.  
  
## <a name="number-of-processors"></a>Liczba procesorów  
 Większość komputerów teraz mieć wiele procesorów (nazywane również rdzenie) nawet małych urządzeniach, takich jak tablety i telefony. Jeśli wiesz, że tworzysz oprogramowanie, które będzie również uruchomić na komputerach z jednym procesorem, należy zwrócić uwagę oznacza wielowątkowości rozwiązuje problemy różnych komputerach jednym procesorem i wieloprocesorowych.  
  
### <a name="multiprocessor-computers"></a>Komputerów wieloprocesorowych  
 Wielowątkowość zapewnia większą przepływność. Dziesięć procesory mogą wykonywać dziesięć razy pracę one, ale tylko jeśli praca odbywa się tak, aby wszystkie dziesięć mogą działać jednocześnie; wątki zapewniają prosty sposób podzielić pracę i wykorzystać dodatkowej mocy obliczeniowej. Jeśli używasz wielowątkowości w komputerach wieloprocesorowych:  
  
-   Liczba wątków, które mogą być wykonywane jednocześnie jest ograniczona przez liczbę procesorów.  
  
-   Wątku w tle jest wykonywany tylko wtedy, gdy jest to liczba wątków pierwszego planu wykonania jest mniejszy niż liczba procesorów.  
  
-   Gdy wywołujesz <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> metody na wątek, wątek może lub nie może uruchomić wykonywanie natychmiast, w zależności od liczby procesorów i liczbę wątków oczekujących na wykonanie.  
  
-   Warunki wyścigu może wystąpić, nie tylko z powodu wątki są zastępowane nieoczekiwanie zamknięty, ale ponieważ dwa wątki, wykonując na różnych procesorach może racing do osiągnięcia tego samego bloku kodu.  
  
### <a name="single-processor-computers"></a>Komputery z jednym procesorem  
 Wielowątkowość zapewnia większą elastyczność do komputera użytkownika i korzysta z czasu bezczynności dla zadań w tle. Jeśli używasz wielowątkowość na komputerze jednoprocesorowym:  
  
-   Tylko jeden wątek działa w każdej chwili.  
  
-   Wątku w tle jest wykonywany tylko wtedy, gdy jest bezczynny wątek główny użytkownik. Wątek pierwszego planu, który wykonuje stale starves wątków w tle czasu procesora.  
  
-   Gdy wywołujesz <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> metody w wątku, że wątek nie rozpocznie się wykonywanie aż do bieżącego wątku daje lub jest przerywane przez system operacyjny.  
  
-   Sytuacje wyścigu zazwyczaj wystąpić, ponieważ programistę nie jest przewidywane fakt, że wątek może przerywane chwili niewygodna czasami co inny wątek nawiązać blokiem kodu.  
  
## <a name="static-members-and-static-constructors"></a>Statyczne elementy członkowskie i konstruktorów statycznych  
 Klasa nie został zainicjowany aż do jej konstruktora klasy (`static` konstruktora w języku C# `Shared Sub New` w języku Visual Basic) zakończył działanie. Aby uniemożliwić wykonywanie kodu na typie, który nie został zainicjowany, środowisko uruchomieniowe języka wspólnego blokuje wszystkie połączenia z innych wątków do `static` elementów członkowskich klasy (`Shared` elementów członkowskich w języku Visual Basic) do momentu zakończenia uruchamiania konstruktora klasy.  
  
 Na przykład, jeśli Konstruktor klasy rozpoczynają nowy wątek, a następnie wywołuje procedury wątku `static` składowej klasy nowe bloki wątku do chwili zakończenia konstruktora klasy.  
  
 Dotyczy to dowolnego typu, który może mieć `static` konstruktora.  
  
## <a name="general-recommendations"></a>Ogólne zalecenia  
 Korzystając z wielu wątków, należy wziąć pod uwagę następujące wytyczne:  
  
-   Nie używaj <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> zakończyć inne wątki. Wywoływanie **przerwać** na inny wątek jest podobnie zostanie zgłoszony wyjątek w że wątku, nie wiedząc o tym, co punkt wątek osiągnęła w zakresie przetwarzania.  
  
-   Nie używaj <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> do synchronizowania działania wielu wątków. Należy używać <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, i <xref:System.Threading.Monitor>.  
  
-   Nie kontrolować wykonywanie wątków roboczych programu głównego (na przykład przy użyciu zdarzeń). Zamiast tego można zaprojektować program, tak, aby wątków roboczych jest odpowiedzialny za na zakończenie pracy jest dostępna, jej wykonanie i powiadamiania innych części programu, po zakończeniu. Jeśli nie blokują wątki procesu roboczego, rozważ użycie wątków z puli wątków. <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType> jest przydatne w sytuacjach, w którym pracownik wątki bloku.  
  
-   Nie należy używać typów jako obiekty blokady. Oznacza to, takich jak Unikaj kodu `lock(typeof(X))` w języku C# lub `SyncLock(GetType(X))` w Visual Basic lub użytkowania <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> z <xref:System.Type> obiektów. Dla danego typu, jest tylko jedno wystąpienie <xref:System.Type?displayProperty=nameWithType> dla domeny aplikacji. W przypadku publicznego typu, który stosuje blokadę na kod inny niż własny może blokad, co prowadzi do zakleszczenia. Aby uzyskać dodatkowe problemy, zobacz [najlepsze rozwiązania dotyczące niezawodności](../../../docs/framework/performance/reliability-best-practices.md).  
  
-   Należy zachować ostrożność podczas blokowania w wystąpieniach, na przykład `lock(this)` w języku C# lub `SyncLock(Me)` w języku Visual Basic. Jeśli inny kod w aplikacji, zewnętrzne w stosunku do typu, przyjmuje blokadę na obiekcie, może wystąpić zakleszczenia.  
  
-   Upewnij się, że wątku, która została wprowadzona przez monitor zawsze pozostawia tego monitora, nawet jeśli wystąpi wyjątek, gdy wątek jest w monitorze. C# [blokady](~/docs/csharp/language-reference/keywords/lock-statement.md) instrukcji i Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) instrukcji zapewnia to zachowanie automatycznie, wykorzystujące **na koniec** bloku, aby upewnić się, że <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> jest wywoływana. Jeśli nie można zapewnić, że **zakończenia** zostanie wywołana, rozważ zmianę projektu do użycia **Mutex**. Mutex automatycznie jest zwalniany, gdy kończy się wątek, który aktualnie jest właścicielem.  
  
-   Użyj wielu wątków dla zadań, które wymagają różnych zasobów i należy unikać przypisywania wiele wątków do pojedynczego zasobu. Na przykład wszystkie zadania dotyczące operacji We/Wy korzyści płynące z konieczności jego własnym wątku, ponieważ wątek będzie blokować podczas operacji We/Wy i Zezwalaj na tym samym innych wątków do wykonania. Dane wejściowe użytkownika jest inny zasób, który korzysta z dedykowanego wątku. Na komputerze jednoprocesorowym zadań, która obejmuje intensywnie korzystających z obliczeń będą współistnieć z danych wejściowych użytkownika i zadania, które obejmują operacje We/Wy, ale wiele zadań intensywnie korzystających z obliczeń zmagać się ze sobą.  
  
-   Należy wziąć pod uwagę przy użyciu metod <xref:System.Threading.Interlocked> klasy dla zmiany stanu prosty, zamiast `lock` — instrukcja (`SyncLock` w języku Visual Basic). `lock` Instrukcja jest dobrym narzędziem ogólnego przeznaczenia, ale <xref:System.Threading.Interlocked> klasy zapewnia lepszą wydajność dla aktualizacji, które muszą być niepodzielna. Wewnętrznie wykonuje prefiks pojedynczego blokadę, jeśli nie występuje rywalizacja. W przeglądach kodu Obserwuj kod, jak pokazano w poniższych przykładach. W pierwszym przykładzie jest zwiększany zmiennej stanu:  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)   
    {  
        myField++;  
    }  
    ```  
  
     Możesz poprawić wydajność przy użyciu <xref:System.Threading.Interlocked.Increment%2A> zamiast metody `lock` instrukcji, w następujący sposób:  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  W .NET Framework w wersji 2.0 <xref:System.Threading.Interlocked.Add%2A> metoda zapewnia atomic aktualizacje w przyrostach większy niż 1.  
  
     W drugim przykładzie zmienna typu odwołania jest aktualizowany tylko wtedy, gdy jest odwołanie o wartości null (`Nothing` w języku Visual Basic).  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            if (x == null)  
            {  
                x = y;  
            }  
        }  
    }  
    ```  
  
     Można poprawić wydajność przy użyciu <xref:System.Threading.Interlocked.CompareExchange%2A> metody zamiast tego, w następujący sposób:  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  W .NET Framework w wersji 2.0 <xref:System.Threading.Interlocked.CompareExchange%2A> metoda ma przeciążenie ogólne, który może służyć do zastąpienia bezpieczny dowolnego typu referencyjnego.  
  
## <a name="recommendations-for-class-libraries"></a>Zalecenia dotyczące bibliotek klas  
 Należy wziąć pod uwagę następujące wskazówki podczas projektowania bibliotek klas dla wielowątkowości:  
  
-   Uniknięcia synchronizacji, jeśli jest to możliwe. Jest to szczególnie istotne dla intensywnie używanych kodu. Na przykład algorytm może dostosować tolerować wyścigu, a nie jej wyeliminowania. Synchronizacja niepotrzebne zmniejsza wydajność i tworzy możliwości zakleszczeń i sytuacje wyścigu.  
  
-   Przechowuj dane statyczne (`Shared` w języku Visual Basic) zapewnia bezpieczeństwa wątkowego domyślnie.  
  
-   Nie należy wprowadzać wątku danych wystąpienia bezpieczne domyślnie. Dodawanie blokady, aby utworzyć kod wątkowo zmniejsza wydajność, zwiększa Rywalizacja o blokady i tworzy możliwości zakleszczenia wystąpić. W typowych modeli aplikacji tylko jeden wątek jednocześnie wykonuje kod użytkownika, co minimalizuje potrzebę bezpieczeństwo wątkowe. Z tego powodu biblioteki klas .NET Framework nie są wątkowo bezpieczne domyślnie.  
  
-   Należy unikać, zapewniając metody statyczne, które zmienia stan statyczne. W typowych scenariuszach serwera stanu statycznego jest współużytkowane przez wiele żądań, co oznacza, że wiele wątków można wykonać ten kod w tym samym czasie. Spowoduje to otwarcie możliwości wątkowości usterek. Należy wziąć pod uwagę przy użyciu wzorca projektowego, który hermetyzuje danych do wystąpienia, które nie są współużytkowane przez wiele żądań. Ponadto jeśli dane statyczne są synchronizowane, wywołań między metody statyczne, które zmienia stan może spowodować zakleszczenia lub nadmiarowe synchronizacji negatywnego wpływu na wydajność.  
  
## <a name="see-also"></a>Zobacz także

- [Wątkowość](../../../docs/standard/threading/index.md)  
- [Wątki i wątkowość](../../../docs/standard/threading/threads-and-threading.md)
