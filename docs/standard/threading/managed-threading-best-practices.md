---
title: Zarządzana wątkowość — najlepsze rozwiązania
ms.date: 10/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
ms.openlocfilehash: a76cc40f308ac2f636a650cd4a17da0e94e23a34
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160264"
---
# <a name="managed-threading-best-practices"></a>Najlepsze rozwiązania dotyczące wątków zarządzanych
Wielowątkowość wymaga starannego programowania. W przypadku większości zadań można zmniejszyć złożoność, kolejkując żądania do wykonania przez wątki puli wątków. Ten temat dotyczy trudniejszych sytuacji, takich jak koordynowanie pracy wielu wątków lub obsługa wątków, które blokują.  
  
> [!NOTE]
> Począwszy od .NET Framework 4, biblioteka równoległa zadań i PLINQ zapewniają interfejsy API, które zmniejszają złożoność i ryzyko programowania wielowątkowego. Aby uzyskać więcej informacji, zobacz [Programowanie równoległe w programie .NET](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="deadlocks-and-race-conditions"></a>Zakleszczenia i warunki wyścigu  
 Wielowątkowość rozwiązuje problemy z przepustowością i reakcją, ale w ten sposób wprowadza nowe problemy: zakleszczenia i warunki wyścigu.  
  
### <a name="deadlocks"></a>Zakleszczenia  
 Zakleszczenie występuje, gdy każdy z dwóch wątków próbuje zablokować zasób inny już zablokowany. Żaden wątek nie może poczynić dalszych postępów.  
  
 Wiele metod zarządzanych klas wątków zapewniają uchybienia czasu, aby ułatwić wykrywanie zakleszczeń. Na przykład poniższy kod próbuje uzyskać blokadę `lockObject`na obiekcie o nazwie . Jeśli blokada nie zostanie uzyskana w <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> ciągu `false`300 milisekund, zwraca wartość .  
  
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
 Stan wyścigu jest błąd, który występuje, gdy wynik programu zależy od tego, który z dwóch lub więcej wątków osiągnie określonego bloku kodu pierwszy. Uruchamianie programu wiele razy daje różne wyniki, a wynik danego przebiegu nie może być przewidywany.  
  
 Prostym przykładem stanu wyścigu jest zwiększanie pola. Załóżmy, że klasa ma prywatne pole **statyczne** **(Udostępnione** w języku Visual Basic), które jest zwiększane za każdym razem, gdy tworzone jest wystąpienie klasy, przy użyciu kodu, takiego jak `objCt++;` (C#) lub `objCt += 1` (Visual Basic). Ta operacja wymaga załadowania wartości z `objCt` do rejestru, zwiększania wartości i `objCt`przechowywania jej w pliku .  
  
 W aplikacji wielowątkowej wątku wątku, który został załadowany i zwiększa wartość może być wywłaszczony przez inny wątek, który wykonuje wszystkie trzy kroki; gdy pierwszy wątek wznawia wykonywanie i `objCt` przechowuje jego wartość, zastępuje bez uwzględnienia faktu, że wartość została zmieniona w międzyczasie.  
  
 Ten szczególny stan wyścigu można łatwo uniknąć <xref:System.Threading.Interlocked> za pomocą <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>metod klasy, takich jak . Aby przeczytać o innych technikach synchronizowania danych między wieloma wątkami, zobacz [Synchronizowanie danych dla wielowątkowości](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).  
  
 Warunki wyścigu mogą również wystąpić podczas synchronizowania działań wielu wątków. Za każdym razem, gdy piszesz wiersz kodu, należy wziąć pod uwagę, co może się zdarzyć, jeśli wątek zostały wywłaszczone przed wykonaniem wiersza (lub przed którymkolwiek z instrukcji poszczególnych maszyn, które tworzą wiersz), a inny wątek wyprzedził go.  
  
## <a name="static-members-and-static-constructors"></a>Statyczne elementy członkowskie i konstruktory statyczne  
 Klasa nie jest inicjowane, dopóki`static` jego konstruktor `Shared Sub New` klasy (konstruktor w języku C#, w języku Visual Basic) został zakończony uruchomiony. Aby zapobiec wykonywaniu kodu na typ, który nie jest inicjowany, czas wykonywania języka wspólnego blokuje wszystkie wywołania z innych wątków do `static` elementów członkowskich klasy (elementy`Shared` członkowskie w języku Visual Basic), dopóki konstruktor klasy nie zakończy się uruchomiony.  
  
 Na przykład jeśli konstruktor klasy uruchamia nowy wątek, `static` a procedura wątku wywołuje element członkowski klasy, nowe bloki wątku, dopóki konstruktor klasy nie zostanie ukończony.  
  
 Dotyczy to dowolnego typu, który `static` może mieć konstruktora.  

## <a name="number-of-processors"></a>Liczba przetwórców

To, czy w systemie jest dostępnych wiele procesorów, czy tylko jeden procesor, może mieć wpływ na architekturę wielowątkową. Aby uzyskać więcej informacji, zobacz [Liczba procesorów](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).

Użyj <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> właściwości, aby określić liczbę procesorów dostępnych w czasie wykonywania.
  
## <a name="general-recommendations"></a>Zalecenia ogólne  
 Podczas korzystania z wielu wątków należy wziąć pod uwagę następujące wskazówki:  
  
- Nie należy <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> używać do zakończenia innych wątków. Wywołanie **Abort** w innym wątku jest podobne do zgłaszania wyjątku w tym wątku, nie wiedząc, jaki punkt, który wątek osiągnął w jego przetwarzania.  
  
- Nie należy <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> używać <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> i synchronizować działania wielu wątków. Czy <xref:System.Threading.Mutex>używać <xref:System.Threading.ManualResetEvent> <xref:System.Threading.AutoResetEvent>, <xref:System.Threading.Monitor>, i .  
  
- Nie należy kontrolować wykonywanie wątków roboczych z głównego programu (przy użyciu zdarzeń, na przykład). Zamiast tego zaprojektuj program tak, aby wątki robocze były odpowiedzialne za oczekiwanie, aż praca będzie dostępna, wykonanie go i powiadomienie innych części programu po zakończeniu. Jeśli wątki robocze nie blokują, należy rozważyć użycie wątków puli wątków. <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType>jest przydatne w sytuacjach, gdy blok wątków roboczych.  
  
- Nie należy używać typów jako obiektów blokady. Oznacza to, że `lock(typeof(X))` należy unikać `SyncLock(GetType(X))` kodu, takich jak w <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Type> języku C# lub w języku Visual Basic lub użycia z obiektami. Dla danego typu istnieje tylko jedno <xref:System.Type?displayProperty=nameWithType> wystąpienie na domenę aplikacji. Jeśli typ wziąć blokady jest publiczny, kod inny niż własne może podjąć blokady na nim, co prowadzi do zakleszczenia. Aby uzyskać dodatkowe problemy, zobacz [Najważniejsze wskazówki dotyczące niezawodności](../../../docs/framework/performance/reliability-best-practices.md).  
  
- Należy zachować ostrożność podczas blokowania `lock(this)` wystąpień, `SyncLock(Me)` na przykład w języku C# lub w języku Visual Basic. Jeśli inny kod w aplikacji, zewnętrznego do typu, ma blokady na obiekcie, może wystąpić zakleszczenia.  
  
- Upewnij się, że wątek, który wszedł monitor zawsze pozostawia tego monitora, nawet jeśli wystąpi wyjątek, gdy wątek znajduje się na monitorze. C# [lock](../../csharp/language-reference/keywords/lock-statement.md) instrukcji i Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) instrukcji zapewniają to **finally** zachowanie automatycznie, <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> wykorzystując finally bloku, aby upewnić się, że jest wywoływana. Jeśli nie możesz upewnić się, że **exit** zostanie wywołany, rozważ zmianę projektu na **mutex**. Mutex jest automatycznie zwalniany, gdy wątek, który jest obecnie właścicielem kończy.  
  
- Należy używać wielu wątków dla zadań, które wymagają różnych zasobów i uniknąć przypisywania wielu wątków do jednego zasobu. Na przykład każde zadanie obejmujące we/wy korzyści z posiadania własnego wątku, ponieważ ten wątek będzie blokować podczas operacji we/wy, a tym samym zezwolić na wykonywanie innych wątków. Dane wejściowe użytkownika to inny zasób, który korzysta z dedykowanego wątku. Na komputerze z jednym procesorem zadanie, które obejmuje intensywne obliczenia współistnieje z danymi wejściowymi użytkownika i zadaniami, które obejmują we/wy, ale wiele zadań intensywnie korzystających z obliczeń walczy ze sobą.  
  
- Należy rozważyć użycie <xref:System.Threading.Interlocked> metod klasy dla prostych zmian `lock` stanu, zamiast używać instrukcji (w`SyncLock` języku Visual Basic). Instrukcja `lock` jest dobrym narzędziem ogólnego <xref:System.Threading.Interlocked> przeznaczenia, ale klasa zapewnia lepszą wydajność dla aktualizacji, które muszą być atomowej. Wewnętrznie wykonuje prefiks pojedynczej blokady, jeśli nie ma żadnych rywalizacji. W przeglądzie kodu uważaj na kod podobny do tego, który został pokazany w poniższych przykładach. W pierwszym przykładzie zmienna stanu jest zwiększana:  
  
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
  
     Można zwiększyć wydajność <xref:System.Threading.Interlocked.Increment%2A> przy użyciu `lock` metody zamiast instrukcji, w następujący sposób:  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > W .NET Framework 2.0 i <xref:System.Threading.Interlocked.Add%2A> nowszych użyj metody przyrostów niepodzielnych większych niż 1.  
  
     W drugim przykładzie zmienna typu odwołania jest aktualizowana tylko`Nothing` wtedy, gdy jest to odwołanie zerowe (w języku Visual Basic).  
  
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
            x ??= y;
        }  
    }  
    ```  
  
     Wydajność można poprawić za <xref:System.Threading.Interlocked.CompareExchange%2A> pomocą metody zamiast, w następujący sposób:  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > Począwszy od .NET Framework <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> 2.0 przeciążenie metody zapewnia alternatywę dla typów odwołań.
  
## <a name="recommendations-for-class-libraries"></a>Zalecenia dotyczące bibliotek klas  
 Podczas projektowania bibliotek klas do wielowątkowości należy wziąć pod uwagę następujące wskazówki:  
  
- Unikaj konieczności synchronizacji, jeśli to możliwe. Jest to szczególnie ważne dla kodu intensywnie używane. Na przykład algorytm może być dostosowane do tolerowania stanu wyścigu, a nie go wyeliminować. Niepotrzebna synchronizacja zmniejsza wydajność i stwarza możliwość zakleszczenia i warunków wyścigu.  
  
- Ustaw domyślnie`Shared` wątek danych statycznych (w języku Visual Basic).  
  
- Nie należy domyślnie zabezpieczać wątku danych wystąpienia. Dodawanie blokad do tworzenia kodu bezpiecznego dla wątków zmniejsza wydajność, zwiększa rywalizację blokad i tworzy możliwość wystąpienia zakleszczenia. W typowych modelach aplikacji tylko jeden wątek naraz wykonuje kod użytkownika, co minimalizuje potrzebę bezpieczeństwa wątków. Z tego powodu biblioteki klas .NET Framework nie są domyślnie bezpieczne dla wątków.  
  
- Należy unikać podawania metod statycznych, które zmieniają stan statyczny. W typowych scenariuszach serwera stan statyczny jest współużytkowany przez żądania, co oznacza, że wiele wątków może wykonać ten kod w tym samym czasie. Otwiera to możliwość wątków błędów. Należy wziąć pod uwagę przy użyciu wzorca projektu, który hermetyzuje dane w wystąpieniach, które nie są współużytkowane przez żądania. Ponadto jeśli dane statyczne są synchronizowane, wywołania między metodami statycznymi, które zmieniają stan może spowodować zakleszczenia lub nadmiarowej synchronizacji, niekorzystnie wpływając na wydajność.  
  
## <a name="see-also"></a>Zobacz też

- [Wątków](../../../docs/standard/threading/index.md)
- [Wątki i wątkowość](../../../docs/standard/threading/threads-and-threading.md)
