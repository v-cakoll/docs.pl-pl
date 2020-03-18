---
title: Implementacja wzorca asynchronicznego opartego na zdarzeniach
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
ms.openlocfilehash: 9865fa169e0776765f9a97ec0a7b4555bf253886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "67663708"
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a>Implementacja wzorca asynchronicznego opartego na zdarzeniach

Jeśli piszesz klasę z niektórych operacji, które mogą ponosić zauważalne opóźnienia, należy rozważyć nadanie jej funkcji asynchronicznych, implementując [omówienie asynchronicznego wzorca opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).

Wzorzec asynchroniczny oparty na zdarzeniach zapewnia znormalizowany sposób pakowania klasy, która ma funkcje asynchroniczne. Jeśli zaimplementowane z <xref:System.ComponentModel.AsyncOperationManager>klas pomocnika, takich jak , klasa będzie działać poprawnie w dowolnym modelu aplikacji, w tym ASP.NET, aplikacji konsoli i aplikacji Windows Forms.

Na przykład, który implementuje wzorzec asynchroniczny oparty na zdarzeniach, zobacz [Jak: Implementowanie składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).

W przypadku prostych operacji asynchronicznych <xref:System.ComponentModel.BackgroundWorker> może się okazać, że składnik jest odpowiedni. Aby uzyskać <xref:System.ComponentModel.BackgroundWorker>więcej informacji na temat , zobacz [Jak: Uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).

Na poniższej liście opisano funkcje wzorca asynchronicznego opartego na zdarzeniach omówione w tym temacie.

- Możliwości implementowania wzorca asynchronicznego opartego na zdarzeniach

- Nazywanie metod asynchronicznych

- Opcjonalnie obsługa anulowania

- Opcjonalnie obsługa isbusy właściwość

- Opcjonalnie zapewnij obsługę raportowania postępów

- Opcjonalnie zapewnij obsługę zwracania wyników przyrostowych

- Obsługa parametrów out i ref w metodach

## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>Możliwości implementowania wzorca asynchronicznego opartego na zdarzeniach

Należy rozważyć wdrożenie wzorca asynchronicznego opartego na zdarzeniach, gdy:

- Klienci klasy nie potrzebują <xref:System.Threading.WaitHandle> <xref:System.IAsyncResult> i obiekty dostępne dla operacji asynchronicznych, co oznacza, że sondowanie i <xref:System.Threading.WaitHandle.WaitAll%2A> lub <xref:System.Threading.WaitHandle.WaitAny%2A> będą musiały być tworzone przez klienta.

- Operacje asynchroniczne mają być zarządzane przez klienta za pomocą znanego modelu zdarzenia/delegata.

Każda operacja jest kandydatem do implementacji asynchronicznej, ale te, które można oczekiwać, aby ponieść długie opóźnienia powinny być brane pod uwagę. Szczególnie odpowiednie są operacje, w których klienci dzwonią metodą i są powiadamiani po zakończeniu, bez konieczności dalszej interwencji. Odpowiednie są również operacje, które są uruchamiane w sposób ciągły, okresowo powiadamiając klientów o postępie, wynikach przyrostowych lub zmianach stanu.

Aby uzyskać więcej informacji na temat podejmowania decyzji, kiedy obsługiwać wzorzec asynchroniczny oparty na zdarzeniach, zobacz [Decydowanie o wdrożeniu wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).

## <a name="naming-asynchronous-methods"></a>Nazywanie metod asynchronicznych

Dla każdej metody synchronicznej *MethodName,* dla której chcesz podać odpowiednik asynchroniczny:

Zdefiniuj metodę**Asynia** _MethodName,_ która:

- Zwraca wartość `void`.

- Przyjmuje te same parametry, co *MethodName* metody.

- Akceptuje wiele wywołań.

Opcjonalnie zdefiniuj przeciążenie**Asynia** _Name MethodName,_ identyczne `userState`z _MethodName_**Async**, ale z dodatkowym parametrem o wartości obiektu o nazwie . Wykonaj to, jeśli jesteś przygotowany do zarządzania wieloma równoczesnych wywołań `userState` metody, w którym to przypadku wartość zostanie dostarczona z powrotem do wszystkich programów obsługi zdarzeń, aby odróżnić wywołania metody. Można również to zrobić po prostu jako miejsce do przechowywania stanu użytkownika do późniejszego pobierania.

Dla każdego oddzielnego podpisu metody _MethodName_**Async:**

1. Zdefiniuj następujące zdarzenie w tej samej klasie co metoda:

    ```vb
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler
    ```

    ```csharp
    public event MethodNameCompletedEventHandler MethodNameCompleted;
    ```

2. Zdefiniuj <xref:System.ComponentModel.AsyncCompletedEventArgs>następującego pełnomocnika i . Będą one prawdopodobnie zdefiniowane poza samą klasą, ale w tym samym obszarze nazw.

    ```vb
    Public Delegate Sub MethodNameCompletedEventHandler( _
        ByVal sender As Object, _
        ByVal e As MethodNameCompletedEventArgs)

    Public Class MethodNameCompletedEventArgs
        Inherits System.ComponentModel.AsyncCompletedEventArgs
    Public ReadOnly Property Result() As MyReturnType
    End Property
    ```

    ```csharp
    public delegate void MethodNameCompletedEventHandler(object sender,
        MethodNameCompletedEventArgs e);

    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs
    {
        public MyReturnType Result { get; }
    }
    ```

    - Upewnij się, że _MethodName_**CompletedEventArgs** klasy udostępnia jego elementy członkowskie jako właściwości tylko do odczytu, a nie pola, jak pola zapobiec powiązanie danych.

    - Nie należy <xref:System.ComponentModel.AsyncCompletedEventArgs>definiować żadnych klas pochodnych dla metod, które nie dają wyników. Wystarczy użyć samego <xref:System.ComponentModel.AsyncCompletedEventArgs> wystąpienia.

      > [!NOTE]
      > Jest całkowicie dopuszczalne, jeśli jest to wykonalne i <xref:System.ComponentModel.AsyncCompletedEventArgs> właściwe, ponowne użycie delegata i typów. W takim przypadku nazewnictwa nie będzie tak zgodne z nazwą metody, <xref:System.ComponentModel.AsyncCompletedEventArgs> ponieważ danego delegata i nie będą powiązane z jedną metodą.

## <a name="optionally-support-cancellation"></a>Opcjonalnie obsługa anulowania

Jeśli klasa będzie obsługiwać anulowanie operacji asynchronicznych, anulowanie powinno być widoczne dla klienta, jak opisano poniżej. Należy pamiętać, że istnieją dwa punkty decyzyjne, które muszą zostać osiągnięte przed zdefiniowaniem wsparcia anulowania:

- Czy twoja klasa, w tym przyszłe przewidywane dodatki do niej, mają tylko jedną operację asynchroniczną, która obsługuje anulowanie?

- Czy operacje asynchroniczne obsługujące anulowanie obsługują wiele oczekujących operacji? Oznacza to, czy _MethodName_**Async** metoda podjąć `userState` parametr i czy zezwala na wiele wywołań przed oczekiwaniem na dowolne do końca?

Skorzystaj z odpowiedzi na te dwa pytania w poniższej tabeli, aby określić, jaki powinien być podpis dla metody anulowania.

### <a name="visual-basic"></a>Visual Basic

||Obsługa wielu równoczesnych operacji|Tylko jedna operacja naraz|
|------|------------------------------------------------|----------------------------------|
|Jedna operacja Async w całej klasie|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|
|Wiele operacji asynchronicznej w klasie|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|

### <a name="c"></a>C\#

||Obsługa wielu równoczesnych operacji|Tylko jedna operacja naraz|
|------|------------------------------------------------|----------------------------------|
|Jedna operacja Async w całej klasie|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|
|Wiele operacji asynchronicznej w klasie|`void CancelAsync(object userState);`|`void CancelAsync();`|

Jeśli zdefiniujesz `CancelAsync(object userState)` metodę, klienci muszą być ostrożni podczas wybierania ich wartości stanu, aby mogły rozróżniać wszystkie metody asynchroniczne wywoływane na obiekcie, a nie tylko między wszystkimi wywołaniami pojedynczej metody asynchronicznej.

Decyzja o nazwie wersji pojedynczej operacji asynchronicznej _MethodName_**AsyncCancel** opiera się na możliwości łatwiejszego odnajdowania metody w środowisku projektowym, takim jak IntelliSense programu Visual Studio. To grupuje powiązanych członków i odróżnia je od innych elementów członkowskich, które nie mają nic wspólnego z funkcjami asynchronicznymi. Jeśli oczekujesz, że mogą istnieć dodatkowe operacje asynchroniczne `CancelAsync`dodane w kolejnych wersjach, lepiej jest zdefiniować .

Nie należy definiować wielu metod z powyższej tabeli w tej samej klasie. To nie ma sensu, lub będzie zaśmiecać interfejs klasy z proliferacji metod.

Te metody zazwyczaj zwróci natychmiast, a operacja może lub nie może faktycznie anulować. W programie obsługi zdarzeń dla _MethodName_**Complete** zdarzenia _MethodName_**CompleteArgs** obiekt zawiera `Cancelled` pole, które klienci mogą używać do określenia, czy nastąpiło anulowanie.

Przestrzegaj semantyki anulowania opisanej w [najlepszych rozwiązaniach dotyczących implementowania wzorca asynchronicznego opartego na zdarzeniach.](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)

## <a name="optionally-support-the-isbusy-property"></a>Opcjonalnie obsługa isbusy właściwość

Jeśli klasa nie obsługuje wielu równoczesnych wywołań, `IsBusy` należy rozważyć ujawnienie właściwości. Dzięki temu deweloperzy mogą określić, czy _MethodName_**Async** metoda jest uruchomiona bez przechwytywania wyjątek od _MethodName_**Async** metody.

Przestrzegaj `IsBusy` semantyki opisanej w [najlepszych rozwiązaniach dotyczących implementowania wzorca asynchronicznego opartego na zdarzeniach.](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)

## <a name="optionally-provide-support-for-progress-reporting"></a>Opcjonalnie zapewnij obsługę raportowania postępów

Często pożądane jest, aby operacja asynchroniczna zgłaszała postęp podczas jej działania. Wzorzec asynchroniczny oparty na zdarzeniach zawiera wskazówki dotyczące tego.

- Opcjonalnie zdefiniuj zdarzenie, które ma być wywoływane przez operację asynchroniczną i wywoływane w odpowiednim wątku. Obiekt <xref:System.ComponentModel.ProgressChangedEventArgs> zawiera wskaźnik postępu wartości całkowitej, który ma wynosić od 0 do 100.

- Nazwij to zdarzenie w następujący sposób:

  - `ProgressChanged`jeśli klasa ma wiele operacji asynchronicznych (lub oczekuje się, że wzrośnie do uwzględnienia wielu operacji asynchronicznych w przyszłych wersjach);

  - _MethodName_**ProgressChanged,** jeśli klasa ma jedną operację asynchroniczną.

  Ten wybór nazewnictwa paralele, które dla metody anulowania, zgodnie z opisem w opcjonalnie obsługuje anulowanie sekcji.

To zdarzenie powinno <xref:System.ComponentModel.ProgressChangedEventHandler> używać podpisu <xref:System.ComponentModel.ProgressChangedEventArgs> delegata i klasy. Alternatywnie, jeśli można podać wskaźnik postępu bardziej specyficzne dla domeny (na przykład bajty odczytu i całkowita liczba <xref:System.ComponentModel.ProgressChangedEventArgs>bajtów dla operacji pobierania), należy zdefiniować klasę pochodną .

Należy zauważyć, że `ProgressChanged` istnieje tylko jedno lub _MethodName_**ProgressChanged** zdarzenie dla klasy, niezależnie od liczby metod asynchronicznych, które obsługuje. Klienci powinni używać `userState` obiektu, który jest przekazywany do _MethodName_**Async** metody do rozróżniania między aktualizacjami postępu na wiele równoczesnych operacji.

Mogą wystąpić sytuacje, w których wiele operacji obsługuje postęp i każdy zwraca inny wskaźnik postępu. W takim przypadku `ProgressChanged` pojedyncze zdarzenie nie jest odpowiednie i `ProgressChanged` można rozważyć obsługę wielu zdarzeń. W takim przypadku należy użyć wzorca nazewnictwa _MethodName_**ProgressChanged** dla każdej metody**Asynchronia** _Nazwa metody._

Przestrzegaj semantyki raportowania postępu opisane [najlepsze rozwiązania dotyczące implementowania wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).

## <a name="optionally-provide-support-for-returning-incremental-results"></a>Opcjonalnie zapewnij obsługę zwracania wyników przyrostowych

Czasami operacja asynchroniczna może zwracać wyniki przyrostowe przed zakończeniem. Istnieje wiele opcji, które mogą służyć do obsługi tego scenariusza. Poniżej przedstawiono kilka przykładów.

### <a name="single-operation-class"></a>Klasa jednooperacyjna

Jeśli klasa obsługuje tylko jedną operację asynchroniczną, a ta operacja jest w stanie zwracać wyniki przyrostowe, a następnie:

- Rozszerz <xref:System.ComponentModel.ProgressChangedEventArgs> typ, aby przenosić przyrostowe dane wyników, i zdefiniuj zdarzenie _MethodName_**ProgressChanged** z tymi rozszerzonymi danymi.

- Wynieś to _Zdarzenie MethodName_**ProgressChanged,** gdy istnieje wynik przyrostowy do raportu.

To rozwiązanie ma zastosowanie w szczególności do klasy operacji pojedynczej asynchronicznej, ponieważ nie ma problemu z tym samym zdarzeniem występującym w celu zwrócenia wyników przyrostowych na "wszystkie operacje", tak jak robi to zdarzenie _MethodName_**ProgressChanged.**

### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>Klasa wielooperacjawa z jednorodnymi wynikami przyrostowymi

W takim przypadku klasa obsługuje wiele metod asynchronicznych, z których każda może zwracać wyniki przyrostowe, a te wyniki przyrostowe mają ten sam typ danych.

Postępuj zgodnie z modelem opisanym powyżej <xref:System.EventArgs> dla klas pojedynczej operacji, ponieważ ta sama struktura będzie działać dla wszystkich wyników przyrostowych. Zdefiniuj `ProgressChanged` zdarzenie zamiast _Zdarzenia MethodName_**ProgressChanged,** ponieważ ma ono zastosowanie do wielu metod asynchronicznych.

### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>Klasa wielooperacjawa z heterogenicznymi wynikami przyrostowymi

Jeśli klasa obsługuje wiele metod asynchronicznych, z których każda zwraca inny typ danych, należy:

- Oddziel raporty o wynikach przyrostowych od raportów o postępach.

- Zdefiniuj oddzielne Zdarzenie <xref:System.EventArgs> _MethodName_**ProgressChanged** z odpowiednim dla każdej metody asynchronicznej do obsługi przyrostowych danych wyników tej metody.

Wywołaj ten program obsługi zdarzeń w odpowiednim wątku, zgodnie z opisem w [najlepszych rozwiązań dotyczących implementowania wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).

## <a name="handling-out-and-ref-parameters-in-methods"></a>Obsługa parametrów out i ref w metodach

Mimo że `out` korzystanie `ref` z i jest, ogólnie rzecz biorąc, odradzane w .NET Framework, oto reguły, których należy przestrzegać, gdy są obecne:

Biorąc pod uwagę metodę synchroniczną *MethodName:*

- `out`parametry *do MethodName* nie powinny być częścią _MethodName_**Async**. Zamiast tego powinny być częścią _MethodName_**CompletedEventArgs** o tej samej nazwie, co jego odpowiednik parametru w *MethodName* (chyba że istnieje bardziej odpowiednia nazwa).

- `ref`parametry *do MethodName* powinny być wyświetlane jako część _MethodName_**Async**i jako część _MethodName_**CompletedEventArgs** o tej samej nazwie co jego odpowiednik parametru w *MethodName* (chyba że istnieje bardziej odpowiednia nazwa).

Na przykład, biorąc pod uwagę:

```vb
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer
```

```csharp
public int MethodName(string arg1, ref string arg2, out string arg3);
```

Metoda asynchroniczna <xref:System.ComponentModel.AsyncCompletedEventArgs> i jej klasa będzie wyglądać tak:

```vb
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)

Public Class MethodNameCompletedEventArgs
    Inherits System.ComponentModel.AsyncCompletedEventArgs
    Public ReadOnly Property Result() As Integer
    End Property
    Public ReadOnly Property Arg2() As String
    End Property
    Public ReadOnly Property Arg3() As String
    End Property
End Class
```

```csharp
public void MethodNameAsync(string arg1, string arg2);

public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs
{
    public int Result { get; };
    public string Arg2 { get; };
    public string Arg3 { get; };
}
```

## <a name="see-also"></a>Zobacz też

- <xref:System.ComponentModel.ProgressChangedEventArgs>
- <xref:System.ComponentModel.AsyncCompletedEventArgs>
- [Instrukcje: Implementacja składnika obsługującego wzorzec asynchroniczny oparty na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)
- [Instrukcje: uruchamianie operacji w tle](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)
- [Instrukcje: implementowanie formularza korzystającego z operacji w tle](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
- [Decydowanie o czasie implementacji klienta wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)
- [Najlepsze rozwiązania w zakresie implementacji wzorca asynchronicznego opartego na zdarzeniach](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
- [Asynchroniczny wzorzec oparty na zdarzeniach (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)
