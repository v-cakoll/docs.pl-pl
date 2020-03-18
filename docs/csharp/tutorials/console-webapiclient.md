---
title: Tworzenie klienta REST przy użyciu programu .NET Core
description: W tym samouczku nauczy Cię wiele funkcji w .NET Core i języku C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 5796df2d2fd8c4d9aaca783d720448c90858c067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156860"
---
# <a name="rest-client"></a>Klient REST

W tym samouczku nauczy Cię wiele funkcji w .NET Core i języku C#. Dowiesz się:

* Podstawy cli.NET Core CLI.
* An overview of C# Language features.
* Zarządzanie zależnościami za pomocą NuGet
* Komunikacja HTTP
* Przetwarzanie informacji JSON
* Zarządzanie konfiguracją za pomocą atrybutów.

Stworzysz aplikację, która wystawia żądania HTTP do usługi REST w usłudze GitHub. Będziesz czytać informacje w formacie JSON i konwertować ten pakiet JSON do obiektów C#. Na koniec zobaczysz, jak pracować z obiektami Języka C#.

Istnieje wiele funkcji w tym samouczku. Budujmy je jeden po drugim.

Jeśli wolisz śledzić wraz z [końcowego przykładu](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) dla tego tematu, można go pobrać. Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować komputer do uruchamiania rdzenia .NET. Instrukcje instalacji można znaleźć na stronie [pobierania .NET Core.](https://dotnet.microsoft.com/download) Tę aplikację można uruchomić w systemie Windows, Linux, macOS lub w kontenerze platformy Docker.
Musisz zainstalować swój ulubiony edytor kodu. Poniższe opisy używają [kodu Visual Studio](https://code.visualstudio.com/), który jest edytorem open source, między platformami. Możesz jednak użyć dowolnych narzędzi, które Ci się podobają.

## <a name="create-the-application"></a>Tworzenie aplikacji

Pierwszym krokiem jest utworzenie nowej aplikacji. Otwórz wiersz polecenia i utwórz nowy katalog dla aplikacji. Upewnij się, że bieżący katalog. W oknie konsoli wprowadź następujące polecenie:

```dotnetcli
dotnet new console --name WebApiClient
```

Spowoduje to utworzenie plików startowych dla podstawowej aplikacji "Hello World". Nazwa projektu to "WebApiClient". Ponieważ jest to nowy projekt, żadna z zależności nie są na miejscu. Pierwsze uruchomienie spowoduje pobranie struktury .NET Core, zainstalowanie certyfikatu dewelopera i uruchomienie Menedżera pakietów NuGet w celu przywrócenia brakujących zależności.

Przed rozpoczęciem wprowadzania modyfikacji wpisz `dotnet run` [(patrz uwaga)](#dotnet-restore-note)w wierszu polecenia, aby uruchomić aplikację. `dotnet run`automatycznie wykonuje, `dotnet restore` jeśli w środowisku brakuje zależności. Wykonuje `dotnet build` również, jeśli aplikacja musi zostać przebudowany.
Po wstępnej konfiguracji należy tylko `dotnet restore` uruchomić `dotnet build` lub gdy ma to sens dla projektu.

## <a name="adding-new-dependencies"></a>Dodawanie nowych zależności

Jednym z kluczowych celów projektowych programu .NET Core jest zminimalizowanie rozmiaru instalacji .NET. Jeśli aplikacja wymaga dodatkowych bibliotek dla niektórych swoich funkcji, należy dodać te\*zależności do pliku projektu C# (csproj). W naszym przykładzie musisz dodać `System.Runtime.Serialization.Json` pakiet, aby aplikacja mogła przetwarzać odpowiedzi JSON.

Potrzebny pakiet `System.Runtime.Serialization.Json` dla tej aplikacji. Dodaj go do projektu, uruchamiając następujące polecenie [.NET CLI:](../../core/tools/dotnet-add-package.md)

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a>Składanie żądań internetowych

Teraz możesz rozpocząć pobieranie danych z sieci Web. W tej aplikacji będziesz czytać informacje z [interfejsu API GitHub](https://developer.github.com/v3/). Przeczytajmy informacje o projektach w ramach parasola [.NET Foundation.](https://www.dotnetfoundation.org/) Rozpoczniesz od złożenia żądania do interfejsu API usługi GitHub w celu pobrania informacji o projektach. Punkt końcowy, którego użyjesz, to: <https://api.github.com/orgs/dotnet/repos>. Chcesz pobrać wszystkie informacje o tych projektach, więc użyjesz żądania HTTP GET.
Przeglądarka korzysta również z żądań HTTP GET, dzięki czemu można wkleić ten adres URL do przeglądarki, aby zobaczyć, jakie informacje będziesz otrzymywać i przetwarzać.

Klasa służy <xref:System.Net.Http.HttpClient> do tworzenia żądań sieci web. Podobnie jak wszystkie nowoczesne <xref:System.Net.Http.HttpClient> interfejsy API .NET obsługuje tylko metody asynchroniczne dla jego długotrwałych interfejsów API.
Zacznij od metody asynchronicznej. Będziesz wypełnić implementacji podczas tworzenia funkcji aplikacji. Rozpocznij `program.cs` od otwarcia pliku w katalogu projektu `Program` i dodania następującej metody do klasy:

```csharp
private static async Task ProcessRepositories()
{
}
```

Należy dodać dyrektywy `using` w górnej części `Main` metody, tak aby kompilator C# rozpoznaje <xref:System.Threading.Tasks.Task> typ:

```csharp
using System.Threading.Tasks;
```

Jeśli tworzysz projekt w tym momencie, otrzymasz ostrzeżenie wygenerowane dla tej metody, ponieważ nie zawiera żadnych `await` operatorów i będzie działać synchronicznie. Ignoruj to na razie; operatory dodasz `await` podczas wypełniania metody.

Następnie zmień nazwę obszaru nazw zdefiniowanego `namespace` w instrukcji `ConsoleApp` `WebAPIClient`z domyślnej wartości do . Później zdefiniujemy `repo` klasę w tym obszarze nazw.

Następnie zaktualizuj `Main` metodę wywołania tej metody. Metoda `ProcessRepositories` zwraca zadanie i nie należy zamykać programu przed zakończeniem tego zadania. W związku z tym `Main`należy zmienić podpis . Dodaj `async` modyfikator i zmień `Task`typ powrotu na . Następnie w treści metody dodaj wywołanie `ProcessRepositories`do . Dodaj `await` słowo kluczowe do tego wywołania metody:

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

Teraz masz program, który nic nie robi, ale robi to asynchronicznie. Poprawmy to.

Najpierw potrzebny jest obiekt, który jest w stanie pobrać dane z sieci Web; można użyć, <xref:System.Net.Http.HttpClient> aby to zrobić. Ten obiekt obsługuje żądania i odpowiedzi. Wystąpienia pojedynczego wystąpienia tego typu w `Program` klasie wewnątrz pliku *Program.cs.*

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static async Task Main(string[] args)
        {
            //...
        }
    }
}
```

Wróćmy do `ProcessRepositories` metody i wypełnijmy jej pierwszą wersję:

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

Musisz również dodać dwie nowe `using` dyrektywy w górnej części pliku, aby to skompilować:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Ta pierwsza wersja sprawia, że żądanie sieci Web do odczytu listy wszystkich repozytoriów w organizacji fundacji dotnet. (Identyfikator gitHub dla .NET Foundation to "dotnet"). Kilka pierwszych wierszy <xref:System.Net.Http.HttpClient> skonfigurować dla tego żądania. Po pierwsze jest skonfigurowany do akceptowania odpowiedzi JSON GitHub.
Ten format jest po prostu JSON. Następny wiersz dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu. Te dwa nagłówki są sprawdzane przez kod serwera GitHub i są niezbędne do pobierania informacji z usługi GitHub.

Po skonfigurowaniu <xref:System.Net.Http.HttpClient>żądania sieci Web i pobrania odpowiedzi. W tej pierwszej wersji <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> należy użyć metody wygody. Ta metoda wygody uruchamia zadanie, które sprawia, że żądanie sieci web, a następnie po zwróceniu żądania odczytuje strumień odpowiedzi i wyodrębnia zawartość ze strumienia. Treść odpowiedzi jest zwracana jako <xref:System.String>. Ciąg jest dostępny po zakończeniu zadania.

Ostatnie dwa wiersze tej metody czekają na to zadanie, a następnie wydrukuj odpowiedź do konsoli.
Skompiluj aplikację i uruchom ją. Ostrzeżenie kompilacji już nie `ProcessRepositories` ma, ponieważ `await` teraz zawiera operator. Zobaczysz długi wyświetlacz tekstu sformatowanego przez JSON.

## <a name="processing-the-json-result"></a>Przetwarzanie wyniku JSON

W tym momencie został napisany kod, aby pobrać odpowiedź z serwera sieci web i wyświetlić tekst, który jest zawarty w tej odpowiedzi. Następnie przekonwertujmy tę odpowiedź JSON na obiekty Języka C#.

Klasa <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> serializuje obiekty do JSON i deserializuje JSON do obiektów. Rozpocznij od zdefiniowania klasy do reprezentowania `repo` obiektu JSON zwróconego z interfejsu API GitHub:

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; }
    }
}
```

Umieść powyższy kod w nowym pliku o nazwie 'repo.cs'. Ta wersja klasy reprezentuje najprostszą ścieżkę do przetwarzania danych JSON. Nazwa klasy i nazwa elementu członkowskiego są zgodne z nazwami używanymi w pakiecie JSON, zamiast przestrzegać konwencji Języka C#. Naprawisz to, podając niektóre atrybuty konfiguracji później. Ta klasa pokazuje inną ważną cechą serializacji JSON i deserializacji: Nie wszystkie pola w pakiecie JSON są częścią tej klasy.
Serializator JSON zignoruje informacje, które nie są uwzględnione w typie klasy używane.
Ta funkcja ułatwia tworzenie typów, które działają tylko z podzbiorem pól w pakiecie JSON.

Teraz, gdy został utworzony typ, niech deserialize go.

Następnie użyjesz serializatora do konwersji JSON na obiekty Języka C#. Zastąp <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> wywołanie w metodzie `ProcessRepositories` następującymi trzema wierszami:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

Używasz nowego obszaru nazw, więc musisz dodać go również w górnej części pliku:

```csharp
using System.Text.Json;
```

Zwróć uwagę, że <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> używasz <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>teraz zamiast . Serializator używa strumienia zamiast ciągu jako źródła. Wyjaśnijmy kilka funkcji języka C#, które są używane w drugim wierszu poprzedniego fragmentu kodu. Pierwszy argument <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> jest `await` wyrażeniem. (Pozostałe dwa parametry są opcjonalne i są pomijane we fragmencie kodu). Await wyrażenia mogą pojawić się prawie w dowolnym miejscu w kodzie, nawet jeśli do tej pory, widziałeś je tylko jako część instrukcji przypisania. Metoda `Deserialize` jest *ogólna*, co oznacza, że należy podać argumenty typu dla jakiego rodzaju obiektów powinny być tworzone z tekstu JSON. W tym przykładzie deserializing do `List<Repository>`, który jest inny <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>obiekt ogólny, . Klasa `List<>` przechowuje kolekcję obiektów. Argument typu deklaruje typ obiektów przechowywanych `List<>`w pliku . Tekst JSON reprezentuje kolekcję obiektów repo, więc `Repository`argument typu jest .

Prawie skończyłeś z tą sekcją. Teraz, gdy zostały przekonwertowane JSON do C# obiektów, niech wyświetlić nazwę każdego repozytorium. Zamień wiersze, które brzmią:

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

z następującymi:

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

Skompiluj i uruchom aplikację. Spowoduje to wydrukowanie nazw repozytoriów, które są częścią .NET Foundation.

## <a name="controlling-serialization"></a>Kontrolowanie serializacji

Przed dodaniem więcej funkcji, niech adres `name` `[JsonPropertyName]` właściwości przy użyciu atrybutu. Wprowadzić następujące zmiany w deklaracji `name` pola w repo.cs:

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

Aby `[JsonPropertyName]` użyć atrybutu, należy <xref:System.Text.Json.Serialization> dodać obszar `using` nazw do dyrektyw:

```csharp
using System.Text.Json.Serialization;
```

Ta zmiana oznacza, że musisz zmienić kod, który zapisuje nazwę każdego repozytorium w program.cs:

```csharp
Console.WriteLine(repo.Name);
```

Wykonaj, `dotnet run` aby upewnić się, że mapowania są poprawne. Powinien zostać wyświetlony te same dane wyjściowe, jak poprzednio.

Przed dodaniem nowych funkcji dokonajmy jeszcze jednej zmiany. Metoda `ProcessRepositories` może wykonać pracę asynchronicznej i zwrócić kolekcję repozytoriów. Wróćmy `List<Repository>` z tej metody i przenieść kod, który zapisuje `Main` informacje do metody.

Zmień `ProcessRepositories` podpis, aby zwrócić zadanie, którego `Repository` wynikiem jest lista obiektów:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Następnie po prostu zwróć repozytoria po przetworzeniu odpowiedzi JSON:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

Kompilator generuje `Task<T>` obiekt dla zwracania, ponieważ oznaczono tę metodę jako `async`.
Następnie zmodyfikujmy `Main` metodę, aby przechwytywać te wyniki i zapisywać każdą nazwę repozytorium w konsoli. Twoja `Main` metoda wygląda teraz następująco:

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a>Czytanie więcej informacji

Zakończmy to, przetwarzając kilka więcej właściwości w pakiecie JSON, który jest wysyłany z interfejsu API GitHub. Nie będzie chciał chwycić wszystko, ale dodanie kilku właściwości zademonstruje kilka funkcji języka C#.

Zacznijmy od dodania kilku bardziej prostych `Repository` typów do definicji klasy. Dodaj te właściwości do tej klasy:

```csharp
[JsonPropertyName("description")]
public string Description { get; set; }

[JsonPropertyName("html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName("homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName("watchers")]
public int Watchers { get; set; }
```

Te właściwości mają wbudowane konwersje z typu ciągu (który jest to, co pakiety JSON zawierają) do typu docelowego. Typ <xref:System.Uri> może być dla Ciebie nowy. Reprezentuje identyfikator URI lub w tym przypadku adres URL. W przypadku `Uri` i `int` typów, jeśli pakiet JSON zawiera dane, które nie konwertuje do typu docelowego, akcja serializacji spowoduje wyjątek.

Po dodaniu tych zaktualizuj `Main` metodę, aby wyświetlić te elementy:

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```

Ostatnim krokiem jest dodawanie informacji dotyczących ostatniej operacji wypychania. Informacje te są sformatowane w ten sposób w odpowiedzi JSON:

```json
2016-02-08T21:27:00Z
```

Ten format nie jest zgodny ze <xref:System.DateTime> standardowymi formatami .NET. Z tego powodu musisz napisać niestandardową metodę konwersji. Prawdopodobnie również nie chcesz, aby ciąg raw uwidocznił użytkowników `Repository` klasy. Atrybuty mogą pomóc kontrolować, że również. `public` Najpierw zdefiniuj właściwość, która będzie przechowywać `Repository` reprezentację `LastPush` `readonly` ciągu daty i godziny w klasie oraz właściwość, która zwraca sformatowany ciąg reprezentujący zwróconą datę:

```csharp
[JsonPropertyName("pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

Przejdźmy do nowych konstrukcji, które właśnie zdefiniowaliśmy. Właściwość `LastPush` jest zdefiniowana przy użyciu elementu `get` *członkowskiego zabudowane wyrażenie* dla akcesora. Nie ma `set` akcesora. Pominięcie akcesorjest `set` jak zdefiniować właściwość tylko do *odczytu* w języku C#. (Tak, można utworzyć właściwości tylko do *zapisu* w języku C#, ale ich wartość jest ograniczona). Metoda <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> analizuje ciąg i tworzy <xref:System.DateTime> obiekt przy użyciu formatu podanych dat `DateTime` i `CultureInfo` dodaje dodatkowe metadane do przy użyciu obiektu. Jeśli operacja analizy nie powiedzie się, akcesor właściwości zgłasza wyjątek.

Aby <xref:System.Globalization.CultureInfo.InvariantCulture>użyć , należy dodać <xref:System.Globalization> obszar nazw `using` do `repo.cs`dyrektyw w :

```csharp
using System.Globalization;
```

Na koniec dodaj jeszcze jedną instrukcję danych wyjściowych w konsoli i możesz ponownie utworzyć i uruchomić tę aplikację:

```csharp
Console.WriteLine(repo.LastPush);
```

Twoja wersja powinna teraz odpowiadać [gotowej próbce](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).

## <a name="conclusion"></a>Podsumowanie

W tym samouczku pokazano, jak tworzyć żądania sieci Web, analizować wynik i wyświetlać właściwości tych wyników. Dodano również nowe pakiety jako zależności w projekcie. Widzieliście niektóre funkcje języka C#, które obsługują techniki obiektowe.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
