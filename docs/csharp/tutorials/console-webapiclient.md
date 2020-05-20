---
title: Tworzenie klienta REST przy użyciu platformy .NET Core
description: W tym samouczku przedstawiono szereg funkcji platformy .NET Core i języka C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 4a3a76d1ec9893c2c3e0353e305a19e59c586fe5
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420386"
---
# <a name="rest-client"></a>Klient REST

W tym samouczku przedstawiono szereg funkcji platformy .NET Core i języka C#. Dowiesz się:

* Podstawowe informacje dotyczące interfejs wiersza polecenia platformy .NET Core.
* Omówienie funkcji języka C#.
* Zarządzanie zależnościami przy użyciu narzędzia NuGet
* Komunikacja HTTP
* Przetwarzanie informacji JSON
* Zarządzanie konfiguracją przy użyciu atrybutów.

Utworzysz aplikację, która wystawia żądania HTTP do usługi REST w serwisie GitHub. Informacje są odczytywane w formacie JSON i konwertowane na obiekty w języku C#. Na koniec zobaczysz, jak korzystać z obiektów C#.

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

Przed rozpoczęciem wprowadzania modyfikacji wpisz `dotnet run` ([Zobacz Uwaga](#dotnet-restore-note)) w wierszu polecenia, aby uruchomić aplikację. `dotnet run`wykonuje automatycznie, `dotnet restore` Jeśli w środowisku nie ma zależności. Wykonuje również, `dotnet build` Jeśli aplikacja musi zostać odbudowana.
Po wstępnej konfiguracji wystarczy uruchomić program `dotnet restore` lub tylko `dotnet build` wtedy, gdy jest to zrozumiałe dla projektu.

## <a name="adding-new-dependencies"></a>Dodawanie nowych zależności

Jednym z kluczowych celów projektowych dla platformy .NET Core jest Minimalizacja rozmiaru instalacji programu .NET. Jeśli aplikacja wymaga dodatkowych bibliotek dla niektórych funkcji, należy dodać te zależności do pliku projektu C# ( \* . csproj). Na potrzeby tego przykładu należy dodać `System.Runtime.Serialization.Json` pakiet, aby aplikacja mogła przetwarzać odpowiedzi JSON.

Wymagany jest `System.Runtime.Serialization.Json` pakiet dla tej aplikacji. Dodaj go do projektu, uruchamiając następujące polecenie [interfejsu wiersza polecenia platformy .NET](../../core/tools/dotnet-add-package.md) :

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a>Tworzenie żądań sieci Web

Teraz wszystko jest gotowe do rozpoczęcia pobierania danych z sieci Web. W tej aplikacji należy przeczytać informacje z [interfejsu API usługi GitHub](https://developer.github.com/v3/). Zapoznajmy się z informacjami na temat projektów w ramach parasola [.NET Foundation](https://www.dotnetfoundation.org/) . Zacznij od wprowadzenia żądania do interfejsu API usługi GitHub w celu pobrania informacji o projektach. Używany punkt końcowy to: <https://api.github.com/orgs/dotnet/repos> . Chcesz pobrać wszystkie informacje o tych projektach, aby użyć żądania HTTP GET.
Przeglądarka korzysta również z żądań HTTP GET, dlatego można wkleić ten adres URL do przeglądarki, aby zobaczyć, jakie informacje będą odbierane i przetwarzane.

Użyj klasy, <xref:System.Net.Http.HttpClient> Aby wykonywać żądania sieci Web. Podobnie jak w przypadku wszystkich nowoczesnych interfejsów API platformy .NET, <xref:System.Net.Http.HttpClient> obsługiwane są tylko metody asynchroniczne dla długotrwałych interfejsów API.
Zacznij od wprowadzenia metody asynchronicznej. Wdrożenie jest wypełniane podczas tworzenia funkcjonalności aplikacji. Najpierw Otwórz `program.cs` plik w katalogu projektu i Dodaj następującą metodę do `Program` klasy:

```csharp
private static async Task ProcessRepositories()
{
}
```

Należy dodać `using` dyrektywę u góry `Main` metody, aby kompilator języka C# rozpoznał <xref:System.Threading.Tasks.Task> Typ:

```csharp
using System.Threading.Tasks;
```

Jeśli tworzysz projekt w tym momencie, otrzymasz ostrzeżenie wygenerowane dla tej metody, ponieważ nie zawiera ona żadnych `await` operatorów i zostanie uruchomiony synchronicznie. Zignoruj to teraz; Operatory należy dodać podczas `await` wypełniania.

Następnie zaktualizuj metodę, `Main` Aby wywołać `ProcessRepositories` metodę. `ProcessRepositories`Metoda zwraca zadanie i nie należy zamykać programu przed zakończeniem tego zadania. W związku z tym należy zmienić sygnaturę `Main` . Dodaj `async` modyfikator i Zmień zwracany typ na `Task` . Następnie w treści metody Dodaj wywołanie do `ProcessRepositories` . Dodaj `await` słowo kluczowe do tego wywołania metody:

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

Teraz masz program, który nic nie robi, ale robi to asynchronicznie. Ulepszamy go.

Najpierw wymagany jest obiekt, który może pobrać dane z sieci Web; Możesz użyć, <xref:System.Net.Http.HttpClient> Aby to zrobić. Ten obiekt obsługuje żądanie i odpowiedzi. Utwórz wystąpienie pojedynczego wystąpienia tego typu w `Program` klasie wewnątrz pliku *program.cs* .

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

Wróćmy do `ProcessRepositories` metody i wypełnimy ją pierwszą wersją:

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

Należy również dodać dwie nowe `using` dyrektywy w górnej części pliku do skompilowania:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Ta pierwsza wersja wysyła żądanie sieci Web w celu odczytania listy wszystkich repozytoriów w ramach organizacji programu dotnet Foundation. (Identyfikator gitHub dla platformy .NET Foundation to "dotnet"). Pierwsze kilka wierszy zostało skonfigurowanych <xref:System.Net.Http.HttpClient> dla tego żądania. Najpierw jest skonfigurowany do akceptowania odpowiedzi JSON usługi GitHub.
Ten format jest po prostu kod JSON. Następny wiersz dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu. Te dwa nagłówki są sprawdzane przez kod serwera usługi GitHub i są niezbędne do pobierania informacji z usługi GitHub.

Po skonfigurowaniu programu należy <xref:System.Net.Http.HttpClient> utworzyć żądanie sieci Web i pobrać odpowiedź. W tej pierwszej wersji jest używana <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> wygodna metoda. Ta wygodna metoda uruchamia zadanie, które wykonuje żądanie sieci Web, a następnie po powrocie żądania odczytuje strumień odpowiedzi i wyodrębnia zawartość ze strumienia. Treść odpowiedzi jest zwracana jako <xref:System.String> . Ten ciąg jest dostępny po zakończeniu zadania.

Ostatnie dwie wiersze tej metody oczekują na zadanie, a następnie drukują odpowiedź do konsoli.
Skompiluj aplikację i uruchom ją. Ostrzeżenie kompilacji pozostanie teraz, ponieważ `ProcessRepositories` teraz zawiera `await` operator. Zobaczysz długi sposób wyświetlania tekstu sformatowanego w formacie JSON.

## <a name="processing-the-json-result"></a>Przetwarzanie wyniku JSON

W tym momencie napisano kod umożliwiający pobranie odpowiedzi z serwera sieci Web i wyświetlenie tekstu zawartego w tej odpowiedzi. Następnie przekonwertujmy tę odpowiedź JSON na obiekty języka C#.

<xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType>Klasa serializować obiekty do formatu JSON i deserializacji kod JSON w obiektach. Zacznij od zdefiniowania klasy, która będzie reprezentować `repo` obiekt JSON zwrócony z interfejsu API usługi GitHub:

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

Umieść powyższy kod w nowym pliku o nazwie "repo. cs". Ta wersja klasy reprezentuje najprostszą ścieżkę do przetwarzania danych JSON. Nazwa klasy i nazwa elementu członkowskiego są zgodne z nazwami użytymi w pakiecie JSON, a nie następującymi konwencjami języka C#. Aby naprawić ten problem, należy w późniejszym czasie dostarczyć pewne atrybuty konfiguracyjne. Ta klasa pokazuje kolejną ważną funkcję serializacji i deserializacji kodu JSON: nie wszystkie pola w pakiecie JSON są częścią tej klasy.
Serializator JSON zignoruje informacje, które nie są uwzględnione w używanym typie klasy.
Ta funkcja ułatwia tworzenie typów, które współpracują z tylko podzbiorem pól w pakiecie JSON.

Teraz, po utworzeniu typu, przyjrzyjmy go.

Następnie użyjemy serializatora do przekonwertowania JSON na obiekty języka C#. Zastąp wywołanie <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> `ProcessRepositories` metody w metodzie następującymi wierszami:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

Używane są nowe przestrzenie nazw, więc należy je dodać również na początku pliku:

```csharp
using System.Collections.Generic;
using System.Text.Json;
```

Zwróć uwagę, że jesteś teraz używany <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> zamiast <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> . Serializator używa strumienia zamiast ciągu jako źródła. Wyjaśnimy kilka funkcji języka C#, które są używane w drugim wierszu poprzedniego fragmentu kodu. Pierwszy argument <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> jest `await` wyrażeniem. (Pozostałe dwa parametry są opcjonalne i pomijane we fragmencie kodu). Wyrażenia await mogą pojawiać się niemal wszędzie w kodzie, nawet w przypadku, gdy tylko do tej pory są widoczne jako część instrukcji przypisania. `Deserialize`Metoda jest *rodzajowa*, co oznacza, że należy podać argumenty typu dla rodzaju obiektów, które mają być tworzone na podstawie tekstu JSON. W tym przykładzie jest deserializowany do `List<Repository>` , który jest innym obiektem ogólnym, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> . `List<>`Klasa przechowuje kolekcję obiektów. Argument typu deklaruje typ obiektów przechowywanych w obiekcie `List<>` . Tekst JSON reprezentuje kolekcję obiektów repozytorium, więc argument type ma wartość `Repository` .

Prawie gotowe do tej sekcji. Teraz, gdy dane JSON zostały przekonwertowane na obiekty języka C#, użyjmy nazwy każdego repozytorium. Zastąp odczytane wiersze:

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

Zanim dodasz więcej funkcji, przyjrzyjmy się `name` właściwości przy użyciu `[JsonPropertyName]` atrybutu. Wprowadź następujące zmiany w deklaracji `name` pola w repo.cs:

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

Aby użyć `[JsonPropertyName]` atrybutu, należy dodać <xref:System.Text.Json.Serialization> przestrzeń nazw do `using` dyrektyw:

```csharp
using System.Text.Json.Serialization;
```

Ta zmiana oznacza, że należy zmienić kod, który zapisuje nazwę każdego repozytorium w program.cs:

```csharp
Console.WriteLine(repo.Name);
```

Wykonaj `dotnet run` , aby upewnić się, że mapowania są poprawne. Powinny zostać wyświetlone te same dane wyjściowe co poprzednio.

Utwórzmy jeszcze jedną zmianę przed dodaniem nowych funkcji. `ProcessRepositories`Metoda może wykonywać działania asynchroniczne i zwracać kolekcję repozytoriów. Wróćmy do tej `List<Repository>` metody i przeniesiesz kod, który zapisuje informacje w `Main` metodzie.

Zmień sygnaturę, `ProcessRepositories` aby zwracała zadanie, którego wynikiem jest lista `Repository` obiektów:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Następnie po przetworzeniu odpowiedzi JSON należy zwrócić repozytoria:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

Kompilator generuje `Task<T>` obiekt do zwrócenia, ponieważ oznaczono tę metodę jako `async` .
Następnie zmodyfikujemy `Main` metodę, aby przechwycić te wyniki i zapisywali nazwy poszczególnych repozytoriów w konsoli programu. `Main`Teraz Metoda wygląda następująco:

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a>Odczytywanie dodatkowych informacji

Zakończmy to przez przetwarzanie kilku większej liczby właściwości w pakiecie JSON, które są wysyłane z interfejsu API usługi GitHub. Nie chcesz dowiedzieć się, ale dodanie kilku właściwości spowoduje pokazanie kilku funkcji języka C#.

Zacznijmy od dodania kilku prostych typów do `Repository` definicji klasy. Dodaj te właściwości do tej klasy:

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

Te właściwości mają wbudowane konwersje z typu ciąg (który zawiera pakiety JSON) do typu docelowego. <xref:System.Uri>Typ może być nowy dla Ciebie. Reprezentuje identyfikator URI lub w tym przypadku adres URL. W przypadku `Uri` `int` typów i, jeśli pakiet JSON zawiera dane, które nie są konwertowane na typ docelowy, Akcja serializacji zgłosi wyjątek.

Po dodaniu tych elementów zaktualizuj metodę, `Main` Aby wyświetlić te elementy:

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

Ten format jest w uniwersalnym czasie koordynowanym (UTC), aby uzyskać <xref:System.DateTime> wartość, której <xref:System.DateTime.Kind%2A> Właściwość jest <xref:System.DateTimeKind.Utc> . Jeśli wolisz daty reprezentowanej w strefie czasowej, musisz napisać niestandardową metodę konwersji. Najpierw Zdefiniuj `public` Właściwość, która będzie zawierać reprezentację UTC daty i godziny w `Repository` klasie oraz `LastPush` `readonly` Właściwość zwracającą datę przekonwertowaną na czas lokalny:

```csharp
[JsonPropertyName("pushed_at")]
public DateTime LastPushUtc { get; set; }

public DateTime LastPush => LastPushUtc.ToLocalTime();
```

Przejdźmy do nowej konstrukcji, która została właśnie zdefiniowana. `LastPush`Właściwość jest definiowana przy użyciu *składowej z wyrażeniami* dla `get` metody dostępu. Brak `set` metody dostępu. Pominięcie `set` metody dostępu oznacza sposób definiowania właściwości tylko do *odczytu* w języku C#. (Tak, możesz tworzyć właściwości *tylko do zapisu* w języku C#, ale ich wartości są ograniczone).

Na koniec Dodaj jedną instrukcję wyjściową w konsoli i wszystko jest gotowe do skompilowania i uruchomienia tej aplikacji ponownie:

```csharp
Console.WriteLine(repo.LastPush);
```

Twoja wersja powinna teraz być zgodna z [Zakończono przykładem](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).

## <a name="conclusion"></a>Podsumowanie

W tym samouczku pokazano, jak wykonywać żądania sieci Web, analizować wyniki i wyświetlać właściwości tych wyników. Dodano również nowe pakiety jako zależności w projekcie. Zaobserwowano niektóre funkcje języka C#, które obsługują techniki zorientowane obiektowo.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
