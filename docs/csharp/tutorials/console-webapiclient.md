---
title: Tworzenie klienta REST przy użyciu platformy .NET Core
description: W tym samouczku przedstawiono szereg funkcji platformy .NET Core i C# języka.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: eb7946d669de60c3469ca8098e40b159082ea270
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76921085"
---
# <a name="rest-client"></a>Klient REST

W tym samouczku przedstawiono szereg funkcji platformy .NET Core i C# języka. Dowiesz się:

* Podstawowe informacje dotyczące interfejs wiersza polecenia platformy .NET Core.
* Omówienie funkcji C# języka.
* Zarządzanie zależnościami przy użyciu narzędzia NuGet
* HTTP Communications
* Przetwarzanie informacji JSON
* Zarządzanie konfiguracją przy użyciu atrybutów.

Utworzysz aplikację, która wystawia żądania HTTP do usługi REST w serwisie GitHub. Informacje są odczytywane w formacie JSON i konwertowane tego pakietu JSON na C# obiekty. Na koniec zobaczysz, jak korzystać z C# obiektów.

Ten samouczek zawiera wiele funkcji. Kompilujmy je po jednej.

Jeśli wolisz postępować wraz z [ostatnim przykładem](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) dla tego tematu, możesz go pobrać. Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

## <a name="prerequisites"></a>Wymagania wstępne

Musisz skonfigurować maszynę do uruchamiania programu .NET Core. Instrukcje instalacji można znaleźć na stronie [pliki do pobrania w programie .NET Core](https://dotnet.microsoft.com/download) . Tę aplikację można uruchomić w systemie Windows, Linux, macOS lub w kontenerze platformy Docker.
Musisz zainstalować swój ulubiony Edytor kodu. Poniższe opisy wykorzystują [Visual Studio Code](https://code.visualstudio.com/), czyli edytor Międzyplatformowy. Można jednak korzystać z dowolnych narzędzi, z którymi masz doświadczenie.

## <a name="create-the-application"></a>Tworzenie aplikacji

Pierwszym krokiem jest utworzenie nowej aplikacji. Otwórz wiersz polecenia i Utwórz nowy katalog dla aplikacji. Upewnij się, że bieżący katalog. W oknie konsoli wprowadź następujące polecenie:

```dotnetcli
dotnet new console --name WebApiClient
```

Spowoduje to utworzenie plików początkowych dla podstawowej aplikacji "Hello world". Nazwa projektu to "WebApiClient". Ponieważ jest to nowy projekt, żadne zależności nie są stosowane. Pierwsze uruchomienie spowoduje pobranie platformy .NET Core, zainstalowanie certyfikatu deweloperskiego i uruchomienie Menedżera pakietów NuGet w celu przywrócenia brakujących zależności.

Przed rozpoczęciem wprowadzania modyfikacji wpisz `dotnet run` ([Zobacz Uwaga](#dotnet-restore-note)) w wierszu polecenia, aby uruchomić aplikację. `dotnet run` automatycznie wykonuje `dotnet restore`, jeśli w środowisku nie ma zależności. Wykonuje również `dotnet build`, jeśli aplikacja musi zostać odbudowana.
Po wstępnej konfiguracji wystarczy uruchomić `dotnet restore` lub `dotnet build`, gdy ma to sens dla projektu.

## <a name="adding-new-dependencies"></a>Dodawanie nowych zależności

Jednym z kluczowych celów projektowych dla platformy .NET Core jest Minimalizacja rozmiaru instalacji programu .NET. Jeśli aplikacja wymaga dodatkowych bibliotek dla niektórych funkcji, należy dodać te zależności do pliku C# projektu (\*. csproj). Na potrzeby tego przykładu należy dodać pakiet `System.Runtime.Serialization.Json`, aby aplikacja mogła przetwarzać odpowiedzi JSON.

Wymagany jest pakiet `System.Runtime.Serialization.Json` dla tej aplikacji. Dodaj go do projektu, uruchamiając następujące polecenie [interfejsu wiersza polecenia platformy .NET](../../core/tools/dotnet-add-package.md) :

```console
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a>Tworzenie żądań sieci Web

Teraz wszystko jest gotowe do rozpoczęcia pobierania danych z sieci Web. W tej aplikacji należy przeczytać informacje z [interfejsu API usługi GitHub](https://developer.github.com/v3/). Zapoznajmy się z informacjami na temat projektów w ramach parasola [.NET Foundation](https://www.dotnetfoundation.org/) . Zacznij od wprowadzenia żądania do interfejsu API usługi GitHub w celu pobrania informacji o projektach. Używany punkt końcowy to: <https://api.github.com/orgs/dotnet/repos>. Chcesz pobrać wszystkie informacje o tych projektach, aby użyć żądania HTTP GET.
Przeglądarka korzysta również z żądań HTTP GET, dlatego można wkleić ten adres URL do przeglądarki, aby zobaczyć, jakie informacje będą odbierane i przetwarzane.

Użyj klasy <xref:System.Net.Http.HttpClient>, aby wykonywać żądania sieci Web. Podobnie jak w przypadku wszystkich nowoczesnych interfejsów API platformy .NET, <xref:System.Net.Http.HttpClient> obsługuje tylko metody asynchroniczne dla długotrwałych interfejsów API.
Zacznij od wprowadzenia metody asynchronicznej. Wdrożenie jest wypełniane podczas tworzenia funkcjonalności aplikacji. Zacznij od otwarcia pliku `program.cs` w katalogu projektu i dodania następującej metody do klasy `Program`:

```csharp
private static async Task ProcessRepositories()
{
}
```

Należy dodać dyrektywę `using` w górnej części metody `Main`, aby C# kompilator rozpoznał <xref:System.Threading.Tasks.Task> typ:

```csharp
using System.Threading.Tasks;
```

W przypadku skompilowania projektu w tym momencie otrzymasz ostrzeżenie wygenerowane dla tej metody, ponieważ nie zawiera ona żadnych operatorów `await` i zostanie uruchomiona synchronicznie. Zignoruj to teraz; podczas wypełniania należy dodać operatory `await`.

Następnie zmień nazwę przestrzeni nazw zdefiniowanej w instrukcji `namespace` z jej domyślnego `ConsoleApp` na `WebAPIClient`. W tej przestrzeni nazw będziemy później definiować klasy `repo`.

Następnie zaktualizuj metodę `Main`, aby wywołać tę metodę. Metoda `ProcessRepositories` zwraca zadanie i nie należy zamykać programu przed zakończeniem tego zadania. W związku z tym należy zmienić sygnaturę `Main`. Dodaj modyfikator `async` i Zmień zwracany typ na `Task`. Następnie w treści metody Dodaj wywołanie do `ProcessRepositories`. Dodaj słowo kluczowe `await` do tego wywołania metody:

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

Teraz masz program, który nic nie robi, ale robi to asynchronicznie. Ulepszamy go.

Najpierw wymagany jest obiekt, który może pobrać dane z sieci Web; Aby to zrobić, możesz użyć <xref:System.Net.Http.HttpClient>. Ten obiekt obsługuje żądanie i odpowiedzi. Utwórz wystąpienie pojedynczego wystąpienia tego typu w klasie `Program` w pliku *program.cs* .

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

Wróćmy do metody `ProcessRepositories` i wypełnimy ją pierwszą wersją:

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

Należy również dodać dwie nowe dyrektywy `using` w górnej części pliku do skompilowania:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Ta pierwsza wersja wysyła żądanie sieci Web w celu odczytania listy wszystkich repozytoriów w ramach organizacji programu dotnet Foundation. (Identyfikator gitHub dla platformy .NET Foundation to "dotnet"). Pierwsze kilka wierszy skonfiguruje <xref:System.Net.Http.HttpClient> dla tego żądania. Najpierw jest skonfigurowany do akceptowania odpowiedzi JSON usługi GitHub.
Ten format jest po prostu kod JSON. Następny wiersz dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu. Te dwa nagłówki są sprawdzane przez kod serwera usługi GitHub i są niezbędne do pobierania informacji z usługi GitHub.

Po skonfigurowaniu <xref:System.Net.Http.HttpClient>należy utworzyć żądanie sieci Web i pobrać odpowiedź. W tej pierwszej wersji jest używana metoda <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> wygodna. Ta wygodna metoda uruchamia zadanie, które wykonuje żądanie sieci Web, a następnie po powrocie żądania odczytuje strumień odpowiedzi i wyodrębnia zawartość ze strumienia. Treść odpowiedzi jest zwracana jako <xref:System.String>. Ten ciąg jest dostępny po zakończeniu zadania.

Ostatnie dwie wiersze tej metody oczekują na zadanie, a następnie drukują odpowiedź do konsoli.
Skompiluj aplikację i uruchom ją. Ostrzeżenie kompilacji teraz znikło, ponieważ `ProcessRepositories` teraz zawiera operator `await`. Zobaczysz długi sposób wyświetlania tekstu sformatowanego w formacie JSON.

## <a name="processing-the-json-result"></a>Przetwarzanie wyniku JSON

W tym momencie napisano kod umożliwiający pobranie odpowiedzi z serwera sieci Web i wyświetlenie tekstu zawartego w tej odpowiedzi. Następnie przekonwertujmy tę odpowiedź JSON na C# obiekty.

Klasa <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> serializować obiekty do formatu JSON i deserializacji kod JSON w obiektach. Zacznij od zdefiniowania klasy, która będzie reprezentować `repo` obiekt JSON zwrócony z interfejsu API usługi GitHub:

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

Umieść powyższy kod w nowym pliku o nazwie "repo. cs". Ta wersja klasy reprezentuje najprostszą ścieżkę do przetwarzania danych JSON. Nazwa klasy i nazwa elementu członkowskiego są zgodne z nazwami użytymi w pakiecie JSON, a C# nie z następującymi konwencjami. Aby naprawić ten problem, należy w późniejszym czasie dostarczyć pewne atrybuty konfiguracyjne. Ta klasa pokazuje kolejną ważną funkcję serializacji i deserializacji kodu JSON: nie wszystkie pola w pakiecie JSON są częścią tej klasy.
Serializator JSON zignoruje informacje, które nie są uwzględnione w używanym typie klasy.
Ta funkcja ułatwia tworzenie typów, które współpracują z tylko podzbiorem pól w pakiecie JSON.

Teraz, po utworzeniu typu, przyjrzyjmy go. 

Następnie użyjesz serializatora, aby przekonwertować kod JSON na C# obiekty. Zastąp wywołanie <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> w metodzie `ProcessRepositories` następującymi trzema wierszami:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

Używasz nowej przestrzeni nazw, więc musisz ją dodać również na początku pliku:

```csharp
using System.Text.Json;
```

Zwróć uwagę, że teraz używasz <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)>, a nie <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>. Serializator używa strumienia zamiast ciągu jako źródła. Wyjaśnimy kilka funkcji C# języka, które są używane w drugim wierszu poprzedniego fragmentu kodu. Pierwszym argumentem <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> jest wyrażenie `await`. (Pozostałe dwa parametry są opcjonalne i pomijane we fragmencie kodu). Wyrażenia await mogą pojawiać się niemal wszędzie w kodzie, nawet w przypadku, gdy tylko do tej pory są widoczne jako część instrukcji przypisania. Metoda `Deserialize` jest *rodzajowa*, co oznacza, że należy podać argumenty typu dla rodzaju obiektów, które mają być tworzone na podstawie tekstu JSON. W tym przykładzie Serializacja jest deserializowana do `List<Repository>`, który jest innym obiektem ogólnym, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>. Klasa `List<>` przechowuje kolekcję obiektów. Argument typu deklaruje typ obiektów przechowywanych w `List<>`. Tekst JSON reprezentuje kolekcję obiektów repozytorium, więc argument typu jest `Repository`.

Prawie gotowe do tej sekcji. Teraz, gdy plik JSON został przekonwertowany C# do obiektów, zostanie wyświetlona nazwa każdego repozytorium. Zastąp odczytane wiersze:

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

należy wykonać następujące czynności:

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

Skompiluj i uruchom aplikację. Spowoduje to wydrukowanie nazw repozytoriów, które są częścią programu .NET Foundation.

## <a name="controlling-serialization"></a>Kontrolowanie serializacji

Zanim dodasz więcej funkcji, przyjrzyjmy się `name` właściwości przy użyciu atrybutu `[JsonPropertyName]`. Wprowadź następujące zmiany w deklaracji pola `name` w repo.cs:

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

Aby użyć `[JsonPropertyName]` atrybutu, należy dodać przestrzeń nazw <xref:System.Text.Json.Serialization> do dyrektyw `using`:

```csharp
using System.Text.Json.Serialization;
```

Ta zmiana oznacza, że należy zmienić kod, który zapisuje nazwę każdego repozytorium w program.cs:

```csharp
Console.WriteLine(repo.Name);
```

Wykonaj `dotnet run`, aby upewnić się, że mapowania są poprawne. Powinny zostać wyświetlone te same dane wyjściowe co poprzednio.

Utwórzmy jeszcze jedną zmianę przed dodaniem nowych funkcji. Metoda `ProcessRepositories` może wykonywać działania asynchroniczne i zwracać kolekcję repozytoriów. Zwróćmy `List<Repository>` z tej metody i przeniesiesz kod, który zapisuje informacje w metodzie `Main`.

Zmień sygnaturę `ProcessRepositories`, aby zwracała zadanie, którego wynikiem jest lista obiektów `Repository`:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Następnie po przetworzeniu odpowiedzi JSON należy zwrócić repozytoria:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

Kompilator generuje obiekt `Task<T>` dla zwracanych, ponieważ oznaczono tę metodę jako `async`.
Następnie Zmodyfikujmy metodę `Main` tak, aby przechwytł te wyniki i zapisywali nazwy poszczególnych repozytoriów w konsoli programu. Teraz Metoda `Main` wygląda następująco:

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a>Odczytywanie dodatkowych informacji

Zakończmy to przez przetwarzanie kilku większej liczby właściwości w pakiecie JSON, które są wysyłane z interfejsu API usługi GitHub. Nie chcesz dowiedzieć się wszystkiego, ale dodanie kilku właściwości spowoduje pokazanie kilku funkcji C# języka.

Zacznijmy od dodania kilku prostych typów do definicji klasy `Repository`. Dodaj te właściwości do tej klasy:

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

Te właściwości mają wbudowane konwersje z typu ciąg (który zawiera pakiety JSON) do typu docelowego. Typ <xref:System.Uri> może być nowy dla Ciebie. Reprezentuje identyfikator URI lub w tym przypadku adres URL. W przypadku typów `Uri` i `int`, jeśli pakiet JSON zawiera dane, które nie są konwertowane na typ docelowy, Akcja serializacji zgłosi wyjątek.

Po dodaniu tych elementów zaktualizuj metodę `Main`, aby wyświetlić te elementy:

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

Ostatnim krokiem jest dodanie informacji dla ostatniej operacji wypychania. Te informacje są sformatowane w ten sposób w odpowiedzi JSON:

```json
2016-02-08T21:27:00Z
```

Ten format nie jest zgodny z żadnym ze standardowych formatów programu .NET <xref:System.DateTime>. Z tego powodu należy napisać niestandardową metodę konwersji. Prawdopodobnie nie chcesz również, aby nieprzetworzony ciąg był widoczny dla użytkowników klasy `Repository`. Atrybuty mogą również ułatwić kontrolę. Najpierw Zdefiniuj `public` właściwość, która będzie przechowywać ciąg reprezentujący datę i godzinę w klasie `Repository` i Właściwość `LastPush` `readonly`, która zwraca sformatowany ciąg, który reprezentuje datę zwróconą:

```csharp
[JsonPropertyName("pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

Przejdźmy do nowej konstrukcji, która została właśnie zdefiniowana. Właściwość `LastPush` jest definiowana przy użyciu *składowej z wyrażeniami* dla metody dostępu `get`. Brak metody dostępu `set`. Pomijanie metody dostępu `set` jest sposobem definiowania właściwości *tylko do odczytu* w C#. (Tak, możesz tworzyć właściwości *tylko do zapisu* w C#, ale ich wartości są ograniczone). Metoda <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> analizuje ciąg i tworzy obiekt <xref:System.DateTime> przy użyciu podanego formatu daty i dodaje dodatkowe metadane do `DateTime` przy użyciu obiektu `CultureInfo`. Jeśli operacja analizy zakończy się niepowodzeniem, metoda dostępu do właściwości zgłasza wyjątek.

Aby użyć <xref:System.Globalization.CultureInfo.InvariantCulture>, należy dodać przestrzeń nazw <xref:System.Globalization> do dyrektyw `using` w `repo.cs`:

```csharp
using System.Globalization;
```

Na koniec Dodaj jedną instrukcję wyjściową w konsoli i wszystko jest gotowe do skompilowania i uruchomienia tej aplikacji ponownie:

```csharp
Console.WriteLine(repo.LastPush);
```

Twoja wersja powinna teraz być zgodna z [Zakończono przykładem](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).

## <a name="conclusion"></a>Wniosek

W tym samouczku pokazano, jak wykonywać żądania sieci Web, analizować wyniki i wyświetlać właściwości tych wyników. Dodano również nowe pakiety jako zależności w projekcie. Zaobserwowano niektóre funkcje C# języka, które obsługują techniki zorientowane obiektowo.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
