---
title: Asynchroniczny model programowania zadania (TAP) z asynchroniczną synchronizacją i oczekiwaniem (C#)
ms.date: 05/22/2017
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
ms.openlocfilehash: 2700f5bfaa2746c1ea6f4862bee3af60cf83d693
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78848985"
---
# <a name="task-asynchronous-programming-model"></a>Model programowania asynchronicznego zadań (APM)

Możesz uniknąć problemów z wydajnością i poprawić ogólny czas odpowiedzi aplikacji, stosując programowanie asynchroniczne. Jednak tradycyjne techniki pisania aplikacji asynchronicznych mogą być skomplikowane, przez co trudne do pisania, debugowania i konserwacji.

[C# 5](../../../whats-new/csharp-version-history.md#c-version-50) wprowadzono uproszczone podejście, programowanie asynchroniczne, które wykorzystuje asynchroniczną obsługę w .NET Framework 4.5 i nowszych, .NET Core i Środowiska uruchomieniowego systemu Windows. Kompilator wykonuje trudną pracę, którą kiedyś wykonywał programista, a aplikacja zachowuje strukturę logiczną przypominającą kod synchroniczny. W efekcie masz wszystkie korzyści wynikające z programowania asynchronicznego przy ułamkowym nakładzie pracy.

Ten temat zawiera omówienie, kiedy i jak stosować programowanie async oraz zawiera łącza do tematów zawierających szczegółowe informacje oraz przykłady.

## <a name="BKMK_WhentoUseAsynchrony"></a>Async poprawia czas reakcji

Asynchrony jest niezbędna dla działań, które potencjalnie blokują, takich jak dostęp do sieci Web. Dostęp do zasobów sieci Web bywa powolny lub opóźniony. Jeśli takie działanie jest zablokowane w procesie synchronicznym, cała aplikacja musi poczekać. W procesie asynchronicznym aplikacja może kontynuować wykonywanie innych zadań, które nie są zależne od zasobów sieci Web, do momentu zakończeniem zadania mogącego powodować blokowanie.

W poniższej tabeli przedstawiono typowe obszary, w których programowanie asynchroniczne poprawia czas odpowiedzi. Wymienione interfejsy API z .NET i środowiska uruchomieniowego systemu Windows zawierają metody obsługujące programowanie asynchroniczne.

| Obszar aplikacji    | Typy .NET z metodami asynchronicznym     | Typy środowiska uruchomieniowego systemu Windows z metodami asynchronicznym  |
|---------------------|-----------------------------------|-------------------------------------------|
|Web access|<xref:System.Net.Http.HttpClient>|<xref:Windows.Web.Syndication.SyndicationClient>|
|Praca z plikami|<xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|<xref:Windows.Storage.StorageFile>|
|Praca z obrazami||<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|
|Programowanie WCF|[Operacje synchroniczne i asynchroniczne](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)||

Asynchroniczność okazuje się szczególnie cenna w przypadku aplikacji, które mają dostęp do wątku interfejsu użytkownika, ponieważ wszystkie działania związane z interfejsem użytkownika korzystają zazwyczaj z jednego wątku. Jeśli w aplikacji synchronicznej jest zablokowany jakikolwiek proces, zablokowane są wszystkie procesy. Aplikacja przestanie odpowiadać i możesz dojść do wniosku, że uległa awarii, a tymczasem może po prostu być w stanie oczekiwania.

Kiedy używasz metod asynchronicznych, aplikacja dalej odpowiada interfejsowi użytkownika. Możesz przykładowo zmienić rozmiar lub zminimalizować aplikację lub możesz ją zamknąć, jeżeli nie chcesz czekać aż zakończy zadanie.

Podejście async oferuje również odpowiednik automatycznego przejścia do listy opcji do wybrania przy projektowaniu operacji asynchronicznych. Oznacza to, że można korzystać z wszystkich zalet tradycyjnego programowania asynchronicznego, ale przy znacznie mniejszym nakładzie pracy programisty.

## <a name="BKMK_HowtoWriteanAsyncMethod"></a>Metody asynchroniczne są łatwiejsze do napisania

[Async](../../../language-reference/keywords/async.md) i [await](../../../language-reference/operators/await.md) słowa kluczowe w języku C# są sercem programowania asynchronicznego. Za pomocą tych dwóch słów kluczowych, można użyć zasobów w .NET Framework, .NET Core lub Środowiska uruchomieniowego systemu Windows, aby utworzyć metodę asynchroniczną prawie tak łatwo, jak utworzyć metodę synchroniczną. Metody asynchroniczne zdefiniowane przy użyciu `async` słowa kluczowego są określane jako *metody asynchroniczne*.

W poniższym przykładzie przedstawiono metodę async. Prawie wszystko w kodzie powinno wyglądać znajomo.

Na końcu tego tematu można znaleźć kompletny przykładowy plik programu Windows Presentation Foundation (WPF) i pobrać przykład z [przykładu asynchronicznego: Przykład z "Programowanie asynchroniczne z asynchroniczną synchronizacją i oczekiwanie".](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs/)

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

Można dowiedzieć się kilka praktyk z poprzedniego przykładu. Zacznij od podpisu metody. Zawiera `async` modyfikator. Zwracany jest `Task<int>` (Zobacz sekcję "Typy zwracania", aby uzyskać więcej opcji). Nazwa metody kończy `Async`się na . W treści metody `GetStringAsync` zwraca wartość `Task<string>`. Oznacza to, `await` że podczas zadania otrzymasz `string` `urlContents`( ).  Przed oczekiwaniem na zadanie można wykonać pracę, która `string` `GetStringAsync`nie opiera się na from .

Należy zwrócić szczególną uwagę na `await` operatora. Zawiesza `AccessTheWebAsync`;

- `AccessTheWebAsync`nie można kontynuować, dopóki nie `getStringTask` zostanie zakończona.
- Tymczasem kontrola powraca do `AccessTheWebAsync`obiektu wywołującego .
- Formant wznawia w tym miejscu po `getStringTask` zakończeniu.
- Operator `await` następnie pobiera `string` wynik `getStringTask`z .

Instrukcja return określa wynik liczby całkowitej. Wszystkie metody, które `AccessTheWebAsync` oczekują na pobranie wartości długości.

Jeśli `AccessTheWebAsync` nie ma żadnej pracy, która `GetStringAsync` może wykonać między wywołaniem i oczekiwania na jego zakończenie, można uprościć kod, wywołując i oczekując w następującej pojedynczej instrukcji.

```csharp
string urlContents = await client.GetStringAsync("https://docs.microsoft.com/dotnet");
```

Następujące cechy podsumowują, co sprawia, że poprzedni przykład jest metodą asynchroniczną:

- Podpis metody zawiera `async` modyfikator.
- Nazwa metody async kończy się zwyczajowo sufiksem „Async”.
- Zwracany typ może być jednym z następujących:

  - <xref:System.Threading.Tasks.Task%601>jeśli metoda ma instrukcję zwrotu, w `TResult`której operand ma typ .
  - <xref:System.Threading.Tasks.Task>jeśli metoda nie ma return instrukcji lub ma return instrukcji bez operand.
  - `void`jeśli piszesz program obsługi zdarzeń asynchronicznej.
  - Każdy inny typ, `GetAwaiter` który ma metodę (począwszy od Języka C# 7.0).

  Aby uzyskać więcej informacji, zobacz [sekcję Typy i parametry zwracania.](#BKMK_ReturnTypesandParameters)

- Metoda zazwyczaj zawiera co `await` najmniej jedno wyrażenie, które oznacza punkt, w którym metoda nie może kontynuować, dopóki nie zostanie ukończona oczekiwana operacja asynchroniczna. W tym czasie metoda jest zawieszona, a sterowanie powraca do obiektu wywołującego metodę. Następna sekcji tego tematu przedstawia, co się dzieje w punkcie zawieszenia.

W metodzie asynchronicznej używasz podanych słów kluczowych i typów w celu wskazania, co chcesz zrobić, a kompilator zajmie się resztą, w tym śledzeniem tego, co musi się zdarzyć, gdy sterowanie powraca do punktu oczekiwania w metodzie zawieszonej. Niektóre procesy, takie jak pętle i obsługa wyjątków, mogą być trudne do obsłużenia w tradycyjnym kodzie asynchronicznym. W metodzie asynchronicznej wpisujesz te elementy podobnie jak w rozwiązaniu synchronicznym i problem rozwiązany.

Aby uzyskać więcej informacji na temat asynchrony w poprzednich wersjach .NET Framework, zobacz [TPL i tradycyjne programowanie asynchroniczne .NET Framework](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).

## <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a>Co się dzieje w metodzie asynchronicznej

Ważne jest, aby rozumieć programowanie asynchroniczne jako przepływ sterowania od metody do metody. Poniższy diagram prowadzi przez proces:

![Śledzenie programu asynchronicznego](./media/task-asynchronous-programming-model/navigation-trace-async-program.png "Śledzenie nawigacji")

Liczby na diagramie odpowiadają następującym krokom zainicjowanym po kliknięciu przycisku "start" przez użytkownika.

1. Obsługa zdarzeń wywołuje i `AccessTheWebAsync` oczekuje na metodę asynchronii.

2. `AccessTheWebAsync`tworzy <xref:System.Net.Http.HttpClient> wystąpienie i <xref:System.Net.Http.HttpClient.GetStringAsync%2A> wywołuje metodę asynchroniczną, aby pobrać zawartość witryny sieci Web jako ciąg.

3. Coś się `GetStringAsync` dzieje w tym zawiesza jego postęp. Być może metoda musi czekać na pobranie strony internetowej lub inne działanie blokujące. Aby uniknąć blokowania `GetStringAsync` zasobów, daje kontrolę do jego obiektu wywołującego, `AccessTheWebAsync`.

     `GetStringAsync`zwraca <xref:System.Threading.Tasks.Task%601>, `TResult` gdzie jest ciągiem i `AccessTheWebAsync` przypisuje `getStringTask` zadanie do zmiennej. Zadanie reprezentuje trwający proces dla wywołania `GetStringAsync`, z zobowiązaniem do uzyskania rzeczywistej wartości ciągu po zakończeniu pracy.

4. Ponieważ `getStringTask` nie został jeszcze oczekiwany, `AccessTheWebAsync` można kontynuować inne prace, które nie `GetStringAsync`zależy od ostatecznego wyniku z . Ta praca jest reprezentowana przez wywołanie `DoIndependentWork`metody synchronicznej .

5. `DoIndependentWork`jest metodą synchroniczną, która wykonuje swoją pracę i powraca do obiektu wywołującego.

6. `AccessTheWebAsync`zabrakło pracy, że może obejść się `getStringTask`bez wyniku z . `AccessTheWebAsync`Następnie chce obliczyć i zwrócić długość pobranego ciągu, ale metoda nie może obliczyć tej wartości, dopóki metoda nie ma ciągu.

     W `AccessTheWebAsync` związku z tym używa await operatora zawiesić jego `AccessTheWebAsync`postęp i udawać kontrolę do metody, która o nazwie . `AccessTheWebAsync`zwraca `Task<int>` do obiektu wywołującego. Zadanie przedstawia obietnicę utworzenia w wyniku liczby całkowitej, która jest długością pobranego ciągu.

    > [!NOTE]
    > Jeśli `GetStringAsync` (i `getStringTask`w związku `AccessTheWebAsync` z tym) zakończy `AccessTheWebAsync`się przed czeka, kontrola pozostaje w . Koszt zawieszenia, a następnie powrotu do `AccessTheWebAsync` będzie zmarnowany, jeśli wywołany proces asynchroniczny (`getStringTask`) został już zakończony i `AccessTheWebAsync` nie musi czekać na wynik końcowy.

     Przetwarzanie wzorca jest kontynuowane wewnątrz elementu wywołującego (programu obsługi zdarzeń w tym przykładzie). Obiekt wywołujący może wykonać inną pracę, która `AccessTheWebAsync` nie zależy od wyniku przed oczekiwaniem na ten wynik lub obiekt wywołujący może oczekiwać natychmiast.   Program obsługi zdarzeń `AccessTheWebAsync`oczekuje `AccessTheWebAsync` na `GetStringAsync`, i oczekuje na .

7. `GetStringAsync`uzupełnia i daje wynik ciągu. Wynik ciągu nie jest zwracany przez `GetStringAsync` wywołanie w sposób, który można oczekiwać. (Należy pamiętać, że metoda zwróciła już zadanie w kroku 3).) Zamiast tego wynik ciągu jest przechowywany w zadaniu, które `getStringTask`reprezentuje zakończenie metody. Operator await pobiera wynik `getStringTask`z . Instrukcja przypisania przypisuje pobrany `urlContents`wynik do .

8. Gdy `AccessTheWebAsync` ma wynik ciągu, metoda może obliczyć długość ciągu. Następnie praca `AccessTheWebAsync` jest również zakończona, a program obsługi zdarzeń oczekiwania można wznowić. W pełnym przykładzie na końcu tematu można zobaczyć, że program obsługi zdarzeń pobiera i drukuje wynikową wartość długości.
Jeśli dopiero zaczynasz przygodę z programowaniem asynchronicznym, zastanów się przez chwilę, jaka jest różnica między zachowaniem synchronicznym i asynchronicznym. Metoda synchroniczna kończy działanie, gdy praca jest zakończona (krok 5), natomiast metoda asynchroniczna zwraca wartość zadania, gdy jej praca jest zawieszona (kroki 3 i 6). Gdy metoda async ukończy pracę, zadanie jest oznaczane jako ukończone, a wynik, o ile istnieje, jest zapisywany w zadaniu.

Aby uzyskać więcej informacji na temat przepływu sterowania, zobacz [Przepływ sterowania w programach asynchronicznych (C#)](control-flow-in-async-programs.md).

## <a name="BKMK_APIAsyncMethods"></a>Metody asynchroniczne interfejsu API

Możesz się zastanawiać, gdzie znaleźć `GetStringAsync` metody, takie jak te obsługują programowanie asynchroniczne. .NET Framework 4.5 lub nowsze i .NET `async` `await`Core zawiera wiele elementów członkowskich, które współpracują z i . Można je rozpoznać za pomocą sufiksu "Async", który jest dołączony do <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>nazwy elementu członkowskiego i przez ich typ zwracany lub . Na przykład `System.IO.Stream` klasa zawiera metody <xref:System.IO.Stream.CopyToAsync%2A>takie <xref:System.IO.Stream.ReadAsync%2A>jak <xref:System.IO.Stream.WriteAsync%2A> , , i obok <xref:System.IO.Stream.CopyTo%2A> <xref:System.IO.Stream.Read%2A>metod <xref:System.IO.Stream.Write%2A>synchronicznych , i .

Środowisko uruchomieniowe systemu Windows zawiera również `async` wiele `await` metod, których można używać z aplikacjami systemu Windows i w nich. Aby uzyskać więcej informacji, zobacz [Wątkowość i programowanie asynchroniczne](/windows/uwp/threading-async/) dla tworzenia środowiska windows i [programowania asynchronicznego (aplikacje ze Sklepu Windows)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) i [Szybki start: Wywoływanie asynchronicznych interfejsów API w języku C# lub Visual Basic,](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10)) jeśli używasz wcześniejszych wersji środowiska uruchomieniowego systemu Windows.

## <a name="BKMK_Threads"></a>Wątków

Metody async mają być operacjami niepowodującymi blokowania. Wyrażenie `await` w metodzie asynchronicznej nie blokuje bieżącego wątku, gdy uruchomione jest oczekiwane zadanie. Zamiast tego, wyrażenie rejestruje pozostałą część metody jako kontynuację i przekazuje sterowanie do obiektu wywołującego metody async.

Słowa `async` `await` kluczowe i nie powodują tworzenia dodatkowych wątków. Metody komunikacji async nie wymagają wielowątkowości, ponieważ nie działają we własnym wątku. Metoda działa w bieżącym kontekście synchronizacji i używa czasu wątku, tylko wtedy, gdy jest aktywna. Można użyć <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> do przeniesienia pracy związanej z procesorem CPU do wątku w tle, ale wątek w tle nie pomaga w procesie, który tylko czeka na wyniki stają się dostępne.

Podejście async do programowania asynchronicznego jest preferowane prawie w każdym przypadku. W szczególności takie podejście jest <xref:System.ComponentModel.BackgroundWorker> lepsze niż klasa dla operacji związanych we/wy, ponieważ kod jest prostszy i nie trzeba chronić przed warunkami wyścigu. W połączeniu <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> z metodą programowania asynchronicznego jest lepszy niż <xref:System.ComponentModel.BackgroundWorker> dla operacji związanych z procesorem CPU, `Task.Run` ponieważ programowanie asynchroniczne oddziela szczegóły koordynacji uruchamiania kodu z pracy, która przenosi się do puli wątków.

## <a name="BKMK_AsyncandAwait"></a>async i czekają

Jeśli określisz, że metoda jest metodą asynchroniczną przy użyciu modyfikatora [asynchronii,](../../../language-reference/keywords/async.md) należy włączyć następujące dwie możliwości.

- Oznaczona metoda asynchroniczna może być używana [w](../../../language-reference/operators/await.md) celu wyznaczenia punktów zawieszenia. Operator `await` informuje kompilator, że metoda asynchroniczna nie może kontynuować przeszłości tego punktu, dopóki oczekiwany proces asynchroniczny nie zostanie zakończony. W międzyczasie sterowanie powraca do obiektu wywołującego metodę async.

     Zawieszenie metody asynchronicznej `await` w wyrażeniu nie stanowi wyjścia `finally` z metody i bloki nie są uruchamiane.

- Metoda oznaczona jako async sama może być oczekiwana przez metody, które ją wywołują.

Metoda asynchroniczna zazwyczaj zawiera co `await` najmniej jedno wystąpienie `await` operatora, ale brak wyrażeń nie powoduje błędu kompilatora. Jeśli metoda asynchroniczna `await` nie używa operatora do oznaczania punktu zawieszenia, metoda jest wykonywana jako metoda synchroniczna, pomimo modyfikatora. `async` Kompilator generuje ostrzeżenia dla takich metod.

`async`i `await` są słowami kluczowymi kontekstowych. Aby uzyskać więcej informacji i przykładów, zobacz następujący temat:

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)

## <a name="BKMK_ReturnTypesandParameters"></a>Typy i parametry zwrotu

Metoda asynchroniczna <xref:System.Threading.Tasks.Task> zazwyczaj <xref:System.Threading.Tasks.Task%601>zwraca wartość a lub . Wewnątrz metody asynchronicznej `await` operator jest stosowany do zadania, które jest zwracane z wywołania do innej metody asynchronicznej.

Jako <xref:System.Threading.Tasks.Task%601> typ zwracany można określić [`return`](../../../language-reference/keywords/return.md) jako typ zwracany, jeśli `TResult`metoda zawiera instrukcję określającą argument typu .

Należy <xref:System.Threading.Tasks.Task> użyć jako typ zwracany, jeśli metoda nie ma return instrukcji lub ma return instrukcji, która nie zwraca operand.

Począwszy od języka C# 7.0, można również określić dowolny `GetAwaiter` inny typ zwracany, pod warunkiem, że typ zawiera metodę. <xref:System.Threading.Tasks.ValueTask%601>jest przykładem takiego typu. Jest on dostępny w [pakiecie System.Threading.Tasks.Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet.

W poniższym przykładzie pokazano, jak deklarujesz <xref:System.Threading.Tasks.Task>i wywoływasz metodę, która zwraca wartość: <xref:System.Threading.Tasks.Task%601>

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

Metoda asynchroniczna `void` może również mieć typ zwracany. Ten typ zwracany jest używany głównie do `void` definiowania programów obsługi zdarzeń, gdzie wymagany jest typ zwracany. Programy async obsługi zdarzeń często służą jako punkt wejścia dla programów async.

Nie można oczekiwać `void` metody asynchronicznej, która ma typ zwracany, a obiekt wywołujący metodę zwracania pustki nie może przechwycić żadnych wyjątków, które zgłasza metoda.

Metoda asynchroniczna nie może zadeklarować [w](../../../language-reference/keywords/in-parameter-modifier.md), [ref](../../../language-reference/keywords/ref.md) lub [out](../../../language-reference/keywords/out-parameter-modifier.md) parametrów, ale metoda może wywołać metody, które mają takie parametry. Podobnie metoda asynchroniczną nie może zwrócić wartość przez odwołanie, chociaż można wywołać metody z wartościami zwracanymi ref.

Aby uzyskać więcej informacji i przykładów, zobacz [Async Return Types (C#)](./async-return-types.md). Aby uzyskać więcej informacji na temat sposobu wychwytywania wyjątków w metodach asynchronicznej, zobacz [try-catch](../../../language-reference/keywords/try-catch.md).

Asynchroniczne interfejsy API w programowaniu środowiska uruchomieniowego systemu Windows mają jeden z następujących typów zwracanych, które są podobne do zadań:

- <xref:Windows.Foundation.IAsyncOperation%601>, co odpowiada<xref:System.Threading.Tasks.Task%601>
- <xref:Windows.Foundation.IAsyncAction>, co odpowiada<xref:System.Threading.Tasks.Task>
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>

## <a name="BKMK_NamingConvention"></a>Konwencja nazewnictwa

Zgodnie z konwencją metody, które zwracają często oczekiwane `Task` `Task<T>`typy `ValueTask` `ValueTask<T>`(np. , , , ) powinny mieć nazwy, które kończą się na "Async". Metody, które rozpoczynają operację asynchroniczną, ale nie zwracają oczekiwanego typu, nie powinny mieć nazw, które kończą się na "Async", ale mogą zaczynać się od "Begin", "Start" lub innego zlecenia sugerującego, że ta metoda nie zwraca lub nie powoduje odrzucenia wyniku operacji.

Można zignorować konwencję, gdy zdarzenie, klasa bazowa lub kontrakt interfejsu sugeruje inną nazwę. Na przykład nie należy zmieniać nazw typowych `Button1_Click`programów obsługi zdarzeń, takich jak .

## <a name="BKMK_RelatedTopics"></a>Tematy pokrewne i przykłady (Visual Studio)

|Tytuł|Opis|Sample|
|-----------|-----------------|------------|
|[Instruktaż: Uzyskiwanie dostępu do sieci Web przy użyciu asynchronii i oczekiwanie (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)|Przedstawia, w jaki sposób konwertować synchroniczne rozwiązanie WPF do asynchronicznego rozwiązania WPF. Ta aplikacja pobiera szereg witryn sieci Web.|[Przykład asynchronicznej: uzyskiwanie dostępu do instruktażu sieci Web](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|
|[Jak rozszerzyć instruktaż asynchroniczny za pomocą Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Dodaje <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> do poprzedniego instruktaże. Korzystanie z `WhenAll` uruchamia wszystkie pliki do pobrania w tym samym czasie.||
|[Jak tworzyć wiele żądań sieci Web równolegle przy użyciu asynchronii i await (C#)](./how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Ilustruje, jak uruchomić kilka zadań w tym samym czasie.|[Przykład asynchronicznej: wprowadzanie wielu żądań sieci Web równolegle](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|
|[Typy zwrotu asynchronicznego (C#)](./async-return-types.md)|Ilustruje typy zwracane przez metody async i wyjaśnia, kiedy poszczególne typy są odpowiednie.||
|[Przepływ sterowania w programach asynchroniczny (C#)](./control-flow-in-async-programs.md)|Śledzi szczegółowo przepływ sterowania w serii wyrażeń await w programie asynchronicznym.|[Przykład asynchroniczne: sterowanie przepływem w programach asynchroniczowych](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|
|[Dostrajanie aplikacji asynchronicznej (C#)](./fine-tuning-your-async-application.md)|Przedstawia, w jaki sposób dodać następujące funkcje do rozwiązania async:<br /><br /> - [Anulowanie zadania asynchronicznego lub listy zadań (C#)](./cancel-an-async-task-or-a-list-of-tasks.md)<br />- [Anulowanie zadań asynchronicznych po upływie określonego czasu (C#)](./cancel-async-tasks-after-a-period-of-time.md)<br />- [Anulowanie pozostałych zadań asynchronicznych po zakończeniu jednego z nich (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md)<br />- [Uruchom wiele zadań asynchronicznych i przetwarzaj je po ich ukończeniu (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Przykład asynchronii: Dostrajanie aplikacji](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|
|[Obsługa reentrancy w akcjonorach asynchronicznej (C#)](./handling-reentrancy-in-async-apps.md)|Pokazuje, jak obsługiwać przypadki, w których aktywna operacja asynchroniczna jest uruchamiana ponownie podczas jej uruchamiania.||
|[WhenAny: Pomostowanie między platformą .NET Framework a środowiskom uruchomieniowymi systemu Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Pokazuje, jak pomostować między typami zadań w programie .NET Framework i <xref:System.Threading.Tasks.Task.WhenAny%2A> IAsyncOperations w czasie wykonywania systemu Windows, dzięki czemu można używać z metodą środowiska uruchomieniowego systemu Windows.|[Przykład asynchroniczne: pomostowanie między programami .NET i środowiska miowego systemu Windows (AsTask i WhenAny)](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|
|Anulowanie asynchroniczne: łączenie platformy .NET Framework ze środowiskiem wykonawczym systemu Windows|Pokazuje, jak pomostować między typami zadań w programie .NET Framework i <xref:System.Threading.CancellationTokenSource> IAsyncOperations w czasie wykonywania systemu Windows, dzięki czemu można używać z metodą środowiska uruchomieniowego systemu Windows.|[Przykład asynchronii: pomostowanie między programem .NET a programem Windows Runtime (anulowanie & zadania mianotowe)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|
|[Korzystanie z asynchronii dostępu do plików (C#)](./using-async-for-file-access.md)|Wyświetla listę korzyści wynikających ze stosowania słów kluczowych async i await przy uzyskiwaniu dostępu do plików.||
|[Wzorzec asynchroniczny oparty na zadaniach (TAP)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Opisano nowy wzorzec asynchronii w .NET Framework. Wzorzec jest <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601> oparty na i typy.||
|[Filmy asynchroniczne na kanale 9](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|Oferuje łącza do różnych plików wideo dotyczących programowania asynchronicznego.||

## <a name="BKMK_CompleteExample"></a>Kompletny przykład

Poniższy kod jest *plik MainWindow.xaml.cs* z aplikacji WPF, który omówiono w tym artykule. Możesz pobrać przykład z [próbki Async: Przykład z "Programowanie asynchroniczne z Async i Await"](https://docs.microsoft.com/samples/dotnet/samples/async-and-await-cs/).

[!code-csharp[async](~/samples/snippets/standard/async/async-and-await/cs/MainWindow.xaml.cs)]

## <a name="see-also"></a>Zobacz też

- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
- [Programowanie asynchroniczne](../../../async.md)
- [Omówienie asynchronicznej](../../../../standard/async.md)
