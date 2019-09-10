---
title: Tworzenie klienta REST przy użyciu platformy .NET Core
description: W tym samouczku przedstawiono szereg funkcji platformy .NET Core i C# języka.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 001a9cbaae1cdb57b6451bc42ce326864f8dcf7b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850976"
---
# <a name="rest-client"></a>Klient REST

## <a name="introduction"></a>Wprowadzenie

W tym samouczku przedstawiono szereg funkcji platformy .NET Core i C# języka. Dowiesz się:

* Podstawowe informacje o interfejsie wiersza polecenia (CLI) platformy .NET Core.
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

Pierwszym krokiem jest utworzenie nowej aplikacji. Otwórz wiersz polecenia i Utwórz nowy katalog dla aplikacji. Upewnij się, że bieżący katalog. Wpisz polecenie `dotnet new console` w wierszu polecenia. Spowoduje to utworzenie plików początkowych dla podstawowej aplikacji "Hello world". Ponieważ jest to nowy projekt, nie są stosowane żadne zależności, więc pierwsze uruchomienie spowoduje pobranie platformy .NET Core, zainstalowanie certyfikatu deweloperskiego i uruchomienie Menedżera pakietów NuGet w celu przywrócenia brakujących zależności.

Przed rozpoczęciem wprowadzania modyfikacji wpisz `dotnet run` ([Zobacz Uwaga](#dotnet-restore-note)) w wierszu polecenia, aby uruchomić aplikację. `dotnet run`wykonuje `dotnet restore` automatycznie, jeśli w środowisku nie ma zależności. Wykonuje `dotnet build` również, jeśli aplikacja musi zostać odbudowana.
Po wstępnej konfiguracji wystarczy uruchomić `dotnet restore` program lub `dotnet build` tylko wtedy, gdy jest to zrozumiałe dla projektu.

## <a name="adding-new-dependencies"></a>Dodawanie nowych zależności

Jednym z kluczowych celów projektowych dla platformy .NET Core jest Minimalizacja rozmiaru instalacji programu .NET. Jeśli aplikacja wymaga dodatkowych bibliotek dla niektórych funkcji, należy dodać te zależności do pliku C# projektu (\*. csproj). Na potrzeby tego przykładu należy dodać `System.Runtime.Serialization.Json` pakiet, aby aplikacja mogła przetwarzać odpowiedzi JSON.

Otwórz plik `csproj` projektu. Pierwszy wiersz pliku powinien wyglądać następująco:

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

Dodaj następujące elementy bezpośrednio po tym wierszu:

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup>
```

Większość edytorów kodu zapewnia uzupełnianie dla różnych wersji tych bibliotek. Zwykle zechcesz używać najnowszej wersji dowolnego dodawanego pakietu. Ważne jest jednak, aby upewnić się, że wersje wszystkich pakietów pasują do siebie i że są one zgodne z wersją struktury aplikacji .NET Core.

Po wprowadzeniu tych zmian wykonaj `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)), aby pakiet został zainstalowany w systemie.

## <a name="making-web-requests"></a>Tworzenie żądań sieci Web

Teraz wszystko jest gotowe do rozpoczęcia pobierania danych z sieci Web. W tej aplikacji należy przeczytać informacje z [interfejsu API usługi GitHub](https://developer.github.com/v3/). Zapoznajmy się z informacjami na temat projektów w ramach parasola [.NET Foundation](https://www.dotnetfoundation.org/) . Zacznij od wprowadzenia żądania do interfejsu API usługi GitHub w celu pobrania informacji o projektach. Używany punkt końcowy to: <https://api.github.com/orgs/dotnet/repos>. Chcesz pobrać wszystkie informacje o tych projektach, aby użyć żądania HTTP GET.
Przeglądarka korzysta również z żądań HTTP GET, dlatego można wkleić ten adres URL do przeglądarki, aby zobaczyć, jakie informacje będą odbierane i przetwarzane.

Użyj klasy, <xref:System.Net.Http.HttpClient> aby wykonywać żądania sieci Web. Podobnie jak w przypadku wszystkich nowoczesnych <xref:System.Net.Http.HttpClient> interfejsów API platformy .NET, obsługiwane są tylko metody asynchroniczne dla długotrwałych interfejsów API.
Zacznij od wprowadzenia metody asynchronicznej. Wdrożenie jest wypełniane podczas tworzenia funkcjonalności aplikacji. Najpierw Otwórz `program.cs` plik w katalogu projektu i Dodaj następującą metodę `Program` do klasy:

```csharp
private static async Task ProcessRepositories()
{
}
```

Należy dodać `using` instrukcję w górnej `Main` części metody, aby C# kompilator rozpoznaje <xref:System.Threading.Tasks.Task> typ:

```csharp
using System.Threading.Tasks;
```

Jeśli tworzysz projekt w tym momencie, otrzymasz ostrzeżenie wygenerowane dla tej metody, ponieważ nie zawiera ona żadnych `await` operatorów i zostanie uruchomiony synchronicznie. Zignoruj to teraz; Operatory należy dodać `await` podczas wypełniania.

Następnie zmień nazwę przestrzeni nazw zdefiniowanej w `namespace` instrukcji z `ConsoleApp` domyślnej na `WebAPIClient`. Później zdefiniujemy `repo` klasę w tej przestrzeni nazw.

Następnie zaktualizuj `Main` metodę, aby wywołać tę metodę. `ProcessRepositories` Metoda zwraca zadanie i nie należy zamykać programu przed zakończeniem tego zadania. W związku z tym należy użyć `Wait` metody do blokowania i oczekiwania na zakończenie zadania:

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

Teraz masz program, który nic nie robi, ale robi to asynchronicznie. Ulepszamy go.

Najpierw wymagany jest obiekt, który może pobrać dane z sieci Web; Możesz użyć <xref:System.Net.Http.HttpClient> , aby to zrobić. Ten obiekt obsługuje żądanie i odpowiedzi. Utwórz wystąpienie pojedynczego wystąpienia tego typu w `Program` klasie wewnątrz pliku program.cs.

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static void Main(string[] args)
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

Należy również dodać dwie nowe instrukcje using na początku pliku do skompilowania:

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

Ta pierwsza wersja wysyła żądanie sieci Web w celu odczytania listy wszystkich repozytoriów w ramach organizacji programu dotnet Foundation. (Identyfikator gitHub dla platformy .NET Foundation to "dotnet"). Pierwsze kilka wierszy zostało skonfigurowanych <xref:System.Net.Http.HttpClient> dla tego żądania. Najpierw jest skonfigurowany do akceptowania odpowiedzi JSON usługi GitHub.
Ten format jest po prostu kod JSON. Następny wiersz dodaje nagłówek agenta użytkownika do wszystkich żądań z tego obiektu. Te dwa nagłówki są sprawdzane przez kod serwera usługi GitHub i są niezbędne do pobierania informacji z usługi GitHub.

Po skonfigurowaniu programu <xref:System.Net.Http.HttpClient>należy utworzyć żądanie sieci Web i pobrać odpowiedź. W tej pierwszej wersji jest używana <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> wygodna metoda. Ta wygodna metoda uruchamia zadanie, które wykonuje żądanie sieci Web, a następnie po powrocie żądania odczytuje strumień odpowiedzi i wyodrębnia zawartość ze strumienia. Treść odpowiedzi jest zwracana jako <xref:System.String>. Ten ciąg jest dostępny po zakończeniu zadania.

Ostatnie dwie wiersze tej metody oczekują na zadanie, a następnie drukują odpowiedź do konsoli.
Skompiluj aplikację i uruchom ją. Ostrzeżenie kompilacji pozostanie teraz, ponieważ `ProcessRepositories` teraz `await` zawiera operator. Zobaczysz długi sposób wyświetlania tekstu sformatowanego w formacie JSON.

## <a name="processing-the-json-result"></a>Przetwarzanie wyniku JSON

W tym momencie napisano kod umożliwiający pobranie odpowiedzi z serwera sieci Web i wyświetlenie tekstu zawartego w tej odpowiedzi. Następnie przekonwertujmy tę odpowiedź JSON na C# obiekty.

Serializator JSON konwertuje dane JSON na C# obiekty. Pierwsze zadanie polega na zdefiniowaniu typu C# klasy, aby zawierała informacje używane z tej odpowiedzi. Kompilujmy ten ruch powoli, więc Zacznij od prostego C# typu, który zawiera nazwę repozytorium:

```csharp
using System;

namespace WebAPIClient
{
    public class repo
    {
        public string name;
    }
}
```

Umieść powyższy kod w nowym pliku o nazwie "repo. cs". Ta wersja klasy reprezentuje najprostszą ścieżkę do przetwarzania danych JSON. Nazwa klasy i nazwa elementu członkowskiego są zgodne z nazwami użytymi w pakiecie JSON, a C# nie z następującymi konwencjami. Aby naprawić ten problem, należy w późniejszym czasie dostarczyć pewne atrybuty konfiguracyjne. Ta klasa ilustruje kolejną ważną funkcję serializacji i deserializacji kodu JSON: Nie wszystkie pola w pakiecie JSON są częścią tej klasy.
Serializator JSON zignoruje informacje, które nie są uwzględnione w używanym typie klasy.
Ta funkcja ułatwia tworzenie typów, które współpracują z tylko podzbiorem pól w pakiecie JSON.

Teraz, po utworzeniu typu, przyjrzyjmy go. Należy utworzyć <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> obiekt. Ten obiekt musi znać typ CLR oczekiwany przez pobrany pakiet JSON. Pakiet z usługi GitHub zawiera sekwencję repozytoriów, więc `List<repo>` jest to poprawny typ. Dodaj następujący wiersz do `ProcessRepositories` metody:

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

Używane są dwa nowe przestrzenie nazw, dlatego należy dodać je również:

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

Następnie użyjesz serializatora, aby przekonwertować kod JSON na C# obiekty. Zastąp wywołanie <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> `ProcessRepositories` w metodzie następującymi dwoma wierszami:

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

Zwróć uwagę, że jesteś teraz <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> używany <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>zamiast. Serializator używa strumienia zamiast ciągu jako źródła. Wyjaśnimy kilka funkcji C# języka, które są używane w drugim wierszu powyżej. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> Argument`await` jest wyrażeniem. Wyrażenia await mogą pojawiać się niemal wszędzie w kodzie, nawet w przypadku, gdy tylko do tej pory są widoczne jako część instrukcji przypisania.

Następnie operator konwertuje `object` typ czasu kompilacji na `List<repo>`. `as`
Deklaracja <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> deklaruje, że zwraca obiekt typu <xref:System.Object?displayProperty=nameWithType>. <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)>zwróci typ określony podczas konstruowania (`List<repo>` w tym samouczku). Jeśli konwersja nie powiedzie się, `as` operator zwróci wartość `null`, zamiast zgłaszać wyjątek.

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

Zanim dodasz więcej funkcji, przyjrzyjmy się `repo` typowi C# . W tym celu należy dodać adnotację do `repo` typu z *atrybutami* , które kontrolują sposób działania serializatora JSON. W Twoim przypadku te atrybuty zostaną użyte do zdefiniowania mapowania między nazwami kluczy JSON i nazwami C# klas i elementów członkowskich. Używane są <xref:System.Runtime.Serialization.DataContractAttribute> atrybuty i <xref:System.Runtime.Serialization.DataMemberAttribute> . Według Konwencji wszystkie klasy atrybutów kończą się sufiksem `Attribute`. Nie trzeba jednak używać tego sufiksu podczas stosowania atrybutu.

Atrybuty <xref:System.Runtime.Serialization.DataContractAttribute> i <xref:System.Runtime.Serialization.DataMemberAttribute> znajdują się w innej bibliotece, dlatego należy dodać tę bibliotekę do pliku C# projektu jako zależność. Dodaj następujący wiersz do `<ItemGroup>` sekcji pliku projektu:

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

Po zapisaniu pliku Uruchom `dotnet restore` polecenie ([patrz Uwaga](#dotnet-restore-note)), aby pobrać ten pakiet.

Następnie otwórz `repo.cs` plik. Zmieńmy nazwę tak, aby korzystała z przypadku języka Pascal, i w pełni `Repository`Wyewidencjonuj nazwę. Nadal chcemy zmapować węzły "repozytorium" JSON na ten typ, dlatego należy dodać <xref:System.Runtime.Serialization.DataContractAttribute> atrybut do deklaracji klasy. Ustawisz `Name` właściwość atrybutu na nazwę węzłów JSON, które są mapowane na ten typ:

```csharp
[DataContract(Name="repo")]
public class Repository
```

Jest członkiem <xref:System.Runtime.Serialization> przestrzeni nazw, dlatego należy dodać odpowiednią `using` instrukcję na początku pliku: <xref:System.Runtime.Serialization.DataContractAttribute>

```csharp
using System.Runtime.Serialization;
```

Zmieniono nazwę `repo` klasy na `Repository`, więc musisz wprowadzić taką samą zmianę nazwy w program.cs (niektóre edytory mogą obsługiwać refaktoryzację zmiany nazwy, która spowoduje automatyczne wprowadzenie tej zmiany:)

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

Następnie wprowadź tę samą zmianę w `name` polu przy <xref:System.Runtime.Serialization.DataMemberAttribute> użyciu klasy. Wprowadź następujące zmiany w deklaracji `name` pola w repo.cs:

```csharp
[DataMember(Name="name")]
public string Name;
```

Ta zmiana oznacza, że należy zmienić kod, który zapisuje nazwę każdego repozytorium w program.cs:

```csharp
Console.WriteLine(repo.Name);
```

Aby upewnić się, że mapowania są poprawne, należy wykonać jedną z nich.`dotnet build` `dotnet run` Powinny zostać wyświetlone te same dane wyjściowe co poprzednio. Przed przetworzeniem większej liczby właściwości na serwerze sieci Web należy wprowadzić nową zmianę `Repository` klasy. `Name` Składowa jest polem dostępnym publicznie. To nie jest dobre rozwiązanie zorientowane obiektowo, więc zmień je na właściwość. Z tego względu nie potrzebujemy żadnego konkretnego kodu do uruchomienia podczas pobierania lub ustawiania właściwości, ale zmiana na Właściwość ułatwia dodawanie tych zmian w późniejszym czasie bez przerywania żadnego kodu, który używa `Repository` klasy.

Usuń definicję pola i Zastąp ją [zaimplementowaną właściwością](../programming-guide/classes-and-structs/auto-implemented-properties.md):

```csharp
public string Name { get; set; }
```

Kompilator generuje treść `get` metod dostępu i `set` , a także pole prywatne do przechowywania nazwy. Będzie wyglądać podobnie do następującego kodu, który można wpisać ręcznie:

```csharp
public string Name
{
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

Utwórzmy jeszcze jedną zmianę przed dodaniem nowych funkcji. `ProcessRepositories` Metoda może wykonywać działania asynchroniczne i zwracać kolekcję repozytoriów. Wróćmy do `List<Repository>` tej metody i przeniesiesz kod, który zapisuje informacje `Main` w metodzie.

Zmień sygnaturę `ProcessRepositories` , aby zwracała zadanie, którego wynikiem jest `Repository` lista obiektów:

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

Następnie po przetworzeniu odpowiedzi JSON należy zwrócić repozytoria:

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

Kompilator generuje `Task<T>` obiekt do zwrócenia, ponieważ oznaczono tę metodę jako `async`.
Następnie zmodyfikujemy `Main` metodę, aby przechwycić te wyniki i zapisywali nazwy poszczególnych repozytoriów w konsoli programu. Teraz `Main` Metoda wygląda następująco:

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

Uzyskiwanie dostępu do właściwości bloków zadań do momentu ukończenia zadania. `Result` Zwykle wolisz wykonać `await` zadanie, jak `ProcessRepositories` w metodzie, ale nie jest `Main` to dozwolone w metodzie.

## <a name="reading-more-information"></a>Odczytywanie dodatkowych informacji

Zakończmy to przez przetwarzanie kilku większej liczby właściwości w pakiecie JSON, które są wysyłane z interfejsu API usługi GitHub. Nie chcesz dowiedzieć się wszystkiego, ale dodanie kilku właściwości spowoduje pokazanie kilku funkcji C# języka.

Zacznijmy od dodania kilku prostych typów do `Repository` definicji klasy. Dodaj te właściwości do tej klasy:

```csharp
[DataMember(Name="description")]
public string Description { get; set; }

[DataMember(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[DataMember(Name="homepage")]
public Uri Homepage { get; set; }

[DataMember(Name="watchers")]
public int Watchers { get; set; }
```

Te właściwości mają wbudowane konwersje z typu ciąg (który zawiera pakiety JSON) do typu docelowego. <xref:System.Uri> Typ może być nowy dla Ciebie. Reprezentuje identyfikator URI lub w tym przypadku adres URL. W przypadku `Uri` typów i `int` , jeśli pakiet JSON zawiera dane, które nie są konwertowane na typ docelowy, Akcja serializacji zgłosi wyjątek.

Po dodaniu tych elementów zaktualizuj `Main` metodę, aby wyświetlić te elementy:

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

Ten format nie jest zgodny z żadnym ze standardowych formatów <xref:System.DateTime> .NET. Z tego powodu należy napisać niestandardową metodę konwersji. Prawdopodobnie nie chcesz również, aby nieprzetworzony ciąg był uwidoczniony dla `Repository` użytkowników klasy. Atrybuty mogą również ułatwić kontrolę. Najpierw Zdefiniuj `private` właściwość, która będzie przechowywać ciąg reprezentujący datę i godzinę `Repository` w klasie:

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<xref:System.Runtime.Serialization.DataMemberAttribute> Atrybut informuje Serializator, który powinien być przetwarzany, nawet jeśli nie jest to publiczny element członkowski. Następnie musisz napisać publiczną właściwość tylko do odczytu, która konwertuje ciąg na prawidłowy <xref:System.DateTime> obiekt, i <xref:System.DateTime>zwraca:

```csharp
[IgnoreDataMember]
public DateTime LastPush
{
    get
    {
        return DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
    }
}
```

Przejdźmy do nowych konstrukcji powyżej. Ten `IgnoreDataMember` atrybut nakazuje serializatorowi, że ten typ nie powinien być odczytany ani zapisany z dowolnego obiektu JSON. Ta właściwość zawiera tylko `get` metodę dostępu. `set` Brak metody dostępu. To właśnie definiuje właściwość tylko do *odczytu* w C#. (Tak, możesz tworzyć właściwości *tylko do zapisu* w C#, ale ich wartości są ograniczone). Metoda analizuje ciąg i <xref:System.DateTime> tworzy obiekt przy użyciu podanego formatu daty i `DateTime` dodaje dodatkowe `CultureInfo` metadane do obiektu za pomocą. <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Jeśli operacja analizy zakończy się niepowodzeniem, metoda dostępu do właściwości zgłasza wyjątek.

Aby użyć <xref:System.Globalization.CultureInfo.InvariantCulture>, należy <xref:System.Globalization> dodać przestrzeń nazw do `using` instrukcji w `repo.cs`:

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
