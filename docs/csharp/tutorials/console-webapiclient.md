---
title: Tworzenie klienta REST przy użyciu programu .NET Core
description: W tym samouczku uczy się wielu funkcji w języku .NET Core i języku C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 0105db519f7accec6bf8bfbafdc6a67a444b1074
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249171"
---
# <a name="rest-client"></a>Klient REST

W tym samouczku uczy się wielu funkcji w języku .NET Core i języku C#. Dowiesz się:

* Podstawy interfejsu wiersza polecenia .NET Core.
* An overview of C# Language features.
* Zarządzanie zależnościami za pomocą nuget
* Komunikacja HTTP
* Przetwarzanie informacji JSON
* Zarządzanie konfiguracją za pomocą atrybutów.

Będziesz tworzyć aplikację, która wystawia żądania HTTP do usługi REST w usłudze GitHub. Będziesz czytać informacje w formacie JSON i konwertować ten pakiet JSON do obiektów języka C#. Na koniec zobaczysz, jak pracować z obiektami języka C#.

Istnieje wiele funkcji w tym samouczku. Zbudujmy je jeden po drugim.

Jeśli wolisz wykonać wraz z [próbką końcową](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) dla tego tematu, możesz go pobrać. Aby uzyskać instrukcje pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować komputer do uruchamiania .NET core. Instrukcje instalacji można znaleźć na stronie [.NET Core Downloads.](https://dotnet.microsoft.com/download) Tę aplikację można uruchomić w systemach Windows, Linux, macOS lub w kontenerze platformy Docker.
Musisz zainstalować swój ulubiony edytor kodu. Poniższe opisy używają [programu Visual Studio Code](https://code.visualstudio.com/), który jest edytorem open source, międzyplatformowym. Możesz jednak użyć dowolnych narzędzi, z których czujesz się komfortowo.

## <a name="create-the-application"></a>Tworzenie aplikacji

Pierwszym krokiem jest utworzenie nowej aplikacji. Otwórz wiersz polecenia i utwórz nowy katalog dla aplikacji. Spraw, aby był to bieżący katalog. Wprowadź następujące polecenie w oknie konsoli:

```dotnetcli
dotnet new console --name WebApiClient
```

Spowoduje to utworzenie plików startowych dla podstawowej aplikacji "Hello World". Nazwa projektu to "WebApiClient". Ponieważ jest to nowy projekt, żadna z zależności nie są na miejscu. Pierwsze uruchomienie pobierze platformę .NET Core, zainstaluje certyfikat deweloperski i uruchomi menedżera pakietów NuGet, aby przywrócić brakujące zależności.

Przed rozpoczęciem wprowadzania zmian `dotnet run` wpisz[(patrz uwaga)](#dotnet-restore-note)w wierszu polecenia, aby uruchomić aplikację. `dotnet run`automatycznie wykonuje, `dotnet restore` jeśli w środowisku brakuje zależności. Działa `dotnet build` również, jeśli aplikacja musi zostać przebudowana.
Po wstępnej konfiguracji, trzeba będzie `dotnet restore` `dotnet build` tylko uruchomić lub gdy ma to sens dla projektu.

## <a name="adding-new-dependencies"></a>Dodawanie nowych zależności

Jednym z kluczowych celów projektowych dla platformy .NET Core jest zminimalizowanie rozmiaru instalacji platformy .NET. Jeśli aplikacja potrzebuje dodatkowych bibliotek dla niektórych jego funkcji, należy dodać\*te zależności do pliku projektu C# (csproj). W naszym przykładzie należy dodać `System.Runtime.Serialization.Json` pakiet, dzięki czemu aplikacja może przetwarzać odpowiedzi JSON.

Pakiet dla tej `System.Runtime.Serialization.Json` aplikacji jest potrzebny. Dodaj go do projektu, uruchamiając następujące polecenie [.NET CLI:](../../core/tools/dotnet-add-package.md)

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a>Składanie żądań sieci Web

Teraz możesz rozpocząć pobieranie danych z sieci Web. W tej aplikacji przeczytasz informacje z [interfejsu API GitHub](https://developer.github.com/v3/). Przeczytajmy informacje o projektach pod patronatem [.NET Foundation.](https://www.dotnetfoundation.org/) Rozpoczniesz od złożenia żądania do interfejsu API Usługi GitHub, aby pobrać informacje o projektach. Punkt końcowy, którego użyjesz, to: <https://api.github.com/orgs/dotnet/repos>. Chcesz pobrać wszystkie informacje o tych projektach, więc użyjesz żądania HTTP GET.
Twoja przeglądarka korzysta również z żądań HTTP GET, dzięki czemu możesz wkleić ten adres URL do przeglądarki, aby zobaczyć, jakie informacje będziesz otrzymywać i przetwarzać.

Klasy służy <xref:System.Net.Http.HttpClient> do żądania sieci web. Podobnie jak wszystkie nowoczesne interfejsy API platformy .NET, <xref:System.Net.Http.HttpClient> obsługuje tylko metody asynchronii dla jego długotrwałych interfejsów API.
Zacznij od metody asynchronii. Podczas tworzenia funkcji aplikacji zostanie uzupełnina implementacja. Zacznij od `program.cs` otwarcia pliku w katalogu projektu i dodania następującej metody do `Program` klasy:

```csharp
private static async Task ProcessRepositories()
{
}
```

Musisz dodać dyrektywę `using` w górnej części `Main` metody, tak aby kompilator <xref:System.Threading.Tasks.Task> języka C# rozpoznaje typ:

```csharp
using System.Threading.Tasks;
```

Jeśli tworzysz projekt w tym momencie, otrzymasz ostrzeżenie wygenerowane dla tej `await` metody, ponieważ nie zawiera żadnych operatorów i będzie działać synchronicznie. Zignoruj to na razie; dodasz `await` operatory podczas wypełniania metody.

Następnie zmień nazwę obszaru nazw `namespace` zdefiniowanego w `ConsoleApp` instrukcji `WebAPIClient`z domyślnego na . Później zdefiniujemy `repo` klasę w tej przestrzeni nazw.

Następnie zaktualizuj `Main` metodę, aby wywołać tę metodę. Metoda `ProcessRepositories` zwraca zadanie i nie należy kończyć programu przed zakończeniem tego zadania. W związku z tym należy `Main`zmienić podpis . Dodaj `async` modyfikator i zmień typ `Task`zwracany na . Następnie w treści metody dodaj wywołanie `ProcessRepositories`do . Dodaj `await` słowo kluczowe do tego wywołania metody:

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

Teraz masz program, który nic nie robi, ale robi to asynchronicznie. Poprawmy to.

Najpierw potrzebny jest obiekt, który jest w stanie pobrać dane z sieci Web; można użyć <xref:System.Net.Http.HttpClient> a to zrobić. Ten obiekt obsługuje żądanie i odpowiedzi. Tworzenie wystąpienia pojedynczego wystąpienia tego `Program` typu w klasie wewnątrz pliku *Program.cs.*

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

Wróćmy do `ProcessRepositories` metody i wypełnij pierwszą jej wersję:

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

Ta pierwsza wersja sprawia, że żądanie sieci web, aby przeczytać listę wszystkich repozytoriów w organizacji dotnet fundacji. (Identyfikator gitHub dla Fundacji .NET to 'dotnet'). Pierwsze kilka wierszy <xref:System.Net.Http.HttpClient> skonfigurować dla tego żądania. Po pierwsze jest skonfigurowany do akceptowania odpowiedzi JSON GitHub.
Ten format jest po prostu JSON. Następny wiersz dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu. Te dwa nagłówki są sprawdzane przez kod serwera GitHub i są niezbędne do pobierania informacji z usługi GitHub.

Po skonfigurowaniu <xref:System.Net.Http.HttpClient>programu , należy złożyć żądanie sieci Web i pobrać odpowiedź. W tej pierwszej wersji <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> należy użyć metody wygody. Ta metoda wygody uruchamia zadanie, które sprawia, że żądanie sieci web, a następnie po zwróceniu żądania odczytuje strumień odpowiedzi i wyodrębnia zawartość ze strumienia. Treść odpowiedzi jest zwracana <xref:System.String>jako . Ciąg jest dostępny po zakończeniu zadania.

Ostatnie dwa wiersze tej metody czekają na to zadanie, a następnie wydrukuj odpowiedź do konsoli.
Skompiluj aplikację i uruchom ją. Ostrzeżenie kompilacji nie ma `ProcessRepositories` teraz, ponieważ `await` teraz zawiera operatora. Zobaczysz długie wyświetlanie tekstu sformatowanego json.

## <a name="processing-the-json-result"></a>Przetwarzanie wyniku JSON

W tym momencie napisano kod, aby pobrać odpowiedź z serwera sieci web i wyświetlić tekst, który jest zawarty w tej odpowiedzi. Następnie przekonwertujmy tę odpowiedź JSON na obiekty języka C#.

Klasa <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> serializuje obiekty do JSON i deserializes JSON do obiektów. Zacznij od zdefiniowania klasy `repo` reprezentującej obiekt JSON zwrócony z interfejsu API Usługi GitHub:

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

Umieść powyższy kod w nowym pliku o nazwie 'repo.cs'. Ta wersja klasy reprezentuje najprostszą ścieżkę do przetwarzania danych JSON. Nazwa klasy i nazwa elementu członkowskiego są zgodne z nazwami używanymi w pakiecie JSON, zamiast następujących konwencji języka C#. Naprawisz to, podając niektóre atrybuty konfiguracji później. Ta klasa pokazuje inną ważną cechę serializacji JSON i deserializacji: nie wszystkie pola w pakiecie JSON są częścią tej klasy.
Serializator JSON zignoruje informacje, które nie są uwzględnione w typie klasy, który jest używany.
Ta funkcja ułatwia tworzenie typów, które działają tylko z podzbiorem pól w pakiecie JSON.

Teraz, gdy utworzono typ, niech deserialize go.

Następnie użyjesz serializatora do konwersji JSON do obiektów języka C#. Zastąp <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> wywołanie w swojej `ProcessRepositories` metodzie następującymi wierszami:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

Używasz nowej przestrzeni nazw, więc musisz dodać ją również u góry pliku:

```csharp
using System.Text.Json;
```

Zwróć uwagę, że <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> teraz używasz zamiast <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>. Serializator używa strumienia zamiast ciągu jako źródła. Wyjaśnijmy kilka funkcji języka C#, które są używane w drugim wierszu poprzedniego fragmentu kodu. Pierwszym argumentem <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> `await` jest wyrażenie. (Pozostałe dwa parametry są opcjonalne i są pomijane we wpisie kodu). Await wyrażenia mogą pojawić się prawie w dowolnym miejscu w kodzie, nawet jeśli do tej pory, masz tylko widział je jako część instrukcji przypisania. Metoda `Deserialize` jest *ogólna*, co oznacza, że należy podać argumenty typu dla jakiego rodzaju obiektów powinny być tworzone z tekstu JSON. W tym przykładzie deserializacji do `List<Repository>`, który jest inny <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>obiekt ogólny, . Klasa `List<>` przechowuje kolekcję obiektów. Argument typu deklaruje typ obiektów przechowywanych `List<>`w pliku . Tekst JSON reprezentuje zbiór obiektów repozytorium, `Repository`więc argument typu jest .

Jesteś prawie gotowy z tej sekcji. Teraz, gdy zostały przekonwertowane JSON do C# obiektów, wyświetlmy nazwę każdego repozytorium. Zastąp wiersze, które brzmią:

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

z następującymi:

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

Skompiluj i uruchom aplikację. Spowoduje to wydrukowanie nazw repozytoriów, które są częścią fundacji .NET.

## <a name="controlling-serialization"></a>Kontrolowanie serializacji

Przed dodaniem większej liczby funkcji, `name` zajmijmy się właściwości za pomocą atrybutu. `[JsonPropertyName]` W repo.cs w repo.cs wykonuj `name` następujące zmiany:

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

Aby `[JsonPropertyName]` użyć atrybutu, <xref:System.Text.Json.Serialization> należy dodać obszar nazw `using` do dyrektyw:

```csharp
using System.Text.Json.Serialization;
```

Ta zmiana oznacza, że należy zmienić kod, który zapisuje nazwę każdego repozytorium w program.cs:

```csharp
Console.WriteLine(repo.Name);
```

Wykonaj, `dotnet run` aby upewnić się, że masz mapowania poprawne. Powinieneś zobaczyć takie same dane wyjściowe jak poprzednio.

Przed dodaniem nowych funkcji należy wprowadzić jeszcze jedną zmianę. Metoda `ProcessRepositories` może wykonać pracę asynchroniiową i zwrócić kolekcję repozytoriów. Wróćmy `List<Repository>` z tej metody i przenieść kod, który zapisuje informacje do `Main` metody.

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

Kompilator generuje `Task<T>` obiekt dla zwracania, ponieważ ta `async`metoda została oznaczona jako .
Następnie zmodyfikujmy `Main` metodę, tak aby przechwytuje te wyniki i zapisywał każdą nazwę repozytorium w konsoli. Twoja `Main` metoda wygląda teraz następująco:

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a>Czytaj więcej informacji

Zakończmy to, przetwarzając kilka właściwości w pakiecie JSON, który jest wysyłany z interfejsu API Usługi GitHub. Nie chcesz pobrać wszystko, ale dodanie kilku właściwości zademonstruje kilka innych funkcji języka C#.

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

Te właściwości mają wbudowane konwersje z typu ciągu (który jest tym, co zawierają pakiety JSON) do typu docelowego. Typ <xref:System.Uri> może być dla Ciebie nowy. Reprezentuje identyfikator URI lub w tym przypadku adres URL. W przypadku `Uri` i `int` typów, jeśli pakiet JSON zawiera dane, które nie konwertują do typu docelowego, akcja serializacji zgłosi wyjątek.

Po dodaniu tych aktualizacji `Main` metody, aby wyświetlić te elementy:

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

Na koniec dodajmy informacje dotyczące ostatniej operacji wypychania. Te informacje są sformatowane w ten sposób w odpowiedzi JSON:

```json
2016-02-08T21:27:00Z
```

Ten format jest w skoordynowany czas uniwersalny (UTC), <xref:System.DateTime.Kind%2A> więc <xref:System.DateTimeKind.Utc>otrzymasz wartość, <xref:System.DateTime> której właściwość jest . Jeśli wolisz datę reprezentowaną w strefie czasowej, musisz napisać niestandardową metodę konwersji. Najpierw `public` zdefiniuj właściwość, która będzie przechowywać `Repository` reprezentację `LastPush` `readonly` UTC daty i godziny w klasie oraz właściwość, która zwraca datę przekonwertowane na czas lokalny:

```csharp
[JsonPropertyName("pushed_at")]
public DateTime LastPushUtc { get; set; }

public DateTime LastPush => LastPushUtc.ToLocalTime();
```

Przejdźmy do nowych konstrukcji, które właśnie zdefiniowaliśmy. Właściwość `LastPush` jest zdefiniowana przy użyciu elementu *członkowskiego zabudowanego wyrażenia* dla `get` akcesora. Nie ma `set` akcesora. Pomijając `set` akcesor jest jak zdefiniować właściwość *tylko do odczytu* w języku C#. (Tak, można tworzyć właściwości *tylko do zapisu* w języku C#, ale ich wartość jest ograniczona.)

Na koniec dodaj jeszcze jedną instrukcję danych wyjściowych w konsoli i możesz ponownie utworzyć i uruchomić tę aplikację:

```csharp
Console.WriteLine(repo.LastPush);
```

Twoja wersja powinna teraz być zgodna z [gotową próbką](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).

## <a name="conclusion"></a>Podsumowanie

W tym samouczku pokazano, jak tworzyć żądania sieci web, analizować wynik i wyświetlać właściwości tych wyników. Dodano również nowe pakiety jako zależności w projekcie. Widziałeś niektóre funkcje języka C#, które obsługują techniki obiektowe.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
