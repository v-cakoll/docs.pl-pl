---
title: Model programowania asynchronicznego zadania (TAP) z asynchroniczne i oczekujące (C#)
ms.date: 05/22/2017
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
ms.openlocfilehash: 644830ac62a4df23f22d8f91e9b3c768dd611451
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395694"
---
# <a name="task-asynchronous-programming-model"></a>Model programowania asynchronicznego zadań (APM)

Możesz uniknąć problemów z wydajnością i poprawić ogólny czas odpowiedzi aplikacji, stosując programowanie asynchroniczne. Jednak tradycyjne techniki pisania aplikacji asynchronicznych mogą być skomplikowane, przez co trudne do pisania, debugowania i konserwacji.

5 wprowadzono uproszczone podejście, programowanie asynchroniczne, które wykorzystuje asynchroniczne wsparcie w .NET Framework 4,5 i wyższych, .NET Core i środowisko wykonawcze systemu Windows. [ C# ](../../../whats-new/csharp-version-history.md#c-version-50) Kompilator wykonuje trudną pracę, którą kiedyś wykonywał programista, a aplikacja zachowuje strukturę logiczną przypominającą kod synchroniczny. W efekcie masz wszystkie korzyści wynikające z programowania asynchronicznego przy ułamkowym nakładzie pracy.

Ten temat zawiera omówienie, kiedy i jak stosować programowanie async oraz zawiera łącza do tematów zawierających szczegółowe informacje oraz przykłady.

## <a name="BKMK_WhentoUseAsynchrony"></a>Asynchroniczne zwiększenie czasu odpowiedzi

Asynchroniczności jest istotna dla działań, które mogą być blokowane, takich jak dostęp do sieci Web. Dostęp do zasobów sieci Web bywa powolny lub opóźniony. Jeśli takie działanie jest zablokowane w procesie synchronicznym, cała aplikacja musi czekać. W procesie asynchronicznym aplikacja może kontynuować wykonywanie innych zadań, które nie są zależne od zasobów sieci Web, do momentu zakończeniem zadania mogącego powodować blokowanie.

W poniższej tabeli przedstawiono typowe obszary, w których programowanie asynchroniczne poprawia czas odpowiedzi. Wymienione interfejsy API platformy .NET i środowisko wykonawcze systemu Windows zawierają metody, które obsługują programowanie asynchroniczne.

| Obszar aplikacji    | Typy .NET z metodami asynchronicznymi     | Typy środowisko wykonawcze systemu Windows z metodami asynchronicznymi  |
|---------------------|-----------------------------------|-------------------------------------------|
|Web access|<xref:System.Net.Http.HttpClient>|<xref:Windows.Web.Syndication.SyndicationClient>|
|Praca z plikami|<xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|<xref:Windows.Storage.StorageFile>|
|Praca z obrazami||<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|
|Programowanie WCF|[Operacje synchroniczne i asynchroniczne](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)||

Asynchroniczność okazuje się szczególnie cenna w przypadku aplikacji, które mają dostęp do wątku interfejsu użytkownika, ponieważ wszystkie działania związane z interfejsem użytkownika korzystają zazwyczaj z jednego wątku. Jeśli w aplikacji synchronicznej jest zablokowany jakikolwiek proces, zablokowane są wszystkie procesy. Aplikacja przestanie odpowiadać i możesz dojść do wniosku, że uległa awarii, a tymczasem może po prostu być w stanie oczekiwania.

Kiedy używasz metod asynchronicznych, aplikacja dalej odpowiada interfejsowi użytkownika. Możesz przykładowo zmienić rozmiar lub zminimalizować aplikację lub możesz ją zamknąć, jeżeli nie chcesz czekać aż zakończy zadanie.

Podejście async oferuje również odpowiednik automatycznego przejścia do listy opcji do wybrania przy projektowaniu operacji asynchronicznych. Oznacza to, że można korzystać z wszystkich zalet tradycyjnego programowania asynchronicznego, ale przy znacznie mniejszym nakładzie pracy programisty.

## <a name="BKMK_HowtoWriteanAsyncMethod"></a>Metody asynchroniczne są łatwiejsze do zapisu

Słowa kluczowe [Async](../../../language-reference/keywords/async.md) i [await](../../../language-reference/operators/await.md) w C# programie to serce programowanie asynchroniczne. Korzystając z tych dwóch słów kluczowych, można użyć zasobów w .NET Framework, .NET Core lub środowisko wykonawcze systemu Windows, aby szybko utworzyć metodę asynchroniczną niemal jak w przypadku tworzenia metody synchronicznej. Metody asynchroniczne zdefiniowane za pomocą słowa kluczowego `async` są określane mianem *metod asynchronicznych*.

W poniższym przykładzie przedstawiono metodę async. Prawie wszystko w kodzie powinno wyglądać znajomo.

Kompletny przykładowy plik Windows Presentation Foundation (WPF) można znaleźć na końcu tego tematu i można pobrać przykład z [przykład Async: przykład z "programowania asynchronicznego z Async i await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs/).

```csharp
async Task<int> AccessTheWebAsync()
{
    // You need to add a reference to System.Net.Http to declare client.
    var client = new HttpClient();

    // GetStringAsync returns a Task<string>. That means that when you await the
    // task you'll get a string (urlContents).
    Task<string> getStringTask = client.GetStringAsync("https://docs.microsoft.com/dotnet");

    // You can do work here that doesn't rely on the string from GetStringAsync.
    DoIndependentWork();

    // The await operator suspends AccessTheWebAsync.
    //  - AccessTheWebAsync can't continue until getStringTask is complete.
    //  - Meanwhile, control returns to the caller of AccessTheWebAsync.
    //  - Control resumes here when getStringTask is complete.
    //  - The await operator then retrieves the string result from getStringTask.
    string urlContents = await getStringTask;

    // The return statement specifies an integer result.
    // Any methods that are awaiting AccessTheWebAsync retrieve the length value.
    return urlContents.Length;
}
```

Możesz poznać kilka praktyk z powyższego przykładu. Zacznij od sygnatury metody. Zawiera modyfikator `async`. Zwracany typ to `Task<int>` (zobacz sekcję "typy zwracane", aby uzyskać więcej opcji). Nazwa metody jest zakończona `Async`. W treści metody `GetStringAsync` zwraca `Task<string>`. Oznacza to, że w przypadku `await` zadania uzyskasz `string` (`urlContents`).  Przed oczekiwaniem na zadanie można wykonać zadania, które nie polegają na `string` od `GetStringAsync`.

Zwróć szczególną uwagę na operator `await`. Wstrzymuje `AccessTheWebAsync`;

- nie można kontynuować `AccessTheWebAsync` do momentu ukończenia `getStringTask`.
- W tym czasie sterowanie powraca do obiektu wywołującego `AccessTheWebAsync`.
- Formant zostanie wznowiony w tym miejscu po zakończeniu `getStringTask`.
- Następnie operator `await` pobiera wynik `string` z `getStringTask`.

Instrukcja return określa wynik w postaci liczby całkowitej. Wszystkie metody, które oczekują na `AccessTheWebAsync` Pobieranie wartości długości.

Jeśli `AccessTheWebAsync` nie ma żadnej pracy, którą może wykonać między wywołaniem `GetStringAsync` i oczekiwaniem na jego zakończenie, można uprościć kod, wywołując i await w następującej pojedynczej instrukcji.

```csharp
string urlContents = await client.GetStringAsync("https://docs.microsoft.com/dotnet");
```

Poniższe cechy podsumowują, co sprawia, że w poprzednim przykładzie metoda async:

- Podpis metody zawiera modyfikator `async`.
- Nazwa metody async kończy się zwyczajowo sufiksem „Async”.
- Zwracany typ może być jednym z następujących:

  - <xref:System.Threading.Tasks.Task%601>, jeśli metoda zawiera instrukcję return, w której operand ma typ `TResult`.
  - <xref:System.Threading.Tasks.Task>, jeśli metoda nie zawiera instrukcji return lub zawiera instrukcję return bez operandu.
  - `void`, jeśli piszesz procedurę obsługi zdarzeń asynchronicznych.
  - Każdy inny typ, który ma metodę `GetAwaiter` (rozpoczynając od C# 7,0).

  Aby uzyskać więcej informacji, zobacz sekcję [typy zwracane i parametry](#BKMK_ReturnTypesandParameters) .

- Metoda zwykle zawiera co najmniej jedno wyrażenie `await`, które oznacza punkt, w którym metoda nie może kontynuować do momentu ukończenia operacji asynchronicznej oczekującej. W tym czasie metoda jest zawieszona, a sterowanie powraca do obiektu wywołującego metodę. Następna sekcji tego tematu przedstawia, co się dzieje w punkcie zawieszenia.

W metodzie asynchronicznej używasz podanych słów kluczowych i typów w celu wskazania, co chcesz zrobić, a kompilator zajmie się resztą, w tym śledzeniem tego, co musi się zdarzyć, gdy sterowanie powraca do punktu oczekiwania w metodzie zawieszonej. Niektóre procesy, takie jak pętle i obsługa wyjątków, mogą być trudne do obsłużenia w tradycyjnym kodzie asynchronicznym. W metodzie asynchronicznej wpisujesz te elementy podobnie jak w rozwiązaniu synchronicznym i problem rozwiązany.

Aby uzyskać więcej informacji na temat asynchroniczności w poprzednich wersjach .NET Framework, zobacz [TPL i tradycyjne .NET Framework programowanie asynchroniczne](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Co dzieje się w metodzie asynchronicznej

Ważne jest, aby rozumieć programowanie asynchroniczne jako przepływ sterowania od metody do metody. Poniższy diagram przeprowadzi Cię przez proces:

![Śledzenie programu asynchronicznego](./media/task-asynchronous-programming-model/navigation-trace-async-program.png "NavigationTrace")

Liczby na diagramie odpowiadają następującym krokom, inicjowanym po kliknięciu przycisku "Start" przez użytkownika.

1. Program obsługi zdarzeń wywołuje i czeka na metodę asynchroniczną `AccessTheWebAsync`.

2. `AccessTheWebAsync` tworzy wystąpienie <xref:System.Net.Http.HttpClient> i wywołuje metodę asynchroniczną <xref:System.Net.Http.HttpClient.GetStringAsync%2A>, aby pobrać zawartość witryny sieci Web jako ciąg.

3. Coś się dzieje w `GetStringAsync`, który zawiesza postęp. Być może metoda musi czekać na pobranie strony internetowej lub inne działanie blokujące. Aby uniknąć zablokowania zasobów, `GetStringAsync` daje formant do obiektu wywołującego, `AccessTheWebAsync`.

     `GetStringAsync` zwraca <xref:System.Threading.Tasks.Task%601>, gdzie `TResult` jest ciągiem, a `AccessTheWebAsync` przypisuje zadanie do zmiennej `getStringTask`. Zadanie reprezentuje proces trwającego wywołania do `GetStringAsync`, z zobowiązaniem do tworzenia rzeczywistej wartości ciągu po zakończeniu pracy.

4. Ponieważ `getStringTask` nie został jeszcze oczekiwany, `AccessTheWebAsync` może kontynuować wykonywanie innych zadań, które nie zależą od końcowego wyniku `GetStringAsync`. To działanie jest reprezentowane przez wywołanie metody synchronicznej `DoIndependentWork`.

5. `DoIndependentWork` to metoda synchroniczna, która wykonuje jej działanie i powraca do obiektu wywołującego.

6. `AccessTheWebAsync` zabrakło pracy, które może wykonać bez wyniku z `getStringTask`. `AccessTheWebAsync` dalej chce obliczyć i zwrócić długość pobranego ciągu, ale metoda nie może obliczyć tej wartości, dopóki metoda nie ma ciągu.

     W związku z tym `AccessTheWebAsync` używa operatora await, aby zawiesić postęp i przekazać kontrolę do metody, która została wywołana `AccessTheWebAsync`. `AccessTheWebAsync` zwraca `Task<int>` do obiektu wywołującego. Zadanie przedstawia obietnicę utworzenia w wyniku liczby całkowitej, która jest długością pobranego ciągu.

    > [!NOTE]
    > Jeśli `GetStringAsync` (i w związku z tym `getStringTask`) kończy przed `AccessTheWebAsync` czeka na to, formant pozostaje w `AccessTheWebAsync`. Koszt zawieszenia, a następnie powrotu do `AccessTheWebAsync` zostałby zatracony, jeśli wywołany proces asynchroniczny (`getStringTask`) został już ukończony i `AccessTheWebAsync` nie musi czekać na wynik końcowy.

     Przetwarzanie wzorca jest kontynuowane wewnątrz elementu wywołującego (programu obsługi zdarzeń w tym przykładzie). Obiekt wywołujący może wykonywać inne czynności, które nie są zależne od wyniku `AccessTheWebAsync` przed oczekiwaniem na ten wynik, lub obiekt wywołujący może natychmiast oczekiwać.   Program obsługi zdarzeń oczekuje na `AccessTheWebAsync`, a `AccessTheWebAsync` oczekuje na `GetStringAsync`.

7. `GetStringAsync` uzupełnia i generuje wynik w postaci ciągu. Wynik ciągu nie jest zwracany przez wywołanie `GetStringAsync` w oczekiwany sposób. (Należy pamiętać, że metoda zwróciła już zadanie w kroku 3). Zamiast tego wynik w postaci ciągu jest przechowywany w zadaniu, które reprezentuje zakończenie metody, `getStringTask`. Operator await pobiera wynik z `getStringTask`. Instrukcja przypisania przypisuje pobrany wynik do `urlContents`.

8. Gdy `AccessTheWebAsync` ma wynik ciągu, Metoda może obliczyć długość ciągu. Następnie należy wykonać pracę `AccessTheWebAsync`, a procedura obsługi zdarzeń oczekujących może zostać wznowiona. W pełnym przykładzie na końcu tematu można zobaczyć, że program obsługi zdarzeń pobiera i drukuje wynikową wartość długości.
Jeśli dopiero zaczynasz przygodę z programowaniem asynchronicznym, zastanów się przez chwilę, jaka jest różnica między zachowaniem synchronicznym i asynchronicznym. Metoda synchroniczna kończy działanie, gdy praca jest zakończona (krok 5), natomiast metoda asynchroniczna zwraca wartość zadania, gdy jej praca jest zawieszona (kroki 3 i 6). Gdy metoda async ukończy pracę, zadanie jest oznaczane jako ukończone, a wynik, o ile istnieje, jest zapisywany w zadaniu.

Aby uzyskać więcej informacji o przepływie sterowania, zobacz [sterowanie przepływem wC#programach asynchronicznych ()](control-flow-in-async-programs.md).

## <a name="BKMK_APIAsyncMethods"></a>Metody asynchroniczne interfejsu API

Być może zastanawiasz się, gdzie można znaleźć metody, takie jak `GetStringAsync`, które obsługują programowanie asynchroniczne. .NET Framework 4,5 lub nowszy i .NET Core zawierają wiele elementów członkowskich, które współpracują z `async` i `await`. Można je rozpoznać za pomocą sufiksu "Async", który jest dołączany do nazwy elementu członkowskiego, i typu zwracanego <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Na przykład Klasa `System.IO.Stream` zawiera metody takie jak <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A> i <xref:System.IO.Stream.WriteAsync%2A> obok metod synchronicznych <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A> i <xref:System.IO.Stream.Write%2A>.

Środowisko wykonawcze systemu Windows również zawiera wiele metod, których można użyć z `async` i `await` w aplikacjach systemu Windows. Aby uzyskać więcej informacji, zobacz [wątkowość i programowanie asynchroniczne](/windows/uwp/threading-async/) dla programowania platformy UWP oraz [programowanie asynchroniczne (aplikacje do sklepu Windows)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) i [Szybki Start: wywoływanie C# asynchronicznych interfejsów API w programie lub Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10)) , jeśli używasz wcześniejszych wersji programu środowisko wykonawcze systemu Windows.

## <a name="BKMK_Threads"></a>Wątk

Metody async mają być operacjami niepowodującymi blokowania. Wyrażenie `await` w metodzie asynchronicznej nie blokuje bieżącego wątku, gdy oczekiwane zadanie jest uruchomione. Zamiast tego, wyrażenie rejestruje pozostałą część metody jako kontynuację i przekazuje sterowanie do obiektu wywołującego metody async.

Słowa kluczowe `async` i `await` nie powodują tworzenia dodatkowych wątków. Metody komunikacji async nie wymagają wielowątkowości, ponieważ nie działają we własnym wątku. Metoda działa w bieżącym kontekście synchronizacji i używa czasu wątku, tylko wtedy, gdy jest aktywna. @No__t-0 służy do przenoszenia pracy powiązanej z PROCESORem do wątku w tle, ale wątek w tle nie jest w stanie pomóc w przypadku procesu, który tylko oczekuje na dostępność wyników.

Podejście async do programowania asynchronicznego jest preferowane prawie w każdym przypadku. W szczególności ta metoda jest lepsza niż Klasa <xref:System.ComponentModel.BackgroundWorker> dla operacji we/wy, ponieważ kod jest prostszy i nie trzeba chronić przed warunkami wyścigu. W połączeniu z metodą <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> programowanie asynchroniczne jest lepsze niż <xref:System.ComponentModel.BackgroundWorker> dla operacji związanych z PROCESORem, ponieważ programowanie asynchroniczne oddziela szczegóły koordynacji dotyczące uruchamiania kodu z pracy, która `Task.Run` transferuje do puli wątków.

## <a name="BKMK_AsyncandAwait"></a>Async i await

Jeśli określisz, że metoda jest metodą asynchroniczną przy użyciu modyfikatora [Async](../../../language-reference/keywords/async.md) , włączysz następujące dwie możliwości.

- Oznaczona Metoda async może użyć [oczekiwania](../../../language-reference/operators/await.md) do wyznaczenia punktów zawieszenia. Operator `await` instruuje kompilator, że metoda async nie może kontynuować tego punktu do momentu zakończenia procesu asynchronicznego oczekiwania. W międzyczasie sterowanie powraca do obiektu wywołującego metodę async.

     Zawieszenie metody asynchronicznej w wyrażeniu `await` nie stanowi wyjścia z metody, a bloki `finally` nie są uruchamiane.

- Metoda oznaczona jako async sama może być oczekiwana przez metody, które ją wywołują.

Metoda async zwykle zawiera co najmniej jedno wystąpienie operatora `await`, ale brak wyrażeń `await` nie powoduje błędu kompilatora. Jeśli Metoda asynchroniczna nie używa operatora `await` do oznaczania punktu zawieszenia, metoda jest wykonywana jako metoda synchroniczna, pomimo modyfikatora `async`. Kompilator generuje ostrzeżenia dla takich metod.

`async` i `await` są kontekstowymi słowami kluczowymi. Aby uzyskać więcej informacji i przykładów, zobacz następujący temat:

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)

## <a name="BKMK_ReturnTypesandParameters"></a>Typy zwracane i parametry

Metoda async zwykle zwraca <xref:System.Threading.Tasks.Task> lub <xref:System.Threading.Tasks.Task%601>. Wewnątrz metody asynchronicznej do zadania, które jest zwracane z wywołania innej metody asynchronicznej, jest stosowany operator `await`.

Należy określić <xref:System.Threading.Tasks.Task%601> jako typ zwracany, jeśli metoda zawiera instrukcję [`return`](../../../language-reference/keywords/return.md) , która określa operand typu `TResult`.

Jeśli metoda nie zawiera instrukcji return lub zawiera instrukcję return, która nie zwraca operandu, należy użyć <xref:System.Threading.Tasks.Task> jako zwracanego typu.

Począwszy od C# 7,0, można również określić dowolny inny zwracany typ, pod warunkiem, że typ zawiera metodę `GetAwaiter`. Przykładem tego typu jest <xref:System.Threading.Tasks.ValueTask%601>. Jest on dostępny w pakiecie NuGet [System. Threading. Tasks. Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) .

Poniższy przykład pokazuje, jak zadeklarować i wywołać metodę, która zwraca <xref:System.Threading.Tasks.Task%601> lub <xref:System.Threading.Tasks.Task>:

```csharp
// Signature specifies Task<TResult>
async Task<int> GetTaskOfTResultAsync()
{
    int hours = 0;
    await Task.Delay(0);
    // Return statement specifies an integer result.
    return hours;
}

// Calls to GetTaskOfTResultAsync
Task<int> returnedTaskTResult = GetTaskOfTResultAsync();
int intResult = await returnedTaskTResult;
// or, in a single statement
int intResult = await GetTaskOfTResultAsync();

// Signature specifies Task
async Task GetTaskAsync()
{
    await Task.Delay(0);
    // The method has no return statement.
}

// Calls to GetTaskAsync
Task returnedTask = GetTaskAsync();
await returnedTask;
// or, in a single statement
await GetTaskAsync();
```

Każde zwracane zadanie reprezentuje zadanie pracy w toku. Zadanie zawiera informacje o stanie procesu asynchronicznego i, ostatecznie, albo ostatecznego wyniku procesu lub wyjątku, który zgłasza proces, jeśli się nie powiedzie.

Metoda async może również mieć typ zwracany `void`. Ten typ zwracany jest używany głównie do definiowania programów obsługi zdarzeń, gdzie wymagany jest typ zwracany `void`. Programy async obsługi zdarzeń często służą jako punkt wejścia dla programów async.

Nie można oczekiwać metody asynchronicznej, która ma typ zwracany `void`, a obiekt wywołujący metodę zwracającą wartość void nie może przechwycić żadnych wyjątków zgłaszanych przez metodę.

Metoda async nie może deklarować parametrów [in](../../../language-reference/keywords/in-parameter-modifier.md), [ref](../../../language-reference/keywords/ref.md) ani [out](../../../language-reference/keywords/out-parameter-modifier.md) , ale metoda może wywoływać metody, które mają takie parametry. Podobnie Metoda asynchroniczna nie może zwracać wartości przez odwołanie, chociaż może wywoływać metody z ref zwracanymi wartościami.

Aby uzyskać więcej informacji i przykładów, zobacz [asynchroniczne typy zwracaneC#()](./async-return-types.md). Aby uzyskać więcej informacji o sposobie przechwytywania wyjątków w metodach asynchronicznych, zobacz [try-catch](../../../language-reference/keywords/try-catch.md).

Asynchroniczne interfejsy API w programowaniu środowisko wykonawcze systemu Windows mają jeden z następujących typów zwracanych, które są podobne do zadań:

- <xref:Windows.Foundation.IAsyncOperation%601>, który odnosi się do <xref:System.Threading.Tasks.Task%601>
- <xref:Windows.Foundation.IAsyncAction>, który odnosi się do <xref:System.Threading.Tasks.Task>
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

## <a name="BKMK_NamingConvention"></a>Konwencja nazewnictwa

Zgodnie z Konwencją metody, które zwracają powszechnie oczekiwane typy (np. `Task`, `Task<T>`, `ValueTask`, `ValueTask<T>`) powinny mieć nazwy kończące się na "Async". Metody, które uruchamiają operację asynchroniczną, ale nie zwracają typu oczekującego, nie powinny mieć nazw kończących się na "Async", ale mogą zaczynać się od "BEGIN", "Start" lub innego zlecenia, aby zasugerować, że ta metoda nie zwraca lub nie generuje wyniku operacji.

Można zignorować konwencję, gdy zdarzenie, klasa bazowa lub kontrakt interfejsu sugeruje inną nazwę. Na przykład nie należy zmieniać nazw często używanych procedur obsługi zdarzeń, takich jak `Button1_Click`.

## <a name="BKMK_RelatedTopics"></a>Tematy pokrewne i przykłady (Visual Studio)

|Tytuł|Opis|Przykład|
|-----------|-----------------|------------|
|[Przewodnik: uzyskiwanie dostępu do sieci Web za pomocą AsyncC#i Await ()](./walkthrough-accessing-the-web-by-using-async-and-await.md)|Przedstawia, w jaki sposób konwertować synchroniczne rozwiązanie WPF do asynchronicznego rozwiązania WPF. Ta aplikacja pobiera szereg witryn sieci Web.|[Przykład asynchroniczny: uzyskiwanie dostępu do przewodnika dla sieci Web](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Instrukcje: Rozszerzonie procedury asynchronicznej za pomocą Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Dodaje <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> do poprzedniego przewodnika. Użycie `WhenAll` uruchamia wszystkie pliki do pobrania w tym samym czasie.||
|[Instrukcje: równoległe żądania sieci Web za pomocą Async i Await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ilustruje, jak uruchomić kilka zadań w tym samym czasie.|[Przykład Async: równoległe wykonywanie wielu żądań sieci Web](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Asynchroniczne typy zwracane (C#)](./async-return-types.md)|Ilustruje typy zwracane przez metody async i wyjaśnia, kiedy poszczególne typy są odpowiednie.||
|[Przepływ sterowania w programach asynchronicznychC#()](./control-flow-in-async-programs.md)|Śledzi szczegółowo przepływ sterowania w serii wyrażeń await w programie asynchronicznym.|[Przykład asynchroniczny: przepływ sterowania w programach asynchronicznych](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Dostrajanie aplikacji asynchronicznej (C#)](./fine-tuning-your-async-application.md)|Przedstawia, w jaki sposób dodać następujące funkcje do rozwiązania async:<br /><br /> - [Anulowanie zadania asynchronicznego lub listy zadańC#()](./cancel-an-async-task-or-a-list-of-tasks.md)<br />- [Anulowanie zadań asynchronicznych po upływie czasu (C#)](./cancel-async-tasks-after-a-period-of-time.md)<br />- [Anuluj pozostałe zadania asynchroniczne po zakończeniu jednegoC#()](./cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [Uruchamianie wielu zadań asynchronicznych i przetwarzanie ich w miarę ichC#ukończenia ()](./start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Próbka asynchroniczna: dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Obsługa współużytkowania wątkowości w aplikacjach asynchronicznychC#()](./handling-reentrancy-in-async-apps.md)|Pokazuje, jak obsługiwać przypadki, w których aktywna operacja asynchroniczna jest uruchamiana ponownie, gdy jest uruchomiona.||
|[WhenAny: mostkowanie między .NET Framework i środowisko wykonawcze systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Pokazuje, jak połączyć typy zadań w .NET Framework i IAsyncOperations w środowisko wykonawcze systemu Windows, aby można było użyć <xref:System.Threading.Tasks.Task.WhenAny%2A> z metodą środowisko wykonawcze systemu Windows.|[Próbka asynchroniczna: mostkowanie między programami .NET i środowisko wykonawcze systemu Windows (AsTask i WhenAny)](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|
|Anulowanie asynchroniczne: łączenie platformy .NET Framework ze środowiskiem wykonawczym systemu Windows|Pokazuje, jak połączyć typy zadań w .NET Framework i IAsyncOperations w środowisko wykonawcze systemu Windows, aby można było użyć <xref:System.Threading.CancellationTokenSource> z metodą środowisko wykonawcze systemu Windows.|[Próbka asynchroniczna: mostkowanie między programami .NET i środowisko wykonawcze systemu Windows (anulowanie & AsTask)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Używanie Async na potrzeby dostępu doC#plików ()](./using-async-for-file-access.md)|Wyświetla listę korzyści wynikających ze stosowania słów kluczowych async i await przy uzyskiwaniu dostępu do plików.||
|[Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Opisano nowy wzorzec asynchronii w .NET Framework. Wzorzec jest oparty na typach <xref:System.Threading.Tasks.Task> i <xref:System.Threading.Tasks.Task%601>.||
|[Asynchroniczne wideo w kanale 9](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|Oferuje łącza do różnych plików wideo dotyczących programowania asynchronicznego.||

## <a name="BKMK_CompleteExample"></a>Pełny przykład

Poniższy kod jest plikiem *MainWindow.XAML.cs* z aplikacji WPF, którą omówiono w tym artykule. Możesz pobrać przykład z przykładu [asynchronicznego: przykład z "programowania asynchronicznego z Async i await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs/).

[!code-csharp[async](~/samples/async/async-and-await/cs/MainWindow.xaml.cs)]

## <a name="see-also"></a>Zobacz także

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Programowanie asynchroniczne](../../../async.md)
- [Przegląd Async](../../../../standard/async.md)
