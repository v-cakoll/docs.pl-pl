---
title: "Zarządzana wątkowość — najlepsze rozwiązania"
ms.custom: 
ms.date: 11/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e396bb1f6a710e49e311ca1526a7aae9bca7bf90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="managed-threading-best-practices"></a>Zarządzana wątkowość — najlepsze rozwiązania
Wielowątkowość wymaga zachować ostrożność podczas programowania. W przypadku większości zadań można zmniejszyć złożoność kolejkowania wiadomości żądania do wykonania przez wątków z puli wątków. Ten temat dotyczy sytuacji trudniej, takich jak koordynowanie pracy wiele wątków, lub obsługa wątki tego bloku.  
  
> [!NOTE]
> Począwszy od programu .NET Framework 4, w bibliotece równoległych zadań i PLINQ Podaj interfejsów API, które zmniejszyć niektóre złożoność i ryzyko programów wielowątkowych. Aby uzyskać więcej informacji, zobacz [Programowanie równoległe w .NET](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="deadlocks-and-race-conditions"></a>Zakleszczenie i sytuacja wyścigu  
 Wielowątkowość rozwiązuje problemy z przepływność i elastyczność, jednak w ten sposób wprowadza nowe problemy: zakleszczenie i sytuacja wyścigu.  
  
### <a name="deadlocks"></a>Zakleszczenie  
 Zakleszczenie występuje, gdy każdy z dwoma wątkami próbuje zablokować zasobu, do którego innych został już zablokowany. Wątek nie może poczyniła żadnego postępu dalsze.  
  
 Wiele metod klasy wątkowości zarządzane Podaj limity czasu, co ułatwia wykrywanie zakleszczenia. Na przykład następujący kod próbuje uzyskać blokady obiektu o nazwie `lockObject`. Jeżeli nie uzyskano blokady w milisekundach 300 <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> zwraca `false`.  
  
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
 Sytuacja wyścigu jest usterkę, która występuje, gdy wynik programu zależy od tego, który dwa lub więcej wątków najpierw osiągnie bloku kodu. Program działa wiele razy daje różne wyniki, a nie można przewidzieć wynik dowolnym danym uruchomieniu.  
  
 Prosty przykład sytuacja wyścigu jest zwiększenie pola. Załóżmy, że klasa ma prywatnej **statycznych** pola (**Shared** w języku Visual Basic) który jest zwiększany za każdym razem, gdy tworzone jest wystąpienie klasy, takich jak przy użyciu kodu `objCt++;` (C#) lub `objCt += 1` () Visual Basic). Ta operacja wymaga ładowania wartość `objCt` w rejestrze, zwiększając wartość, a następnie zapisanie jej w `objCt`.  
  
 W aplikacji wielowątkowych wątku, który został załadowany i zwiększana wartość może być wywłaszczony przez inny wątek, który wykonuje wszystkie trzy kroki; Po pierwszym wątkiem wznawia wykonywania i przechowuje wartość, zastępuje on `objCt` bez biorąc pod uwagę fakt, że wartość została zmieniona w tymczasowych.  
  
 Łatwo uniknąć sytuacja wyścigu określonego za pomocą metody <xref:System.Threading.Interlocked> klas, takich jak <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>. Aby uzyskać informacje dotyczące innych technik synchronizowania danych między wiele wątków, zobacz [synchronizowanie danych Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).  
  
 Warunki wyścigu może również wystąpić podczas synchronizowania działania wiele wątków. Zawsze, gdy zapisywania wiersza kodu, należy rozważyć co może się zdarzyć, jeśli wątek zostały wywłaszczone przed wykonaniem wiersza (lub przed każdą instrukcji poszczególnych maszyn, które składają się na wiersz), a inny wątek podbili go.  
  
## <a name="number-of-processors"></a>Liczba procesorów  
 Większość komputerów już wielu procesorów (nazywanych również rdzenie) nawet małych urządzeń, takich jak tablety i telefony. Jeśli wiesz, że projektujesz oprogramowania, które zostanie też uruchomiony na komputerach z jednym procesorem, należy zwrócić uwagę że wielowątkowość rozwiązuje różne problemy dla komputerów z jednym procesorem i komputerach wieloprocesorowych.  
  
### <a name="multiprocessor-computers"></a>Komputerach wieloprocesorowych  
 Wielowątkowość zapewnia większą przepływność. Dziesięć procesorów możliwość dziesięciokrotnie pracy jednego, ale tylko jeśli praca odbywa się tak, aby wszystkie dziesięciu mogą działać jednocześnie; wątki umożliwiają łatwe do dzielenia pracy i wykorzystać dodatkowej mocy obliczeniowej. Jeśli używasz wielowątkowości w komputerach wieloprocesorowych:  
  
-   Liczba wątków, które mogą być wykonywane jednocześnie jest ograniczona przez liczbę procesorów.  
  
-   Wątku w tle jest wykonywana tylko wtedy, gdy liczba wątków pierwszego planu wykonania jest mniejszy niż liczba procesorów.  
  
-   Podczas wywoływania <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> metody w wątku, wątek może lub nie może rozpocząć wykonywania, w zależności od liczby procesorów i liczbę wątków oczekujących na wykonanie.  
  
-   Warunki wyścigu może być spowodowany nie tylko wątki są zastępowane nieoczekiwanie, ale ponieważ dwa wątki wykonywanych na różnych procesorów może racing do tego samego bloku kodu.  
  
### <a name="single-processor-computers"></a>Komputery z jednym procesorem  
 Wielowątkowość zapewnia większą elastyczność użytkowników komputera, a używa czas bezczynności dla zadania w tle. Jeśli używasz wielowątkowość na komputerze z jednym procesorem:  
  
-   Tylko jeden wątek działa w każdej chwili.  
  
-   Wątku w tle jest wykonywana tylko wtedy, gdy jest bezczynny wątek użytkownika głównego. Wątek pierwszego planu, który wykonuje stale starves wątki w tle czasu procesora.  
  
-   Podczas wywoływania <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> metody w wątku, że wątek nie rozpocznie się wykonywanie do bieżącego wątku daje lub są zastępowane przez system operacyjny.  
  
-   Warunki wyścigu zwykle występuje, ponieważ programistę nie jest przewidywane fakt, że wątku może być wywłaszczony chwili nieodpowiednich czasami stosowanie inny wątek nawiązać blok kodu.  
  
## <a name="static-members-and-static-constructors"></a>Statyczne elementy członkowskie i konstruktorów statycznych  
 Nie zainicjowano klasy do jego konstruktora klasy (`static` konstruktora w języku C# `Shared Sub New` w języku Visual Basic) zakończył działanie. Aby zapobiec wykonywanie kodu na typ, który nie został zainicjowany, środowisko uruchomieniowe języka wspólnego blokuje wywołania z innych wątków `static` elementy członkowskie klasy (`Shared` elementów członkowskich w języku Visual Basic) do momentu konstruktora klasy zakończył działanie.  
  
 Na przykład, jeśli konstruktora klasy rozpoczyna się nowego wątku i wywołuje procedurę wątku `static` elementu członkowskiego klasy nowych bloków wątku do momentu ukończenia konstruktora klasy.  
  
 Dotyczy to dowolnego typu, który może mieć `static` konstruktora.  
  
## <a name="general-recommendations"></a>Ogólne zalecenia  
 Korzystając z wielu wątków, należy wziąć pod uwagę następujące wytyczne:  
  
-   Nie używaj <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> zakończyć inne wątki. Wywoływanie **przerwać** w innym wątku jest podobnie Zgłaszanie wyjątku wątku, bez wiedzy o co punktu wątek ma osiągnięcie w jego przetwarzanie.  
  
-   Nie używaj <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> do synchronizowania działania wiele wątków. Należy używać <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, i <xref:System.Threading.Monitor>.  
  
-   Nie mają wpływu na wykonywanie wątków roboczych z programu głównego (na przykład za pomocą zdarzeń,). Zamiast tego projektu programu tak, aby wątków roboczych są odpowiedzialne za czekając na zakończenie pracy jest dostępna, jej wykonanie i powiadamiania innych części program po zakończeniu. Jeśli Twoje wątków roboczych nie blokują, rozważ użycie wątków z puli wątków. <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType>jest przydatne w sytuacjach, gdy proces roboczy wątki bloku.  
  
-   Nie można używać typów jako obiekty blokady. Oznacza to, takich jak uniknąć kodu `lock(typeof(X))` w języku C# lub `SyncLock(GetType(X))` w języku Visual Basic lub korzystanie z <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> z <xref:System.Type> obiektów. Dla danego typu, jest tylko jedno wystąpienie <xref:System.Type?displayProperty=nameWithType> na domeny aplikacji. Jeśli wykonywane blokady na typ jest publiczny, kodu innego niż własny może zająć blokad, co prowadzi do zakleszczenia. Aby uzyskać dodatkowe problemy, zobacz [najlepsze rozwiązania dotyczące niezawodności](../../../docs/framework/performance/reliability-best-practices.md).  
  
-   Należy zachować ostrożność podczas blokowania w wystąpieniach, na przykład `lock(this)` w języku C# lub `SyncLock(Me)` w języku Visual Basic. Jeśli inny kod w aplikacji zewnętrznych do typu, przyjmuje blokady na obiekcie, może wystąpić zakleszczenia.  
  
-   Upewnij się, że wątek, który wprowadził monitor zawsze pozostawia monitora, nawet jeśli wystąpi wyjątek, gdy wątek znajduje się w monitorze. C# [blokady](~/docs/csharp/language-reference/keywords/lock-statement.md) instrukcji i Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) instrukcji Podaj to zachowanie automatycznie, wykorzystujących **koniec** bloku, aby upewnić się, że <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> jest wywołuje się. Jeśli nie można zapewnić **zakończenia** zostanie wywołana, należy rozważyć zmianę projektu do użycia **obiektu Mutex**. Obiektu mutex jest zwalniany automatycznie, gdy zakończenie wątku, który obecnie jest jego właścicielem.  
  
-   Użyj wielu wątków zadań, które wymagają różnych zasobów i przypisywać wiele wątków do pojedynczego zasobu. Na przykład wszystkie zadania dotyczące operacji We/Wy korzysta z o własnym wątku, ponieważ wątek będzie zablokować podczas operacji We/Wy i w związku z tym zezwolić na inne wątki do wykonania. Dane wejściowe użytkownika jest inny zasób, który korzysta z dedykowanym wątku. Na komputerze z jednym procesorem zadań, która obejmuje obliczeń obciążających współdziała z danych wejściowych użytkownika i zadaniach dotyczących operacji We/Wy, ale wiele zadań intensywnie obliczeń będą konkurować ze sobą.  
  
-   Należy rozważyć użycie metody <xref:System.Threading.Interlocked> klasy zmian stanu prostego, zamiast `lock` instrukcji (`SyncLock` w języku Visual Basic). `lock` Instrukcja jest dobrym narzędzie ogólnego przeznaczenia, ale <xref:System.Threading.Interlocked> klasy zapewnia lepszą wydajność aktualizacji, które muszą być atomic. Wewnętrznie wykonuje on prefiks jedną blokadą jeśli ma rywalizacji nie istnieje. W przeglądów kodu Obejrzyj dla kodu, takie jak przedstawionych w poniższych przykładach. W pierwszym przykładzie jest zwiększany zmiennej stanu:  
  
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
  
     Wydajność można poprawić za pomocą <xref:System.Threading.Interlocked.Increment%2A> zamiast metody `lock` instrukcji w następujący sposób:  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  W programie .NET Framework w wersji 2.0 <xref:System.Threading.Interlocked.Add%2A> metoda zapewnia atomic aktualizacje w przyrostach większy niż 1.  
  
     W drugim przykładzie zmienna typu odniesienia jest aktualizowany tylko wtedy, gdy jest odwołanie o wartości null (`Nothing` w języku Visual Basic).  
  
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
  
     Można poprawić wydajność przy użyciu <xref:System.Threading.Interlocked.CompareExchange%2A> metody zamiast tego w następujący sposób:  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  W programie .NET Framework w wersji 2.0 <xref:System.Threading.Interlocked.CompareExchange%2A> metoda ma rodzajowy przeciążenia, które umożliwia bezpieczne zastąpienie dowolnego typu referencyjnego.  
  
## <a name="recommendations-for-class-libraries"></a>Zalecenia dotyczące biblioteki klas  
 Należy wziąć pod uwagę poniższe wskazówki podczas projektowania biblioteki klas dla wielowątkowości:  
  
-   Uniknąć konieczności synchronizacji, jeśli to możliwe. Jest to szczególnie istotne dla kodu intensywnie używane. Algorytm może na przykład dostosowana do tolerować wyścigu, a nie jej wyeliminowania. Niepotrzebne synchronizacji spadku wydajności i tworzy możliwości zakleszczenie i sytuacja wyścigu.  
  
-   Wprowadź dane statyczne (`Shared` w języku Visual Basic) wielowątkowość domyślnie.  
  
-   Nie należy wprowadzać wątku danych wystąpienia bezpieczne domyślnie. Dodawanie blokad, aby utworzyć kod wątkowo spadku wydajności, zwiększa rywalizacji blokad i tworzy możliwość Zakleszczenie występuje. Wspólne modeli aplikacji tylko jeden wątek jednocześnie wykonuje kod użytkownika, co minimalizuje konieczność bezpieczeństwa wątków. Z tego powodu bibliotek klas .NET Framework nie są wątkowo bezpieczne domyślnie.  
  
-   Unikaj udostępnia metody statyczne, które zmienia stan statycznych. W typowych scenariuszach serwera stanu statycznego jest współużytkowane przez wiele żądań, co oznacza, że wiele wątków może zostać uruchomiony ten kod w tym samym czasie. Spowoduje to otwarcie się możliwość wątkowość usterki. Należy rozważyć użycie wzorzec projektowania, który hermetyzuje danych do wystąpienia, które nie są współużytkowane przez wiele żądań. Ponadto jeśli dane statyczne są synchronizowane, wywołań między metod statycznych, które zmiany stanu może spowodować zakleszczenie lub nadmiarowe synchronizacji, negatywnego wpływu na wydajność.  
  
## <a name="see-also"></a>Zobacz też  
 [Wątkowość](../../../docs/standard/threading/index.md)  
 [Wątki i wątkowość](../../../docs/standard/threading/threads-and-threading.md)
