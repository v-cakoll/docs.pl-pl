---
title: Zarządzana wątkowość — najlepsze rozwiązania
description: Uzyskaj informacje o zarządzanych wątkach najlepszych rozwiązań w programie .NET. Pracuj z trudnymi sytuacjami, takimi jak koordynowanie wielu wątków lub obsługa wątków blokujących.
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
ms.openlocfilehash: fa0af1461ba568583127316934b9d55577dd4c5a
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662826"
---
# <a name="managed-threading-best-practices"></a>Zarządzane wątki z najlepszymi rozwiązaniami
Wielowątkowość wymaga starannego programowania. W przypadku większości zadań można zmniejszyć złożoność przez kolejkowanie żądań na potrzeby wykonywania przez wątki puli wątków. Ten temat dotyczy trudniejszych sytuacji, takich jak koordynacja pracy wielu wątków lub obsługa wątków, które blokują.  
  
> [!NOTE]
> Począwszy od .NET Framework 4, Biblioteka zadań równoległych i PLINQ zapewniają interfejsy API, które zmniejszają część złożoności i zagrożeń związanych z programowaniem wielowątkowym. Aby uzyskać więcej informacji, zobacz [programowanie równoległe w programie .NET](../parallel-programming/index.md).  
  
## <a name="deadlocks-and-race-conditions"></a>Zakleszczenia i sytuacje wyścigu  
 Wielowątkowość rozwiązuje problemy dotyczące przepływności i czasu reakcji, ale w ten sposób wprowadza nowe problemy: zakleszczenie i sytuacje wyścigu.  
  
### <a name="deadlocks"></a>Zakleszczenia  
 Zakleszczenie występuje, gdy każdy z dwóch wątków próbuje zablokować zasób, drugi został już zablokowany. Żaden wątek nie może wykonywać żadnych dalszych postępów.  
  
 Wiele metod klas zarządzanych wątków zapewnia przekroczenia limitu czasu, aby pomóc w wykrywaniu zakleszczenii. Na przykład poniższy kod próbuje uzyskać blokadę obiektu o nazwie `lockObject` . Jeśli blokada nie zostanie uzyskana w 300 milisekundach, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> zwraca `false` .  
  
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
 Sytuacja wyścigu jest usterką, która występuje, gdy wynik programu zależy od tego, co dwa lub więcej wątków osiągną określony blok kodu jako pierwszy. Uruchamianie programu wiele razy daje różne wyniki, a wynik danego uruchomienia nie może być przewidywany.  
  
 Prosty przykład warunku wyścigu powoduje zwiększenie pola. Załóżmy, że Klasa ma prywatne pole **statyczne** (**udostępniane** w Visual Basic), które jest zwiększane za każdym razem, gdy tworzone jest wystąpienie klasy, przy użyciu kodu, takiego jak `objCt++;` (C#) lub `objCt += 1` (Visual Basic). Ta operacja wymaga załadowania wartości z `objCt` do rejestru, zwiększenia wartości i zapisania jej w `objCt` .  
  
 W aplikacji wielowątkowej wątek, który został załadowany i zwiększony wartość może zostać przeniesiona przez inny wątek, który wykonuje wszystkie trzy kroki; gdy pierwszy wątek wznawia wykonywanie i przechowuje jego wartość, zastępuje bez uwzględniania `objCt` faktu, że wartość została zmieniona w tymczasowym.  
  
 Ten konkretny warunek wyścigu można łatwo uniknąć przy użyciu metod <xref:System.Threading.Interlocked> klasy, takich jak <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType> . Aby zapoznać się z innymi technikami synchronizowania danych między wieloma wątkami, zobacz [synchronizowanie danych w celu wielowątkowości](synchronizing-data-for-multithreading.md).  
  
 Sytuacje wyścigu mogą również wystąpić podczas synchronizowania działań wielu wątków. Za każdym razem, gdy piszesz wiersz kodu, należy wziąć pod uwagę to, co może się zdarzyć, jeśli wątek został przemieszczony przed wykonaniem wiersza (lub przed dowolnym z instrukcji poszczególnych maszyn, które składają się na linię), a inny wątek przejdzie do niego.  
  
## <a name="static-members-and-static-constructors"></a>Statyczne elementy członkowskie i konstruktory statyczne  
 Klasa nie została zainicjowana do momentu zakończenia działania konstruktora klasy ( `static` Konstruktor w języku C# w `Shared Sub New` Visual Basic). Aby zapobiec wykonywaniu kodu w typie, który nie został zainicjowany, środowisko uruchomieniowe języka wspólnego blokuje wszystkie wywołania z innych wątków do `static` elementów członkowskich klasy ( `Shared` elementy członkowskie w Visual Basic) do momentu zakończenia działania konstruktora klasy.  
  
 Na przykład jeśli Konstruktor klasy uruchamia nowy wątek, a procedura wątku wywołuje `static` element członkowski klasy, nowy wątek jest blokowany do momentu ukończenia konstruktora klasy.  
  
 Dotyczy to dowolnego typu, który może mieć `static` Konstruktor.  

## <a name="number-of-processors"></a>Liczba procesorów

Bez względu na to, czy istnieje wiele procesorów, czy tylko jeden procesor dostępny w systemie może mieć wpływ na architekturę wielowątkową. Aby uzyskać więcej informacji, zobacz [Liczba procesorów](https://docs.microsoft.com/previous-versions/dotnet/netframework-1.1/1c9txz50(v%3dvs.71)#number-of-processors).

Użyj <xref:System.Environment.ProcessorCount?displayProperty=nameWithType> właściwości, aby określić liczbę procesorów dostępnych w czasie wykonywania.
  
## <a name="general-recommendations"></a>Ogólne zalecenia  
 Podczas korzystania z wielu wątków należy wziąć pod uwagę następujące wytyczne:  
  
- Nie używaj <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> do kończenia innych wątków. Wywołanie metody **Abort** w innym wątku jest zbliżone, aby zgłaszać wyjątek w tym wątku, bez znajomości tego, który punkt został osiągnięty w jego przetwarzaniu.  
  
- Nie używaj <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> i <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> synchronizowania działań wielu wątków. Użyj <xref:System.Threading.Mutex> , <xref:System.Threading.ManualResetEvent> , <xref:System.Threading.AutoResetEvent> , i <xref:System.Threading.Monitor> .  
  
- Nie Kontroluj wykonywania wątków roboczych z głównego programu (na przykład przy użyciu zdarzeń). Zamiast tego Zaprojektuj program tak, aby wątki robocze były odpowiedzialne za oczekiwanie na dostępność, wykonanie tej operacji i powiadomienie innych części programu po zakończeniu. Jeśli wątki robocze nie są blokowane, należy rozważyć użycie wątków puli wątków. <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType>jest przydatny w sytuacjach, w których działa blok wątków roboczych.  
  
- Nie używaj typów jako obiektów blokady. Oznacza to, że należy unikać kodu, takiego jak `lock(typeof(X))` C# lub `SyncLock(GetType(X))` w Visual Basic, lub używania <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> z <xref:System.Type> obiektami. Dla danego typu istnieje tylko jedno wystąpienie dla <xref:System.Type?displayProperty=nameWithType> każdej domeny aplikacji. Jeśli typ, w którym jest wykonywane zablokowanie, jest publiczny, kod inny niż własny może być na nim zablokowany, prowadząc do zakleszczenia. Aby uzyskać dodatkowe problemy, zobacz [najlepsze rozwiązania dotyczące niezawodności](../../framework/performance/reliability-best-practices.md).  
  
- Należy zachować ostrożność podczas blokowania wystąpień, na przykład `lock(this)` w języku C# lub `SyncLock(Me)` w Visual Basic. Jeśli inny kod w aplikacji, zewnętrzny dla tego typu, przyjmuje blokadę obiektu, mogą wystąpić zakleszczenia.  
  
- Upewnij się, że wątek, który został wprowadzony do monitora, zawsze opuszcza ten monitor, nawet jeśli wystąpi wyjątek, gdy wątek jest w monitorze. Instrukcja [Lock](../../csharp/language-reference/keywords/lock-statement.md) języka C# i instrukcja Visual Basic [SyncLock](../../visual-basic/language-reference/statements/synclock-statement.md) umożliwiają automatyczne udostępnienie tego zachowania, przy użyciu bloku **finally** , aby upewnić się, że <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> jest wywoływana. Jeśli nie można zagwarantować, że **wyjście** zostanie wywołane, Rozważ zmianę projektu w celu użycia **muteksu**. Element mutex jest automatycznie wydawany, gdy wątek, który jest aktualnie do przerwania.  
  
- Używaj wielu wątków dla zadań, które wymagają różnych zasobów i nie należy przypisywać wielu wątków do pojedynczego zasobu. Na przykład każde zadanie związane z korzyściami we/wy z posiadania własnego wątku, ponieważ ten wątek zostanie zablokowany podczas operacji we/wy i w ten sposób zezwala na wykonywanie innych wątków. Dane wejściowe użytkownika to inne zasoby, które są korzyści z dedykowanego wątku. Na komputerze z jednym procesorem zadanie, które obejmuje intensywne obliczenia, zawiera dane wejściowe użytkownika i zadania, które obejmują operacje we/wy, ale wiele zadań intensywnie korzystających z obliczeń będą konkurować o ze sobą.  
  
- Rozważ użycie metod <xref:System.Threading.Interlocked> klasy dla prostych zmian stanu, zamiast używać `lock` instrukcji ( `SyncLock` w Visual Basic). `lock`Instrukcja jest dobrym narzędziem ogólnego przeznaczenia, ale <xref:System.Threading.Interlocked> Klasa zapewnia lepszą wydajność dla aktualizacji, które muszą być niepodzielne. Wewnętrznie wykonuje pojedynczy prefiks blokady w przypadku braku rywalizacji. W przeglądach kodu Obejrzyj kod podobny do przedstawionego w poniższych przykładach. W pierwszym przykładzie zmienna stanu jest zwiększana:  
  
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
  
     Można zwiększyć wydajność przy użyciu <xref:System.Threading.Interlocked.Increment%2A> metody zamiast `lock` instrukcji, w następujący sposób:  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    > W .NET Framework 2,0 i nowszych Użyj <xref:System.Threading.Interlocked.Add%2A> metody dla przyrostów niepodzielnych większych niż 1.  
  
     W drugim przykładzie zmienna typu odwołania jest aktualizowana tylko wtedy, gdy jest to odwołanie o wartości null ( `Nothing` w Visual Basic).  
  
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
  
     Wydajność można ulepszyć za pomocą <xref:System.Threading.Interlocked.CompareExchange%2A> metody zamiast tego w następujący sposób:  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    > Począwszy od .NET Framework 2,0, <xref:System.Threading.Interlocked.CompareExchange%60%601%28%60%600%40%2C%60%600%2C%60%600%29> Przeciążenie metody zapewnia bezpieczną alternatywę typu dla typów referencyjnych.
  
## <a name="recommendations-for-class-libraries"></a>Zalecenia dotyczące bibliotek klas  
 Podczas projektowania bibliotek klas dla wielowątkowości należy wziąć pod uwagę następujące wytyczne:  
  
- Należy unikać synchronizacji, jeśli jest to możliwe. Jest to szczególnie prawdziwe w przypadku silnie używanego kodu. Na przykład algorytm może zostać dostosowany do tolerowania warunku wyścigu zamiast go wyeliminować. Niepotrzebna synchronizacja zmniejsza wydajność i tworzy możliwość zakleszczenia i warunków wyścigu.  
  
- Domyślnie Udostępnij statyczne dane ( `Shared` w Visual Basic).  
  
- Nie wykonuj domyślnego wątku danych wystąpienia. Dodanie blokad do tworzenia kodu bezpiecznego wątków zmniejsza wydajność, zwiększa rywalizację o blokady i tworzy możliwość wystąpienia zakleszczenia. W przypadku wspólnych modeli aplikacji tylko jeden wątek w danym momencie wykonuje kod użytkownika, co minimalizuje konieczność zapewnienia bezpieczeństwa wątków. Z tego powodu biblioteki klas .NET Framework nie są bezpieczne wątkowo.  
  
- Unikaj udostępniania metod statycznych, które zmieniają stan statyczny. W typowych scenariuszach serwera stan statyczny jest współużytkowany między żądaniami, co oznacza, że wiele wątków może wykonać ten kod w tym samym czasie. Spowoduje to otwarcie możliwości występowania błędów wątków. Rozważ użycie wzorca projektowego, który hermetyzuje dane w wystąpieniach, które nie są współużytkowane przez żądania. Ponadto jeśli dane statyczne są synchronizowane, wywołania między metodami statycznymi, które zmieniają stan, mogą spowodować zakleszczenia lub nadmiarowa synchronizacja, niekorzystnie wpływając na wydajność.  
  
## <a name="see-also"></a>Zobacz także

- [Wątkowość](index.md)
- [Wątki i wątkowość](threads-and-threading.md)
